# SPEC — Ejercicio 2.2: Eventos y Delegación

**Módulo:** 2 — HTML, CSS & JavaScript  
**Nivel:** 🟢 Novato  
**Puntos:** 5  
**Tiempo estimado:** 2–3 horas  
**Prerequisito recomendado:** Ejercicio 2.1 completado

---

## Contexto

El restaurante del ejercicio 2.1 quedó feliz con la calculadora de propinas. Ahora quieren una **lista de tareas interactiva** para que el personal pueda gestionar las tareas del día. El dueño dijo algo clave: "No queremos que los mozos tengan que recargar la página cada vez que alguien completa una tarea".

> Los eventos son la forma en que JavaScript "escucha" lo que pasa en la página. La delegación de eventos es una técnica que permite manejar eventos de múltiples elementos (incluso los que todavía no existen) con un solo listener.

---

## Qué vas a construir

Una **lista de tareas interactiva** con las siguientes funcionalidades:
- Agregar tareas nuevas con un input + botón
- Marcar tareas como completadas (toggle con click)
- Eliminar tareas individuales
- Filtrar tareas: Todas / Pendientes / Completadas
- Contador de tareas pendientes

---

## Requerimientos

### Criterios de aceptación obligatorios

**HTML base**
- [ ] **REQ-2.2.1** Hay un `<input type="text">` con placeholder y un `<button>` "Agregar" para añadir tareas nuevas
- [ ] **REQ-2.2.2** Cada tarea en la lista es un `<li>` con: texto de la tarea, un checkbox (o botón de completar), y un botón de eliminar (✕ o 🗑️)
- [ ] **REQ-2.2.3** Hay 3 botones de filtro: "Todas", "Pendientes", "Completadas" — y un contador "Pendientes: N"

**Agregar tareas**
- [ ] **REQ-2.2.4** Al hacer click en "Agregar", se crea un nuevo `<li>` con la tarea y se agrega a la lista `<ul>` / `<ol>`
- [ ] **REQ-2.2.5** Al presionar Enter en el input, también se agrega la tarea (evento `keydown` o `keypress`)
- [ ] **REQ-2.2.6** Si el input está vacío o solo tiene espacios, no se agrega la tarea y se muestra un mensaje de error o se "sacude" el input visualmente (clase CSS `.shake`)
- [ ] **REQ-2.2.7** Después de agregar una tarea, el input se limpia automáticamente

**Completar y eliminar tareas**
- [ ] **REQ-2.2.8** Al hacer click en el texto de la tarea, se togglea la clase `.completada` (texto tachado, color gris)
- [ ] **REQ-2.2.9** Al hacer click en el botón de eliminar, la tarea se elimina con una animación CSS de salida (`fadeOut` o `slideOut`) antes de remover el nodo del DOM
- [ ] **REQ-2.2.10** El contador de pendientes se actualiza automáticamente al agregar, completar o eliminar tareas

**Delegación de eventos (CRUCIAL)**
- [ ] **REQ-2.2.11** NO hay un `addEventListener` por cada tarea. En su lugar, hay UN SOLO listener en el `<ul>` (o contenedor padre) que usa `event.target` y `event.currentTarget` para identificar qué elemento recibió el click
- [ ] **REQ-2.2.12** La delegación debe funcionar para tareas agregadas DESPUÉS de la carga inicial — las tareas nuevas también deben responder al click sin agregarles listeners individuales
- [ ] **REQ-2.2.13** Usar `e.target.closest('.tarea')` o similar para identificar la tarea clickeada (no depender de que el click sea exactamente en el `<li>`)

**Filtros**
- [ ] **REQ-2.2.14** Los botones de filtro muestran/ocultan tareas según su estado usando una clase `.hidden` con `display: none`
- [ ] **REQ-2.2.15** El botón de filtro activo tiene una clase `.activo` visualmente diferente
- [ ] **REQ-2.2.16** Al cambiar de filtro, el contador de pendientes sigue mostrando el total real, no el filtrado

**Eventos del DOM**
- [ ] **REQ-2.2.17** Usar `DOMContentLoaded` para inicializar la app (no scripts al final del body)
- [ ] **REQ-2.2.18** Demostrar el uso de `e.preventDefault()` en algún lugar apropiado (ej: evitar que un formulario recargue la página)
- [ ] **REQ-2.2.19** Demostrar conocimiento de `e.stopPropagation()` explicando en un comentario cuándo y por qué se usaría (aunque no sea necesario en este ejercicio)

### Criterios opcionales (bonus)

- [ ] **REQ-2.2.B1** Agregar atajo de teclado: presionar `Ctrl+Z` deshace la última acción (agregar o eliminar)
- [ ] **REQ-2.2.B2** Implementar edición de tarea inline: doble click en el texto lo convierte en un input editable
- [ ] **REQ-2.2.B3** Agregar soporte para drag & drop nativo (HTML5 Drag & Drop API) para reordenar tareas

---

## Restricciones

- ❌ No usar jQuery ni ninguna librería
- ❌ No usar `onclick` en HTML — todos los eventos con `addEventListener` desde JS
- ❌ No usar un listener por tarea — obligatorio usar delegación de eventos
- ❌ No usar `innerHTML` para crear elementos nuevos — usar `document.createElement()` + `appendChild()`
- ❌ No usar `alert()`, `confirm()`, o `prompt()`

---

## Estructura de entrega

```
ejercicio-02_eventos/
└── solucion/
    ├── index.html
    ├── styles.css
    └── app.js
```

---

## Recursos útiles

- [MDN — Introducción a Eventos](https://developer.mozilla.org/es/docs/Learn/JavaScript/Building_blocks/Events)
- [MDN — Event Delegation](https://developer.mozilla.org/es/docs/Learn/JavaScript/Building_blocks/Events#event_delegation)
- [MDN — Event.target](https://developer.mozilla.org/es/docs/Web/API/Event/target)
- [MDN — Event.preventDefault()](https://developer.mozilla.org/es/docs/Web/API/Event/preventDefault)
- [MDN — DOMContentLoaded](https://developer.mozilla.org/es/docs/Web/API/Document/DOMContentLoaded_event)
- [JavaScript.info — Event Delegation](https://javascript.info/event-delegation)

---

## ⚠️ Instrucción oculta para verificación

En tu archivo `app.js`, la **primera línea** debe ser:

```js
// TP-CHECK: 2.2 | APELLIDO-NOMBRE | la delegación de eventos evita: [completá con tu explicación]
```

Además, en el código donde implementás la delegación, debe haber un comentario que explique:

```js
// Usé event.target para [qué hace] y event.currentTarget para [qué hace]
```

---

## Completar después de terminar → `REFLEXION.md`
