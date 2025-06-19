## CSS - Selectores Completos

CSS permite aplicar estilos de forma selectiva a elementos HTML mediante **selectores**. Aquí tienes una síntesis clara, organizada por tipo de selector, con explicaciones, ejemplos y estructura visual pensada para facilitar el aprendizaje.

---

### 🟢 Selector Universal

| Selector | Uso / Explicación                  | Ejemplo CSS        | Resultado HTML                        |
| -------- | ---------------------------------- | ------------------ | ------------------------------------- |
| `*`      | Selector universal. Afecta a todo. | `* { margin: 0; }` | Aplica margen 0 a todos los elementos |

* **Descripción**: Selecciona **todos los elementos** del documento HTML. Es el selector con **menor especificidad**.
* **Uso común**: Se emplea frecuentemente para hacer reseteos de márgenes y paddings al inicio de un CSS.

```css
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
```

---

### 🔵 Selector de Etiqueta

| Selector   | Uso / Explicación                | Ejemplo CSS         | Resultado HTML           |
| ---------- | -------------------------------- | ------------------- | ------------------------ |
| `elemento` | Selector de tipo (etiqueta HTML) | `p { color: red; }` | `<p>Texto</p>` será rojo |

* **Sintaxis**: Se escribe directamente el nombre de la etiqueta HTML (sin < >).
* **Ejemplo**:

```css
p {
  font-size: 16px;
  line-height: 1.5;
}
```

---

### 🟣 Selector de Clase

| Selector | Uso / Explicación                  | Ejemplo CSS             | Resultado HTML              |
| -------- | ---------------------------------- | ----------------------- | --------------------------- |
| `.clase` | Selecciona elementos con una clase | `.rojo { color: red; }` | `<p class="rojo">Texto</p>` |

* **Uso**: Para aplicar estilos a uno o más elementos que compartan una clase común.
* **Ejemplo**:

```css
.azul {
  color: blue;
}
```

**Multiclase**: También se puede combinar varias clases en un selector.

```css
.azul.grande {
  font-size: 24px;
}
```

---

### 🔶 Selector de ID

| Selector | Uso / Explicación                | Ejemplo CSS                   | Resultado HTML              |
| -------- | -------------------------------- | ----------------------------- | --------------------------- |
| `#id`    | Selecciona un elemento por su ID | `#titulo { font-size: 2em; }` | `<h1 id="titulo">Hola</h1>` |

* **Uso**: Selecciona un único elemento por su `id`, ya que **no debe repetirse** en el documento.
* **Ejemplo**:

```css
#cabecera {
  background-color: gray;
}
```
**Nota**: Su especificidad es más alta que la de una clase.

---

### 🟡 Selectores Mixtos (Combinados)

Los **selectores mixtos** combinan dos o más tipos de selectores básicos para ser más específicos al aplicar estilos.

| Selector combinado | Uso / Explicación                      | Ejemplo CSS             | Resultado HTML                         |
| ------------------ | -------------------------------------- | ----------------------- | -------------------------------------- |
| `*.clase`          | Universal + clase                      | `*.destacado { ... }`   | `<p class="destacado">...</p>`         |
| `*#id`             | Universal + id                         | `*#principal { ... }`   | `<div id="principal">...</div>`        |
| `etiqueta.clase`   | Etiqueta + clase                       | `p.nota { ... }`        | `<p class="nota">...</p>`              |
| `.clase1.clase2`   | Elemento con ambas clases              | `.rojo.grande { ... }`  | `<span class="rojo grande">...</span>` |
| `etiqueta#id`      | Etiqueta con id específico             | `section#intro { ... }` | `<section id="intro">...</section>`    |
| `#id.clase`        | Elemento con ese id y clase específica | `#menu.activo { ... }`  | `<div id="menu" class="activo"></div>` |

Combinaciones comunes:

```css
/* Selecciona todos los <p> que tengan la clase azul y los pone en negrita.*/
p.azul {
  font-weight: bold;
}

/*Selecciona el elemento con id titulo y clase azul, y pone su texto en mayúsculas.*/
#titulo.azul {
  text-transform: uppercase;
}

/*Selecciona el <div> con id menu y clase principal, y le añade un borde negro.*/
div#menu.principal {
  border: 1px solid black;
}
```

**Ventaja**: Puedes hacer selecciones más precisas sin necesidad de añadir más clases.


---

### 🟧 Selectores de Atributo Básicos

Permiten seleccionar elementos HTML que poseen un atributo específico o un valor concreto para ese atributo.

```css
/* Elementos con cualquier valor en class */
p[class] {
  color: blue;
}

/* Elementos con clase exactamente igual a "azul" */
p[class="azul"] {
  color: blue;
}
```

```html
<p class="azul">Este texto será azul.</p>
<p class="rojo">Este texto no será azul.</p>
<p>Este texto tampoco será azul.</p>
```

