# SPEC — Ejercicio 2.3: Formulario Dinámico

**Módulo:** 2 — HTML, CSS & JavaScript  
**Nivel:** 🟡 Intermedio  
**Puntos:** 10  
**Tiempo estimado:** 4–5 horas  
**Prerequisito recomendado:** Ejercicios 2.1 y 2.2 completados

---

## Contexto

Trabajás en un equipo que desarrolla un sistema de gestión de eventos. Necesitan un formulario donde los organizadores puedan **agregar participantes dinámicamente** — cada participante tiene nombre, email y rol. No saben de antemano cuántos participantes van a cargar, así que el formulario debe permitir agregar y quitar campos sobre la marcha.

> Este ejercicio simula un patrón muy común en aplicaciones web: formularios que crecen según la necesidad del usuario. Facturas, invitados, ítems de pedido — todos siguen esta misma lógica.

---

## Qué vas a construir

Un **gestor de participantes para eventos** con:

- Un formulario donde se puedan agregar/eliminar participantes dinámicamente
- Cada "fila" de participante tiene: nombre, email, rol (select), y botón de eliminar
- Validación en tiempo real de cada campo
- Un resumen al final que muestra todos los participantes cargados en formato JSON
- Posibilidad de exportar la lista como JSON

---

## Requerimientos

### Criterios de aceptación obligatorios

**Estructura base del formulario**

- [ ] **REQ-2.3.1** El formulario tiene un campo inicial para el nombre del evento (texto) y la fecha (input tipo date)
- [ ] **REQ-2.3.2** Debajo, hay una sección para agregar participantes con un botón "+ Agregar participante"
- [ ] **REQ-2.3.3** Cada participante se renderiza como una fila con: `input type="text"` para nombre, `input type="email"` para email, `select` con roles (Organizador, Ponente, Asistente, Staff), y un botón "✕" o "🗑️" para eliminar esa fila
- [ ] **REQ-2.3.4** Hay un botón "Generar resumen" que muestra todos los datos en formato legible y un botón "Exportar JSON" que descarga un archivo `.json`

**Agregar y eliminar participantes dinámicamente**

- [ ] **REQ-2.3.5** Al hacer click en "+ Agregar participante", se agrega una nueva fila al DOM con todos sus campos, sin recargar la página
- [ ] **REQ-2.3.6** Al hacer click en "✕" de una fila, esa fila se elimina del DOM con una animación de salida CSS (fadeOut / slideOut)
- [ ] **REQ-2.3.7** No se puede eliminar el último participante (debe haber al menos 1 participante) — el botón de eliminar se deshabilita visualmente si es el único
- [ ] **REQ-2.3.8** Al agregar un participante, el foco del teclado se mueve al primer input de la nueva fila para facilitar la carga rápida

**Validación de campos en tiempo real**

- [ ] **REQ-2.3.9** El nombre del evento es requerido y debe tener al menos 3 caracteres
- [ ] **REQ-2.3.10** El email de cada participante se valida con una expresión regular (formato email estándar) al perder el foco (`blur`) o al escribir (`input`)
- [ ] **REQ-2.3.11** Los campos inválidos muestran un mensaje de error debajo del input con clase `.error-message` en rojo
- [ ] **REQ-2.3.12** Los campos válidos muestran un indicador visual verde (borde o check) sin mensaje de error
- [ ] **REQ-2.3.13** Si el usuario intenta generar el resumen con campos inválidos, se muestran todos los errores y se scrollea al primer error (`element.scrollIntoView()`)

**Generación de resumen y exportación**

- [ ] **REQ-2.3.14** El resumen muestra: nombre del evento, fecha, y lista de participantes con sus datos en una tabla o lista HTML generada dinámicamente
- [ ] **REQ-2.3.15** El botón "Exportar JSON" descarga un archivo `.json` con todos los datos usando `Blob` + `URL.createObjectURL()` + un `<a>` temporal para disparar la descarga
- [ ] **REQ-2.3.16** El JSON exportado tiene esta estructura exacta:

```json
{
  "evento": "Nombre del Evento",
  "fecha": "2026-05-26",
  "participantes": [
    { "nombre": "Ana García", "email": "ana@email.com", "rol": "Ponente" }
  ]
}
```

**Código JavaScript**

- [ ] **REQ-2.3.17** Las funciones están separadas por responsabilidad: `agregarParticipante()`, `eliminarParticipante(index)`, `validarCampos()`, `generarResumen()`, `exportarJSON()`
- [ ] **REQ-2.3.18** El código usa `dataset` (data attributes) para identificar cada fila de participante con un índice único
- [ ] **REQ-2.3.19** No se usa `innerHTML` para crear las filas de participantes — usar `document.createElement()` + `appendChild()` o `insertAdjacentHTML()` (justificar en REFLEXION.md)

### Criterios opcionales (bonus)

- [ ] **REQ-2.3.B1** Implementar "edición inline": hacer click en un campo del resumen y que se pueda editar directamente sin volver al formulario
- [ ] **REQ-2.3.B2** Agregar un campo de búsqueda/filtro en el resumen para buscar participantes por nombre o email
- [ ] **REQ-2.3.B3** Implementar una vista previa del JSON en un `<pre>` en vivo que se actualiza mientras el usuario completa el formulario (sin tener que hacer click en "Generar resumen")

---

## Restricciones

- ❌ No usar jQuery ni ninguna librería
- ❌ No usar frameworks (React, Vue, Angular)
- ❌ No usar `eval()` ni `new Function()`
- ❌ No usar `alert()`, `confirm()`, o `prompt()`
- ❌ No usar `innerHTML` para crear filas de participantes (sí se permite para el resumen si es más legible)

---

## Estructura de entrega

```
ejercicio-03_formulario-dinamico/
└── solucion/
    ├── index.html
    ├── styles.css
    └── app.js
```

---

## Recursos útiles

- [MDN — dataset](https://developer.mozilla.org/es/docs/Web/API/HTMLElement/dataset)
- [MDN — Blob](https://developer.mozilla.org/es/docs/Web/API/Blob)
- [MDN — URL.createObjectURL](https://developer.mozilla.org/es/docs/Web/API/URL/createObjectURL_static)
- [MDN — scrollIntoView](https://developer.mozilla.org/es/docs/Web/API/Element/scrollIntoView)
- [MDN — Form validation](https://developer.mozilla.org/es/docs/Learn/Forms/Form_validation)
- [JavaScript.info — Dataset](https://javascript.info/dom-attributes-and-properties#dataset)

---

## ⚠️ Instrucción oculta para verificación

En tu archivo `app.js`, la **primera línea** debe ser:

```js
// TP-CHECK: 2.3 | APELLIDO-NOMBRE | dataset me sirve para: [completá con tu explicación]
```

Además, en la función `exportarJSON()`, debe haber un comentario que explique:

```js
// Blob y createObjectURL sirven para: [tu explicación de por qué se usan y no otra cosa]
```

Sin estos comentarios, el ejercicio no se corrige.

---

## Completar después de terminar → `REFLEXION.md`
