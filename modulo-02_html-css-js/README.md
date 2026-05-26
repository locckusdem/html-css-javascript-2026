# Módulo 2 — HTML, CSS & JavaScript

> **Prerequisito:** Módulo 1 completado. Este módulo presupone que sabés HTML semántico, CSS (Flexbox, Grid, Responsive, Variables, Animaciones).

## Progresión de dificultad

```
🟢 Novato             🟡 Intermedio                🔴 Avanzado          ⚫ Experto
[2.1] [2.2]     →→→   [2.3] [2.4] [2.5]     →→→   [2.6]          →→→   [2.7]
```

## Antes de empezar — Conceptos base

Si necesitás repasar conceptos de JavaScript antes de arrancar:

- [MDN — Introducción a JavaScript](https://developer.mozilla.org/es/docs/Learn/JavaScript/First_steps)
- [MDN — DOM (Document Object Model)](https://developer.mozilla.org/es/docs/Web/API/Document_Object_Model/Introduction)
- [MDN — JavaScript Asíncrono](https://developer.mozilla.org/es/docs/Learn/JavaScript/Asynchronous)
- [JavaScript.info — The Modern JavaScript Tutorial](https://javascript.info/)

## Herramientas recomendadas

- Editor: VS Code con extensión "Live Server" (importante: los módulos ES6 requieren servidor)
- Navegador: Chrome o Firefox con DevTools abiertos (F12)
- Consola del navegador para debugging
- `npx serve .` para servir archivos con módulos ES6 localmente

## Cómo navegar los ejercicios

Cada carpeta de ejercicio contiene:

```
ejercicio-XX_nombre/
├── SPEC.md        ← Lee esto primero. Son los requerimientos.
├── REFLEXION.md   ← Completá esto DESPUÉS de terminar el código.
└── solucion/      ← Acá va todo tu código.
    └── (vacío — vos lo llenás)
```

> 💡 **Importante:** Los ejercicios de este módulo se construyen uno sobre el otro. El 2.6 específicamente es una refactorización del 2.5. Hacelos en orden.

## Diferencia clave con el Módulo 1

En el Módulo 1 todo era HTML + CSS estático. Acá entra JavaScript a la cancha. Vas a:

1. **Manipular el DOM** — crear, modificar y eliminar elementos en vivo
2. **Manejar eventos** — escuchar clicks, teclas, formularios
3. **Consumir APIs** — hablar con servidores usando fetch
4. **Persistir datos** — guardar información en el navegador con localStorage
5. **Estructurar código** — módulos ES6 y patrones de diseño
6. **Crear componentes reutilizables** — Web Components con Shadow DOM

Cada ejercicio introduce UN concepto nuevo y lo lleva al máximo antes de pasar al siguiente.