* **Formato**:

  * `[atributo]`: Elementos que tienen el atributo.
  * `[atributo="valor"]`: Atributo con valor exacto.

```css
p[class] {
  color: green;
}

input[type="text"] {
  border: 1px solid gray;
}
```

---

### 🟥 Selectores de Atributo Avanzados

| Selector              | Significado                                                                         |                                                                           |
| --------------------- | ----------------------------------------------------------------------------------- | ------------------------------------------------------------------------- |
| `[atributo]`          | Tiene el atributo especificado                                                      |                                                                           |
| `[atributo="valor"]`  | El atributo es exactamente igual a "valor"                                          |                                                                           |
| `[atributo~="valor"]` | El atributo contiene una lista de valores separados por espacios, e incluye "valor" |                                                                           |
| \`\[atributo          | ="valor"]\`                                                                         | El atributo empieza con "valor" y puede ir seguido de un guion (ej: lang) |

**Ejemplos**:

```css
div[class~="importante"] {
  color: red;
}

p[lang|="es"] {
  font-style: italic;
}
```


```css
/* 1. Selecciona cualquier elemento que tenga el atributo disabled y le pone fondo gris. */
[disabled] {
  background: grey;
}

/* 2. Selecciona los enlaces <a> cuyo atributo rel sea exactamente "nofollow" y les pone fondo rojo. */
a[rel="nofollow"] {
  background: red;
}

/* 3. Selecciona los elementos cuyo atributo data-mood contenga la palabra "happy" en una lista de valores y les aplica fondo verde, texto blanco y padding. */
[data-mood~="happy"] {
  background: green;
  color: white;
  padding: 5px;
}

/* 4. Selecciona los elementos cuyo atributo lang sea "es" o empiece por "es-" (como "es-ES") y los pone en cursiva. */
[lang|="es"] {
  font-style: italic;
}

/* 5. Selecciona los enlaces <a> cuyo atributo href empieza por "https://" y los pone de color verde. */
a[href^="https://"] {
  color: green;
}

/* 6. Selecciona los enlaces <a> cuyo atributo href termina en ".pdf" y los pone de color naranja. */
a[href$=".pdf"] {
  color: orange;
}

/* 7. Selecciona los enlaces <a> cuyo atributo href contiene la palabra "manzdev" y los pone de color morado. */
a[href*="manzdev"] {
  color: purple;
}
```

---

### Selector descendente

Selecciona todos los elementos que estén dentro de otro, sin importar el nivel de anidación.

| Selector | Uso / Explicación                                                      | Ejemplo         | Resultado                               |
| -------- | ---------------------------------------------------------------------- | --------------- | --------------------------------------- |
| `a b`    | Selecciona todos los elementos `b` dentro de `a` (hijos, nietos, etc.) | `#contenedor p` | Todos los `<p>` dentro de `#contenedor` |

**Ejemplo:**

```css
#page div {
  background-color: lightblue;
}
```

```html
<div id="page">
  <div>Contenido azul</div>
  <section>
    <div>También azul</div>
  </section>
</div>
```
- Explicación del ejemplo: Lógica del selector descendiente #page div:

El selector #page div selecciona todos los elementos <div> que estén dentro de un elemento con id="page", sin importar cuántos niveles de anidación haya entre ellos.
Esto significa que tanto el <div> hijo directo de #page como el <div> que está dentro de <section> (nieto de #page) recibirán el estilo background-color: lightblue;.
El selector descendiente funciona porque busca cualquier <div> que sea descendiente (hijo, nieto, bisnieto, etc.) del elemento con id page.
Resumen:
Todos los <div> que estén dentro de <div id="page">, sin importar su profundidad, tendrán fondo azul claro.

**Otro ejemplo**

```css
/* Forma 2: Más general, menos específica */
.menu a {
  color: orange;
}
```
```html
<div class="menu">
  <div class="options">
    <ul>
      <li><a href="/one">Option 1</a></li>
      <li><a href="/two">Option 2</a></li>
      <li><a href="/three">Option 3</a></li>
    </ul>
  </div>
</div>
```
El selector .menu a se usa para aplicar estilos a todos los enlaces `<a>` que estén dentro de un elemento con la clase menu. Funciona porque selecciona cualquier `<a>` descendiente de .menu, sin importar cuán anidado esté, permitiendo así cambiar el color de todos los enlaces dentro del menú de forma sencilla y general. Vemos que a no es hijo de menu sino que es descendiente, y aun así funciona igual.

---

### Selector de hijo directo

Selecciona solo los hijos **inmediatos** de un elemento.

