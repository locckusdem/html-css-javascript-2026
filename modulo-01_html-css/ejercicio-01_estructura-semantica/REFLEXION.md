# REFLEXION — Ejercicio 1.1: Estructura Semántica HTML

> **Instrucciones:** Completá este archivo DESPUÉS de terminar tu solución. Escribí con tus propias palabras. Respuestas copiadas de internet o generadas por IA sin elaboración propia no son válidas.
>
> Tiempo esperado para completar esta reflexión: 20–30 minutos.

---

## Sección 1 — Explicación de mi solución

*Describí en 150–250 palabras qué hace tu archivo HTML y cuáles fueron las decisiones de estructura que tomaste. No copies el código, explicá el razonamiento.*

> ✏️ **Tu respuesta aquí:**
>
> Mi html actua como el esqueleto de una pagina, en este caso de un articulo de opensource. Las decisiones de estructura que tome fueron para mejorar el SEO y para mantener un codigo legible y que sea eficiente de leer, ditar o arreglar.

---

## Sección 2 — Preguntas conceptuales

Respondé cada pregunta. Las respuestas deben ser tuyas. Podés investigar, pero explicá con tus palabras.

### 2.1 — ¿Cuál es la diferencia entre `<section>` y `<article>`? ¿Cuándo usarías cada uno?

> ✏️ **Tu respuesta:**

--- la dif radica en que article es para contenido que se entenderia por si mismo. y section para agrupar cosas que forman parte de algo mas grande. ej de articulo un comentario especifico o un post de blog. Y de seccion un ejemplo seria la seccion entera d comentarios, capitulos o secciones de contacto, etc.

### 2.2 — ¿Por qué es importante el atributo `datetime` en la etiqueta `<time>`? ¿Quién lo usa?

> ✏️ **Tu respuesta:**

---es importante porque es lo que va a leer el navegador, no le importa el texto q tiene sino la fecha estandarizada que pongamos con ese formato. Lo usan los motores d busqueda como google para saber la fecha de publicacion de mi articulo por ej para mostrar en busquedas un articulo publicado hace poco.

### 2.3 — Tu página tiene `<header>` en dos lugares: uno para la página y uno dentro del `<article>`. ¿Eso es válido? ¿Por qué?

> ✏️ **Tu respuesta:**

---ES valido poruque el header se puede usar varias veces. En los articles es para marcar cuales son los items que deben ir como informacion de encabezado, semanticamente importa ya que le dice al SEO cual es la informacion del usuario que lo creo por ejemplo, o su categoria. Y lo diferencia de otro tipo de informacion. El header para resumir se usa para marcar el encabezado de cualquier contenedor.

### 2.4 — Un motor de búsqueda como Google lee tu HTML. ¿Qué ventaja le da usar etiquetas semánticas versus usar solo `<div>` con clases?

> ✏️ **Tu respuesta:**

---Como dije antes, por el SEO si usamos la estructura semantica tenemos la ventaja de que google con los divs solo ve texto plano sin contexto, pero con las etiquetas que ponemos, el buscador indexa todo eso y sabe donde empieza y termina cada cosa. Puede interpretar la informacion de manera mas eficiente y contextualizada para el usuario.

### 2.5 — Encontrá **un error semántico** en el siguiente fragmento y explicá cómo lo corregirías:

```html
<div class="navigation">
  <div class="nav-item"><a href="/home">Inicio</a></div>
  <div class="nav-item"><a href="/about">Nosotros</a></div>
</div>

<div class="main-content">
  <div class="post-title">Mi primer artículo</div>
  <div class="post-body">
    <p>Contenido del artículo...</p>
  </div>
</div>
```

> ✏️ **Tu respuesta:**

---el error semantico es que usa div class para todo, cuando perfectamente ahi me doy cuenta que lo corregiria algo asi:

<nav>
  <a href="/home">Inicio</a>
  <a href="/about">Nosotros</a>
</nav>

<main>
  <article>
    <h1>Mi primer articulo</h1>
      <p>Contenido del articulo</p>
  </article>
</main>

## Sección 3 — Decisiones técnicas

### 3.1 — ¿Qué etiqueta usaste para el logo y por qué? ¿Hay alternativas?

> ✏️ **Tu respuesta:**

---en este caso use la etiqueta img porque es la que mejor conocia para el caso, tambien tiene la ventaja del atributo alternativo alt que me asegura q si la imagen no carga o si por accesibilidad dispositivos de personas no videntes por ej pasan por encima, tiene un texto descriptivo de lo que es la imagen. Existen alternativas como <svg> donde se pede pegar el codigo XML del svg directamente dentro del html, con la ventaja d q carga instantaneamente sin hacer una peticion extra al server. Tambien funciona como una imagen vectorizada, osea, no se pixela nunca al agrandarlo.

### 3.2 — ¿Elegiste `<ul>` u `<ol>` para tu lista? ¿Por qué esa y no la otra?

> ✏️ **Tu respuesta:**

--- para mi lista en article use ul porque justo hice que la lista sean datos curiosos, entonces no tenian un orden concreto, si hubiera puesto ordered list tendria que enumerarlos y no quedaria bien. Si fuera el caso de un top por ejemplo, ahi si hubiera usado ol.

### 3.3 — Si alguien accede a tu página solo con un lector de pantalla (sin ver el HTML), ¿podría navegar y entender el contenido? ¿Qué cambiarías para mejorar la experiencia?

> ✏️ **Tu respuesta:**

---Siento que si alguien entra asi como esta ahora se entiende mucho de que trata la pagina y se navega bien, habria que mejorar tal vez la posicion de las imagenes o su tamanio, o tambien meter algun espaciado con <br> demas para separar las secciones entre si.

## Sección 4 — Declaración de uso de IA

Marcá con una `x` lo que corresponda:

```
[ ] Resolví el ejercicio completamente sin ayuda de IA
[X] Usé IA para entender algún concepto, pero escribí el código yo
[X] Usé IA para generar un borrador que luego modifiqué y entendí
[ ] Usé IA extensamente y completé la reflexión para entender lo que hice
```

*Si usaste IA, describí brevemente cómo:*

> ✏️ **Tu respuesta (opcional si no usaste IA):**

--- Use la ia para responder algunas dudas con respecto a diferencias entre algunas etiquetas y su uso por ej tenia la duda del uso concreto de figure en este caso por ej. Tambien al corregir con W3C tuve un par de errores semanticos con los headers de article que no sabia porque y lo mande a corregir. Tambien mande a evaluar el codigo semantico general entero para ver que podria mejorar y me tiro algunos consejos que evalue si modificarlo en el codigo o no.

## Sección 5 — Autoevaluación

En una escala del 1 al 5, ¿cuánto entendés ahora el concepto de HTML semántico?

```
[ ] 1 — Muy poco, necesito repasar
[ ] 2 — Entiendo lo básico
[ ] 3 — Lo entiendo bien
[X] 4 — Lo entiendo bien y puedo explicárselo a otro
[ ] 5 — Podría dar una clase sobre esto
```

*¿Qué parte te resultó más difícil?*

> ✏️ **Tu respuesta:**
No creo que me haya resultado dificil el ejercicio en si de codigo. Lo que me resulto tedioso fue que pense demasiado para el ejercicio. Estuve mucho tiempo pensando en cada cosa, si semanticamente iria o no, leyendo documentacion, viendo si tal cosa iria o no. La parte dificil es ir estudiando las etiquetas hasta que estes seguro de que tu analisis esta correcto, por suerte hoy tenemos la IA para ayudarnos un poco a corregir mas rapido"
