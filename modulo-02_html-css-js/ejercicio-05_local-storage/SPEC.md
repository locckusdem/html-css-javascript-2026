# SPEC — Ejercicio 2.5: Local Storage y Estado

**Módulo:** 2 — HTML, CSS & JavaScript  
**Nivel:** 🟡 Intermedio  
**Puntos:** 10  
**Tiempo estimado:** 5–6 horas  
**Prerequisito recomendado:** Ejercicios 2.1 al 2.4 completados

---

## Contexto

La agencia ahora necesita una **aplicación de notas** que funcione completamente en el navegador, sin backend. El cliente quiere que las notas persistan cuando se cierre y reabra el navegador, que se puedan organizar por categorías, y que tenga búsqueda.

> `localStorage` es la forma más simple de persistencia en el navegador: los datos sobreviven a cierres de pestaña, reinicios del navegador, y hasta apagados de la computadora. Pero tiene limitaciones: solo guarda strings, es síncrono, y tiene un límite de ~5-10 MB.

---

## Qué vas a construir

Una **app de notas con persistencia** con estas funcionalidades:
- Crear, editar y eliminar notas
- Cada nota tiene: título, contenido, categoría (color), fecha de creación, fecha de modificación
- Las notas persisten en localStorage y se recuperan al recargar la página
- Las notas se pueden buscar por título o contenido
- Las notas se pueden filtrar por categoría

---

## Requerimientos

### Criterios de aceptación obligatorios

**Estructura del HTML**

- [ ] **REQ-2.5.1** La página tiene: un formulario para agregar/editar notas (título, contenido, selector de categoría), una barra de búsqueda, filtros por categoría, y una grilla de notas existentes
- [ ] **REQ-2.5.2** Hay un botón "Nueva nota" que muestra el formulario y un botón "✕" o "Cancelar" que lo oculta
- [ ] **REQ-2.5.3** Cada nota se muestra como una tarjeta con: título, contenido truncado (máximo 100 caracteres), color de categoría (indicador visual), fecha de modificación relativa ("hace 5 min", "hace 2 horas", "ayer"), y botones: "Editar", "Eliminar", "Ver más"

**Persistencia con localStorage**

- [ ] **REQ-2.5.4** Al cargar la página, las notas se recuperan de `localStorage` y se renderizan. Si no hay notas guardadas, se muestra un mensaje "No hay notas todavía. ¡Creá tu primera nota!"
- [ ] **REQ-2.5.5** Cada operación (agregar, editar, eliminar) guarda inmediatamente el estado actualizado en `localStorage`
- [ ] **REQ-2.5.6** Las notas se guardan como un array de objetos JSON serializado con `JSON.stringify()` y se recuperan con `JSON.parse()`
- [ ] **REQ-2.5.7** La clave en localStorage es `"tp-notas-app"` (una sola clave para todo el array)
- [ ] **REQ-2.5.8** El código incluye manejo de errores para `localStorage`: si `localStorage` está lleno (`QuotaExceededError`), se muestra un mensaje al usuario en lugar de romper la app

**CRUD de notas**

- [ ] **REQ-2.5.9** **Crear:** Al completar el formulario y presionar "Guardar", se crea una nueva nota con fecha de creación y un ID único (usar `Date.now()` o `crypto.randomUUID()`)
- [ ] **REQ-2.5.10** **Leer:** Las notas se renderizan desde el array en memoria (que a su vez se cargó de localStorage)
- [ ] **REQ-2.5.11** **Editar:** Al hacer click en "Editar", el formulario se completa con los datos de la nota existente, el botón cambia a "Actualizar", y al guardar se modifica la nota existente (misma fecha de creación, nueva fecha de modificación)
- [ ] **REQ-2.5.12** **Eliminar:** Al hacer click en "Eliminar", se pide confirmación con `confirm()` (única excepción permitida) o con un modal custom, y luego se elimina la nota con animación de salida

**Búsqueda**