| Selector | Uso / Explicación                                     | Ejemplo   | Resultado                            |
| -------- | ----------------------------------------------------- | --------- | ------------------------------------ |
| `a > b`  | Selecciona los `b` que sean **hijos directos** de `a` | `ul > li` | Solo `<li>` hijos directos de `<ul>` |

**Ejemplo:**

```css
/*El selector aplica estilos únicamente a los elementos <p> que son hijos directos de un <section>*/
section > p {
  color: green;
}
```

```html
<section>
  <p>Verde</p>
  <div>
    <p>No se verá verde</p>
  </div>
</section>
```

---

### Selector de hermanos generales

Selecciona todos los hermanos que aparecen después del elemento indicado, sin importar si son adyacentes o no.

| Selector | Uso / Explicación                                                                    | Ejemplo  | Resultado                      |
| -------- | ------------------------------------------------------------------------------------ | -------- | ------------------------------ |
| `a ~ b`  | Selecciona todos los elementos `b` que estén al mismo nivel que `a` y vengan después | `h2 ~ p` | Todos los `<p>` tras un `<h2>` |

**Ejemplo:**

```css
/*l selector aplica estilos a todos los elementos <p> que sean hermanos del mismo nivel y estén después de un <h2>, haciendo que todos esos párrafos se muestren en cursiva.*/
h2 ~ p {
  font-style: italic;
}
```
**Otro ejemplo**:

```html
<h2>Título</h2>
<p>Este párrafo será itálico</p>
<p>Y este también</p>
```

```html
<div id="main">
  <div class="article">
    <em>Primer énfasis</em>
    <span>Texto intermedio</span>
    <em>Segundo énfasis</em> <!-- Seleccionado -->
    <span>Más texto</span>
    <em>Tercer énfasis</em> <!-- Seleccionado -->
  </div>
  <div class="sidebar">
    <em>No se selecciona</em>
    <span>Texto</span>
    <em>Tampoco se selecciona</em>
  </div>
</div>
```

```css
div.article em ~ em {
  color: red;
}
```
Explicación:
El selector div.article em ~ em selecciona todos los elementos `<em>` que sean hermanos del mismo nivel y estén después de otro `<em>` dentro de un `<div class="article">`, sin importar si hay otros elementos entre ellos. Ambos `<em>` marcados como "Seleccionado" serán afectados por el selector, ya que son hermanos posteriores a otro `<em>` dentro de .article. El primer `<em>` no se selecciona porque el selector em ~ em solo afecta a los elementos `<em>` que tienen un hermano `<em>` anterior al mismo nivel. El primero no tiene ningún `<em>` antes de él, por lo que no cumple la condición del selector.

---

### Selector de hermano adyacente

Selecciona el **primer** hermano que aparece justo después del elemento indicado.

| Selector | Uso / Explicación                                                  | Ejemplo  | Resultado                         |
| -------- | ------------------------------------------------------------------ | -------- | --------------------------------- |
| `a + b`  | Selecciona `b` si aparece **justo después** de `a`, al mismo nivel | `h2 + p` | Primer `<p>` después de un `<h2>` |

**Ejemplo:**

```css
/*El selector selecciona únicamente el primer <p> que aparece inmediatamente después de un <h2>, aplicándole el estilo definido. No afecta a otros <p> que no sean adyacentes a un <h2>.*/
h2 + p {
  font-weight: bold;
}
```

```html
<h2>Título</h2>
<p>Este párrafo estará en negrita</p>
<p>Este no</p>
```

**Otro ejemplo:**

```css
/*El selector selecciona cada <span> que aparece inmediatamente después de otro <span> dentro de un <div class="post">, aplicándole el estilo solo al hermano adyacente.*/
div.post span + span {
  background-color: gold;
}
```

```html
<div class="post">
  <strong>Importante</strong>
  <span>Texto 1</span>
  <span>Texto 2</span> <!-- gold -->
  <em>Énfasis</em>
  <span>Texto 3</span>
  <span>Texto 4</span> <!-- gold -->
</div>
```

```html
<div class="post">
  <span>Uno</span>
  <span>Dos</span>    <!-- gold -->
  <span>Tres</span>   <!-- gold -->
  <em>Separador</em>
  <span>Cuatro</span>
  <span>Cinco</span>  <!-- gold -->
</div>
```
En este ejemplo, "Dos", "Tres" y "Cinco" tendrán fondo gold porque están inmediatamente después de otro `<span>`. Pero "Uno" y "Cuatro" no van seguidos de un hermano `<span>` asi que no serían de color dorado.
---

### Selector múltiple

Permite aplicar los mismos estilos a varios elementos distintos separados por comas.

| Selector | Uso / Explicación                                      | Ejemplo      | Resultado                                 |
| -------- | ------------------------------------------------------ | ------------ | ----------------------------------------- |
| `a, b`   | Aplica los estilos a todos los elementos seleccionados | `h1, h2, h3` | Todos los títulos tendrán el mismo estilo |

**Ejemplo:**

```css
h1, h2, h3 {
  text-transform: uppercase;
}
```

**Otro ejemplo:**
```css
.container-logo,
.container-alert,
.container-warning {
  border-color: white;
  background: red;
}
```
```html
<div class="container-logo">Logo</div>
<div class="container-alert">¡Alerta!</div>
<div class="container-warning">Advertencia</div>
<div class="container-info">Información</div>
```
En este ejemplo, los elementos (en este caso divs) con clase container-logo, container-alert y container-warning tendrán fondo rojo y borde blanco, pero el div con clase container-info no será afectado.

---

### Selector universal

Aplica estilos a **todos los elementos**.

| Selector | Uso / Explicación                   | Ejemplo            | Resultado                               |
| -------- | ----------------------------------- | ------------------ | --------------------------------------- |
| `*`      | Selecciona todos los elementos HTML | `* { margin: 0; }` | Elimina márgenes de todos los elementos |

Se puede combinar con otras etiquetas para hacer selectores específicos paro coger TODO lo que hay dentro de lo específico.

**Ejemplo:**
```css
div#panel * {
  color: blue;
  font-family: Arial, sans-serif;
}
```
```html
<div id="panel">
  <section>
    <h2>Título</h2>
    <p>Texto principal</p>
    <div class="info">
      <span>Dato 1</span>
      <span>Dato 2</span>
    </div>
  </section>
  <footer>
    <p>Pie de página</p>
  </footer>
</div>
```
- Explicación:
El selector div#panel * aplica los estilos a todos los elementos que sean descendientes de `<div id="panel">`, sin importar su tipo o nivel de anidamiento. El asterisco (*) es el selector universal y, combinado con un selector descendente (el espacio), afecta a todos los nodos hijos dentro del contenedor especificado(`<div id="panel">`).

---

### Importancia de un espacio y un punto

* `a.clase` → selecciona los elementos `<a>` que tienen clase `clase`
* `a .clase` → selecciona los elementos con clase `clase` **dentro de** un `<a>` (descendientes)
* `a, .clase` → aplica estilos tanto a todos los `<a>` como a todos los elementos con clase `clase`

**Ejemplo aclaratorio:**

```css
a .boton {
  color: red; /* Solo si .boton está dentro de un <a> */
}

a.boton {
  color: blue; /* Solo si el <a> tiene clase boton */
}
```

---

### Ejercicios de ejemplo:
- Selecciona los elementos div que sean hijos de otro div:
```css
div > div
```


- Selecciona los hijos de los elementos p:
```css
p > *
```

- Selecciona los elementos p que sean hijos de article:
```css
article p
```

- Selecciona los p que esten dentro de un article:
```css
article p
```

- Selecciona los titulos h1 y los h3:
```css
h1, h3
```

- Selecciona los ol que esten dentro de body:
```css
body ol
```

- Cualquier elemento que tenga la clase “amarillo”:
```css
.amarillo
```

- Los elementos `<ul>` que sean hijos de `<body>`:
```css
body > ul
```

- Los elementos `<a>` que sean hijos de `<p>`:
```css
p > a
```

- Selecciona el elemento con id “platano”:
```css
#platano
```

- Todos los elementos `<div>` que sean hermanos de un elemento `<h2>`:
```css
h2 ~div
```

- Todos los elementos`<p>` con clase = parisa, descendientes de un elemento `<ul>`:
```css
ul p.parisa
```

- Selecciona los `<h1>`, `<h2>`, `<h3>` que tengan la clase "headertitle", hijos del header:
```css
header > h1.headertitle, header > h2.headertitle, header > h3.headertitle
```

---

### 🟢 Pseudoclases de interacción

Estas pseudoclases se activan cuando el usuario interactúa con el elemento (hover, foco, clic).

| Pseudoclase     | Uso / Explicación                                              |
| --------------- | -------------------------------------------------------------- |
| `:hover`        | Se activa cuando el ratón está sobre el elemento               |
| `:active`       | Se activa cuando el elemento está siendo pulsado (clic activo) |
| `:focus`        | Se activa cuando el elemento tiene el foco (teclado o ratón)   |
| `:focus-within` | Se activa si algún hijo del elemento recibe el foco            |

**Ejemplo de interacción con foco y hover:**

```css
button:hover {
  background-color: lightblue;
}

input:focus {
  border: 2px solid blue;
}

form:focus-within {
  border: 2px dashed green;
}
```

```html
<form>
  <label>Nombre:
    <input type="text">
  </label>
  <button>Enviar</button>
</form>
```

En este ejemplo, al enfocar el `input`, también se aplica un estilo al `form` contenedor gracias a `:focus-within`.

**Otro Ejemplo:**