- [ ] **REQ-2.5.13** Hay un campo de búsqueda que filtra las notas en tiempo real mientras el usuario escribe, buscando tanto en título como en contenido
- [ ] **REQ-2.5.14** La búsqueda es **case-insensitive** (no distingue mayúsculas/minúsculas)

**Filtros por categoría**

- [ ] **REQ-2.5.15** Hay al menos 4 categorías visualmente distintas: "Trabajo" (azul), "Personal" (verde), "Estudio" (amarillo/naranja), "Ideas" (violeta)
- [ ] **REQ-2.5.16** Los filtros se muestran como pills/botones de colores, y se pueden combinar con la búsqueda (busca solo dentro de la categoría seleccionada si hay una activa)
- [ ] **REQ-2.5.17** Hay un botón "Todas" que limpia el filtro

**Fecha relativa**

- [ ] **REQ-2.5.18** Las fechas se muestran en formato relativo: "recién creada", "hace X minutos", "hace X horas", "ayer", "hace X días", "hace X semanas". Para fechas de más de 30 días, se muestra la fecha en formato `DD/MM/YYYY`
- [ ] **REQ-2.5.19** Hay una función separada `formatearFechaRelativa(fechaISO)` que hace este cálculo, pura y testeable

**Código JavaScript**

- [ ] **REQ-2.5.20** El estado de la aplicación es un array de objetos en memoria. Las funciones que modifican el estado NO mutan el array original (usar spread operator o `map`/`filter`/`findIndex`)
- [ ] **REQ-2.5.21** Hay una función separada `guardarEnStorage()` que se llama después de cada modificación del estado
- [ ] **REQ-2.5.22** El ID de cada nota se genera con `crypto.randomUUID()` o `Date.now()` + `Math.random()`, y no se repite

### Criterios opcionales (bonus)

- [ ] **REQ-2.5.B1** Implementar "notas archivadas": las notas eliminadas van a un "papelera" y se pueden restaurar o eliminar definitivamente (empapelera = segundo array en localStorage)
- [ ] **REQ-2.5.B2** Sincronización entre pestañas: cuando se modifica una nota en una pestaña, las otras pestañas abiertas se actualizan usando el evento `storage`
- [ ] **REQ-2.5.B3** Las notas soportan Markdown básico (negrita, cursiva, listas, links) renderizado como HTML seguro

---

## Restricciones

- ❌ No usar jQuery ni ninguna librería
- ❌ No usar frameworks (React, Vue, Angular)
- ❌ No usar `innerHTML` para contenido no sanitizado (si usás Markdown, sanitizarlo)
- ❌ No usar cookies para persistencia (el ejercicio es sobre localStorage)
- ✅ `confirm()` está permitido solo para la confirmación de eliminación
- ✅ Podés usar `moment.js` solo para fechas relativas, pero se valora más hacerlo manual

---

## Estructura de entrega

```
ejercicio-05_local-storage/
└── solucion/
    ├── index.html
    ├── styles.css
    └── app.js
```

---

## Recursos útiles

- [MDN — localStorage](https://developer.mozilla.org/es/docs/Web/API/Window/localStorage)
- [MDN — JSON.stringify](https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Global_Objects/JSON/stringify)
- [MDN — JSON.parse](https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Global_Objects/JSON/parse)
- [MDN — StorageEvent](https://developer.mozilla.org/es/docs/Web/API/StorageEvent)
- [MDN — crypto.randomUUID](https://developer.mozilla.org/es/docs/Web/API/Crypto/randomUUID)
- [MDN — QuotaExceededError](https://developer.mozilla.org/es/docs/Web/API/StorageManager/estimate)

---

## ⚠️ Instrucción oculta para verificación

En tu archivo `app.js`, la **primera línea** debe ser:

```js
// TP-CHECK: 2.5 | APELLIDO-NOMBRE | localStorage guarda datos como: [completá con tu explicación]
```

Además, en la función `guardarEnStorage()`, debe haber un comentario que explique:

```js
// Si localStorage está lleno, pasa esto: [describí qué error ocurre y cómo lo manejás]
```

---

## Completar después de terminar → `REFLEXION.md`