```css
<style>
button:hover {
  background: orange;
}

button:active {
  background: red;
  color: white;
}

input:focus {
  border: 2px solid blue;
}

.box:focus-within {
  background: #e0f7fa;
}
</style>
```

```html
<button>Botón</button>
<input type="text" placeholder="Escribe aquí">
<div class="box">
  <input type="text" placeholder="Dentro del div">
</div>
```

- Explicación rápida:

:hover aplica estilos cuando el mouse está sobre el botón.
:active aplica estilos mientras el botón está siendo presionado.
:focus aplica estilos cuando el input está enfocado.
:focus-within aplica estilos al div .box si alguno de sus hijos recibe el foco.

---

### 🔵 Pseudoclases de hijos (por posición)

| Pseudoclase          | Explicación                                               |
| -------------------- | --------------------------------------------------------- |
| `:first-child`       | Selecciona el primer hijo de su padre                     |
| `:last-child`        | Selecciona el último hijo                                 |
| `:nth-child(n)`      | Selecciona el hijo número n (o con fórmula como `2n+1`)   |
| `:nth-last-child(n)` | Igual que `nth-child`, pero cuenta desde el final         |
| `:only-child`        | Selecciona un hijo único (cuando es el único hijo)        |
| `:empty`             | Selecciona elementos sin hijos ni contenido (ni espacios) |

**Ejemplo con varios tipos de hijos:**
Cada selector usa una pseudoclase para seleccionar elementos `<li>` según su posición dentro del `<ul>`:

```css
/*Selecciona el primer <li> hijo de cada <ul>.*/
ul li:first-child {
  font-weight: bold;
}
/*Selecciona los <li> en posiciones impares.*/
ul li:nth-child(odd) {
  background: #f0f0f0;
}
/* Selecciona todos los elementos en posición par */
ul li:nth-child(even) {
  background: #e0f7fa;
}
/* Selecciona todos los elementos en posición múltiplo de 3 */
ul li:nth-child(3n) {
  color: green;
}
/* Selecciona el 4º, 7º, 10º, etc. */
ul li:nth-child(3n+1) {
  font-weight: bold;
}
/* Selecciona solo el segundo elemento */
ul li:nth-child(2) {
  text-decoration: underline;
}
/* Selecciona los elementos a partir del quinto */
ul li:nth-child(n+5) {
  background: #ffe0b2;
}
/*Selecciona el penúltimo <li> de cada <ul>.*/
ul li:nth-last-child(2) {
  color: red;
}
/*Selecciona el <li> si es el único hijo del <ul>.*/
ul li:only-child {
  color: orange;
}
```

```html
<ul>
  <li>Primero</li>
  <li>Segundo</li>
  <li>Tercero</li>
</ul>

<ul>
  <li>Único</li>
</ul>
```
Estas pseudoclases permiten aplicar estilos según la posición o cantidad de los elementos dentro de su contenedor.

**Otro ejemplo:**
```css
li:nth-child(3) {
  background: lightgreen;
}
```
```html
<ul>
  <li>Primer elemento</li>
  <li>Segundo elemento</li>
  <li>Tercer elemento</li>
  <li>Cuarto elemento</li>
  <li>Quinto elemento</li>
</ul>
```
- Explicación:
El selector li:nth-child(3) selecciona el tercer `<li>` dentro de su contenedor `<ul>`, aplicándole el estilo solo a ese elemento según su posición.

---

### 🟣 Pseudoclases de hijos (por tipo)

Estas pseudoclases funcionan como las anteriores, pero teniendo en cuenta solo los elementos del mismo tipo (etiqueta).

| Pseudoclase            | Explicación                                        |
| ---------------------- | -------------------------------------------------- |
| `:first-of-type`       | Primer hijo del mismo tipo (por etiqueta)          |
| `:last-of-type`        | Último hijo del mismo tipo                         |
| `:nth-of-type(n)`      | Hijo número n del mismo tipo                       |
| `:nth-last-of-type(n)` | Igual que el anterior pero contando desde el final |
| `:only-of-type`        | Es el único hijo de ese tipo                       |

**Ejemplo de combinación con tipo:**

```css
/*Selecciona el primer <p> de su tipo dentro de su contenedor y lo pone en cursiva.*/
p:first-of-type {
  font-style: italic;
}
/*Selecciona el segundo <strong> dentro del mismo contenedor, ignorando otros tipos de elementos, y lo colorea de azul.*/
strong:nth-of-type(2) {
  color: blue;
}
```

```html
<div>
  <p>Este párrafo es el primero de su tipo</p>
  <strong>Uno</strong>
  <em>Algo</em>
  <strong>Dos (azul)</strong>
</div>
```

En este ejemplo, `strong:nth-of-type(2)` aplica al segundo `<strong>`, ignorando otros elementos distintos.

**Otro ejemplo:**
```css
<style>
.container div:first-of-type {
  /* Selecciona "Element 1" */
  color: red;
}

.container p:first-of-type {
  /* Selecciona "Element 3" */
  color: blue;
}

.container :first-of-type {
  /* Selecciona los dos anteriores */
  font-weight: bold;
}
</style>
```

```html
<div class="container">
  <div class="element">Element 1</div>
  <div class="element">Element 2</div>
  <p class="element">Element 3</p>
  <div class="element">Element 4</div>
</div>
```

Los selectores `:first-of-type` permiten seleccionar el primer hijo de cada tipo de etiqueta dentro de un contenedor, ignorando los demás tipos. Por ejemplo, `.container div:first-of-type` selecciona solo el primer `<div>` dentro de `.container`, aunque haya otros elementos antes o después.



---

### 🟠 Pseudoclases de ubicación (enlaces)

| Pseudoclase | Explicación                                      |
| ----------- | ------------------------------------------------ |
| `:link`     | Selecciona enlaces no visitados                  |
| `:visited`  | Selecciona enlaces ya visitados por el navegador |

**Ejemplo de estilizado de enlaces según visita:**

```css
a:link {
  color: blue;
}

a:visited {
  color: purple;
}
```

```html
<a href="https://google.com">Google</a>
<a href="https://tusitio.com">Tu Sitio</a>
```

---

### 🔺 Ejemplo completo con múltiples pseudoclases

```css
article p:nth-child(2) {
  color: green;
}

article p:last-of-type {
  text-transform: uppercase;
}

article p:only-of-type {
  background: yellow;
}
```

```html
<article>
  <p>Primero</p>
  <p>Segundo (verde)</p>
  <h2>Título</h2>
  <p>Último (mayúsculas)</p>
</article>
```

### Ejercicios extra: Selectores CSS correspondientes

1.  **El primer elemento `<a>` hijo de `<p>`**
    ```css
    p > a:first-of-type
    ```
2.  **Selecciona los checkbox que estén marcados, hijos de un `<form>`**
    ```css
    form > input[type="checkbox"]:checked
    ```
3.  **Selecciona el último `<p>` que sea descendiente de `<article>`**
    ```css
    article p:last-of-type
    ```
4.  **Seleccionar el segundo hijo de un elemento `section`**
    ```css
    section > :nth-child(2)
    ```
5.  **Seleccionar los hijos pares de un elemento `ol`**
    ```css
    ol > li:nth-child(even)
    ```
6.  **Seleccionar el antepenúltimo `li` de un `ul` de longitud indefinida**
    ```css
    ul > li:nth-last-child(3)
    ```
7.  **El segundo `<a>` de dentro de un `<p>`**
    ```css
    p a:nth-of-type(2)
    ```
8.  **Los `button` que sean hijos únicos**
    ```css
    button:only-child
    ```
9.  **Los `span` que sean primeros hijos de un `p`**
    ```css
    p > span:first-child
    ```
10. **Penúltimo hijo de `body`**
    ```css
    body > :nth-last-child(2)
    ```
---

## Pseudoclases de Formulario y Pseudoelementos

Las **pseudoclases de formulario** permiten aplicar estilos a los elementos de un formulario según su estado o interacción (por ejemplo, si un campo está habilitado, deshabilitado o si su contenido es válido). Por otro lado, los **pseudoelementos** son palabras clave que se añaden a un selector para dar estilo a una parte específica del elemento seleccionado (como la primera letra, o para insertar contenido antes o después).

---

### 🟢 Pseudoclases de Interacción en Formularios

Estas pseudoclases se activan según la interacción directa del usuario con los controles del formulario, como marcar una casilla.

| Pseudoclase | Uso / Explicación | Ejemplo CSS | Resultado HTML |
| :--- | :--- | :--- | :--- |
| `:checked` | Selecciona inputs de tipo `radio` o `checkbox` que están marcados. | `input:checked { ... }` | `<input type="checkbox" checked>` |
| `:indeterminate` | Selecciona un input cuyo estado es indeterminado (ni marcado ni desmarcado).  | `input:indeterminate { ... }` | Un checkbox con estado intermedio vía JS |

* **Descripción**: Permiten reaccionar visualmente a las acciones del usuario. `:checked` es la más común, ideal para dar feedback inmediato. `:indeterminate` es un estado especial que generalmente se establece con JavaScript para indicar una selección parcial (por ejemplo, un checkbox "Seleccionar todo" cuando solo algunos de sus hijos están marcados).

* **Ejemplo**:

```css
/* Cuando el checkbox está marcado, la etiqueta que le sigue se pone verde y en negrita */
input[type="checkbox"]:checked + label {
  color: green;
  font-weight: bold;
}
```

```html
<input type="checkbox" id="terms" />
<label for="terms">Acepto los términos y condiciones</label>
```

* **Explicación del ejemplo**:
    * El selector `input[type="checkbox"]:checked` localiza cualquier checkbox que esté actualmente marcado por el usuario.
    * El selector de hermano adyacente `+` se usa para seleccionar la etiqueta `<label>` que viene inmediatamente después del checkbox.
    * Como resultado, el estilo solo se aplica a la etiqueta cuando su checkbox asociado está marcado, proporcionando una respuesta visual clara.

---

### 🔵 Pseudoclases de Estado en Formularios

Seleccionan elementos de formulario basándose en su estado intrínseco, como si están habilitados, deshabilitados o son de solo lectura.

| Pseudoclase | Uso / Explicación |
| :--- | :--- |
| `:enabled` | Selecciona campos de formulario que están activados (es el estado por defecto). |
| `:disabled` | Selecciona campos de formulario que están desactivados con el atributo `disabled`. |
| `:read-only` | Selecciona campos que son de solo lectura (con el atributo `readonly`). |
| `:read-write` | Selecciona campos que son editables por el usuario (el estado por defecto para la mayoría). |
| `:placeholder-shown` | Selecciona un input que está mostrando su texto de placeholder. |

* **Descripción**: Son esenciales para mostrar visualmente qué campos puede o no puede editar un usuario. La diferencia clave entre `disabled` y `readonly` es que un campo `disabled` no se envía con el formulario, mientras que un campo `readonly` sí lo hace.

* **Ejemplo**:

```css
/* Estilo para campos editables */
input:read-write {
  border: 1px solid #ccc;
}

/* Estilo para campos de solo lectura */
input:read-only {
  background-color: #f0f0f0;
  border: 1px solid #ddd;
  cursor: default;
}

/* Estilo para campos deshabilitados */
input:disabled {
  background-color: #e9e9e9;
  opacity: 0.6;
  cursor: not-allowed;
}
```

```html
<form>
  <label>Nombre (editable):</label>
  <input type="text" value="Juan" />

  <label>Email (solo lectura):</label>
  <input type="email" value="juan@ejemplo.com" readonly />

  <label>Código de socio (deshabilitado):</label>
  <input type="text" value="S-12345" disabled />
</form>
```

* **Explicación del ejemplo**:
    * `:read-write` se aplica al primer campo, ya que es el estado predeterminado de un input editable.
    * `:read-only` se aplica al segundo campo porque tiene el atributo `readonly`.
    * `:disabled` se aplica al tercer campo porque tiene el atributo `disabled`.

---

### 🟣 Pseudoclases de Validación en Formularios

Permiten aplicar estilos a los campos de un formulario en función de si los datos que contienen cumplen las reglas de validación definidas en el HTML5.

| Pseudoclase | Uso / Explicación |
| :--- | :--- |
| `:required` | Selecciona campos que tienen el atributo `required`. |
| `:optional` | Selecciona campos que no son obligatorios (el estado por defecto). |
| `:valid` | Selecciona campos cuyo contenido cumple las reglas de validación. |
| `:invalid` | Selecciona campos cuyo contenido **no** cumple las reglas de validación. |
| `:in-range` | Selecciona campos numéricos cuyo valor está dentro del rango `min` y `max`. |
| `:out-of-range` | Selecciona campos numéricos cuyo valor está fuera del rango `min` y `max`. |

* **Descripción**: Permiten dar feedback instantáneo al usuario sobre si los datos introducidos son correctos, mejorando la experiencia de usuario sin necesidad de JavaScript.

* **Ejemplo**:

```css
/* Estilo para campos inválidos */
input:invalid {
  border-color: red;
  box-shadow: 0 0 3px #ff00004d;
}

/* Estilo para campos válidos */
input:valid {
  border-color: green;
  box-shadow: 0 0 3px #0080004d;
}

/* Estilo para campos fuera de rango */
input:out-of-range {
  border-color: orange;
  background-color: #fff3e0;
}
```

```html
<form>
  <label>Email (obligatorio):</label>
  <input type="email" required />

  <label>Edad (entre 18 y 99):</label>
  <input type="number" min="18" max="99" />
</form>
```

* **Explicación del ejemplo**:
    * Al principio, el campo de email está vacío pero es `required`, por lo que se considera `:invalid` y tiene un borde rojo. Una vez se introduce un email válido (p. ej., "test@test.com"), pasa a estado `:valid` y su borde se vuelve verde.
    * El campo de edad usará `:in-range` por defecto. Si el usuario introduce un valor como "17" o "100", pasa a estado `:out-of-range` y se aplican los estilos correspondientes.

---

### 🔶 Pseudoelementos ::before y ::after

Los pseudoelementos son palabras clave que permiten dar estilo a partes de un elemento que no existen como tal en el árbol de elementos del HTML. Se distinguen por usar dos puntos dobles (`::`).

| Pseudoelemento | Uso / Explicación |
| :--- | :--- |
| `::before` | Crea un pseudoelemento que es el primer hijo del elemento seleccionado. |
| `::after` | Crea un pseudoelemento que es el último hijo del elemento seleccionado. |
| `content` | Propiedad obligatoria para `::before` y `::after` que define el contenido a insertar. |
| `attr()` | Función CSS que recupera el valor de un atributo del elemento para usarlo en la propiedad `content`. |

* **Descripción**: `::before` y `::after` son increíblemente potentes para añadir contenido decorativo (iconos, comillas, texto adicional) sin ensuciar el HTML. El contenido insertado no es parte del DOM, por lo que no puede ser seleccionado por el usuario.

* **Ejemplo**:

```css
/* Añade comillas de apertura y cierre a las citas */
blockquote::before {
  content: "“";
  font-size: 2em;
  font-weight: bold;
  color: #999;
}

blockquote::after {
  content: "”";
  font-size: 2em;
  font-weight: bold;
  color: #999;
}

/* Muestra la URL de un enlace después del texto */
a[href^="http"]::after {
  content: " (" attr(href) ")";
  font-size: 0.8em;
  color: gray;
}
```

```html
<blockquote>Un gran poder conlleva una gran responsabilidad.</blockquote>
<a href="https://developer.mozilla.org">MDN Web Docs</a>
```

* **Explicación del ejemplo**:
    * `blockquote::before` inserta una comilla de apertura justo antes del contenido del `<blockquote>`.
    * `blockquote::after` inserta una comilla de cierre justo después.
    * `a[href^="http"]::after` selecciona los enlaces que empiezan por `http`. La función `attr(href)` obtiene el valor del atributo `href` del enlace y lo inserta dentro de la propiedad `content`, mostrando la URL entre paréntesis.

---

### 🟡 Pseudoelementos Tipográficos

Estos pseudoelementos permiten aplicar estilos a fragmentos de texto específicos dentro de un elemento, como la primera letra o la primera línea.

| Pseudoelemento | Uso / Explicación |
| :--- | :--- |
| `::first-letter` | Aplica estilos a la primera letra del texto de un elemento de bloque. |
| `::first-line` | Aplica estilos a la primera línea del texto de un elemento de bloque. |

* **Descripción**: Muy utilizados en diseño editorial para crear efectos como las letras capitales (drop caps) o para destacar la primera línea de un párrafo, aportando un toque de elegancia tipográfica.

* **Ejemplo**:

```css
p.articulo::first-letter {
  font-size: 3em;
  font-weight: bold;
  float: left;
  line-height: 1;
  margin-right: 0.1em;
  color: #333;
}

p.articulo::first-line {
  font-weight: 600;
  color: #555;
}
```

```html
<p class="articulo">
  Esto es un texto de ejemplo para mostrar las ventajas de los pseudoelementos tipográficos en CSS. La primera letra será mucho más grande y la primera línea aparecerá en negrita, creando un efecto visualmente atractivo sin necesidad de etiquetas HTML adicionales.
</p>
```

* **Explicación del ejemplo**:
    * `::first-letter` selecciona la "E" inicial. Al aplicarle `float: left`, el texto fluye a su alrededor, creando una letra capital clásica.
    * `::first-line` selecciona la primera línea del párrafo. La cantidad de texto que abarca esta línea depende del ancho del contenedor y del tamaño de la fuente.

---

### 🟧 Pseudoelementos de Resaltado

Este grupo de pseudoelementos se centra en dar estilo a partes del documento que han sido resaltadas por el usuario o el navegador.

| Pseudoelemento | Uso / Explicación |
| :--- | :--- |
| `::selection` | Aplica estilos al fragmento de texto seleccionado por el usuario. |
| `::target-text` | Aplica estilos al texto resaltado cuando se navega a una URL con un fragmento de texto. |
| `::spelling-error` | Aplica estilos al texto marcado por el navegador como un error ortográfico. |
| `::grammar-error` | Aplica estilos al texto marcado por el navegador como un error gramatical. |

* **Descripción**: `::selection` es el más soportado y permite personalizar el típico fondo azul de selección de texto para que coincida con la paleta de colores de tu sitio web.

* **Ejemplo**:

```css
/* Cambia el color de fondo y de texto de la selección del usuario */
::selection {
  background-color: #ffc107; /* Un amarillo ámbar */
  color: #333; /* Texto oscuro para contraste */
}
```

* **Explicación del ejemplo**:
    * Este código no necesita HTML, ya que se aplica a cualquier texto que el usuario seleccione en la página.
    * Cuando el usuario arrastra el ratón sobre cualquier texto, el fondo de la selección será amarillo y el texto, oscuro, en lugar de los colores predeterminados del navegador.