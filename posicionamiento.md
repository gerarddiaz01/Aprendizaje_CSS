## 📝 Clase 17: Posicionamiento en CSS

Este documento introduce los conceptos fundamentales del posicionamiento de elementos en CSS, explicando cómo los navegadores renderizan los elementos HTML y las propiedades clave para controlar su disposición. Se cubren `display`, `position` (con su valor `static`), y `visibility`, además de una comparativa con `opacity` y `display: none`.

-----

### 1\. Introducción al Posicionamiento

La creación de *layouts* (diseños y maquetaciones) y la colocación de elementos en una página web es una de las partes más complejas pero fundamentales de CSS. Entender cómo se comportan los elementos es crucial para construir diseños efectivos.

**Uso / Explicación:** Cada etiqueta HTML tiene un "tipo de representación visual" o "tipo de caja" por defecto, que determina cómo se comporta en el flujo normal del documento. Históricamente, el posicionamiento ha evolucionado, y comprender estos tipos de caja es el primer paso para dominar el diseño.

#### Tipos de Caja Fundamentales

El documento destaca dos tipos de caja básicos:

  * **Elementos de Bloque (`block`):**

      * Ocupan todo el ancho disponible de su contenedor, forzando un salto de línea antes y después de ellos.
      * Pueden tener `width`, `height`, `margin`, y `padding` definidos.
      * Ejemplos: `<div>`, `<p>`, `<h1>`, `<ul>`, `<li>`.

  * **Elementos en Línea (`inline`):**

      * Ocupan solo el espacio necesario para su contenido.
      * No fuerzan un salto de línea.
      * No pueden tener `width` ni `height` definidos (su tamaño se ajusta a su contenido).
      * `margin-top` y `margin-bottom` no tienen efecto (aunque `margin-left` y `margin-right` sí). `padding-top` y `padding-bottom` añaden espacio pero no afectan la línea de base de los elementos adyacentes.
      * Ejemplos: `<span>`, `<a>`, `<strong>`, `<em>`, `<img>`.

-----

### 2\. Propiedad `display`

La propiedad `display` es una de las más importantes en CSS, ya que controla el tipo de caja de un elemento y, por ende, cómo se renderiza en la página.

**Uso / Explicación:** Permite cambiar el comportamiento por defecto de un elemento (por ejemplo, hacer que un elemento `<span>` se comporte como un `<div>`, o viceversa), lo que es fundamental para la construcción de *layouts*.

#### Valores comunes de `display`

| Valor             | Uso / Explicación                                                                                                                                                                                                                                                                 |
| :---------------- | :-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `block`           | El elemento se comporta como un bloque. Ocupa todo el ancho disponible y fuerza saltos de línea antes y después. Permite definir `width`, `height`, `margin` y `padding` en todas las direcciones.                                                                                 |
| `inline`          | El elemento se comporta como en línea. Ocupa solo el ancho necesario para su contenido. No fuerza saltos de línea. No respeta `width` ni `height`, y solo afecta `margin` y `padding` horizontales.                                                                                   |
| `inline-block`    | Combina características de `inline` y `block`. Se coloca en línea con otros elementos, pero permite definir `width`, `height`, y `margin`/`padding` en todas las direcciones. Muy útil para elementos que deben fluir con el texto pero tener dimensiones y márgenes controlados. |
| `none`            | Oculta completamente el elemento de la página. El elemento no se renderiza, no ocupa espacio, y es como si no existiera en el árbol de renderizado del documento. Esto afecta el flujo del documento.                                                                             |
| `flex`, `grid`    | Valores para activar los modelos de caja Flexbox y Grid, respectivamente, que son sistemas de layout más avanzados para organizar colecciones de elementos. (Se verán en clases posteriores).                                                                                 |

**Sintaxis:** `display: block;` o `display: inline-block;`

#### Ejemplos de `display`

```html
<p>Este es un párrafo de texto con un <span class="inline-to-block">span que es block</span> y otro <span class="inline-normal">span normal</span>.</p>

<div>Normal Block Div</div>
<span class="block-to-inline">Normal Inline Span convertido a inline</span>
```

```css
/* Un span que se comporta como un bloque */
.inline-to-block {
  display: block;
  width: 150px;
  height: 30px;
  background-color: lightblue;
  margin: 5px;
  color: white;
}

/* Un span normal para comparar */
.inline-normal {
  background-color: lightgreen;
  padding: 2px 5px;
}

/* Un div que se comporta como en línea (no fuerza salto de línea) */
.block-to-inline {
  display: inline; /* O inline-block si queremos controlar width/height */
  background-color: lightcoral;
  padding: 5px;
  border: 1px solid red;
  /* width, height, margin-top/bottom no tendrían efecto si es 'inline' puro */
}

div {
  background-color: #f0f0f0;
  padding: 10px;
  margin-bottom: 10px;
  border: 1px dashed #ccc;
}
```

-----

Tienes toda la razón. Mis disculpas por la omisión. El PDF "CSS-Clase-17-Posicionamiento-I.pdf" sí cubre el posicionamiento `relative`, `absolute`, `fixed` y `sticky` en sus páginas posteriores a la introducción. Me enfoqué demasiado en las primeras secciones y el valor `static`.

Aquí tienes el punto 3 actualizado de tu resumen, incluyendo `position: relative;`, `position: absolute;`, `position: fixed;` y `position: sticky;`, con explicaciones detalladas y ejemplos de código para cada uno.

-----

### 3\. Propiedad `position` (Tipos de Posicionamiento)

La propiedad `position` es el fundamento del sistema de posicionamiento en CSS, permitiendo controlar la ubicación precisa de un elemento fuera del flujo normal del documento. Cuando un elemento tiene un valor de `position` diferente de `static` (el valor por defecto), las propiedades `top`, `bottom`, `left`, `right` y `z-index` pasan a tener efecto.

#### `position: static;`

  * **Uso / Explicación:** Este es el valor por defecto de la propiedad `position` para todos los elementos HTML. Un elemento con `position: static;` se renderiza en el flujo normal del documento (es decir, en el orden en que aparece en el HTML).
  * **Comportamiento:**
      * Las propiedades `top`, `bottom`, `left`, `right` y `z-index` **no tienen ningún efecto** sobre un elemento con `position: static;`. Su posición está determinada únicamente por el flujo normal del documento y por las propiedades del modelo de cajas (`margin`, `padding`, `border`).
      * Es el punto de referencia para el posicionamiento `relative`.

**Sintaxis:** `position: static;` (raramente se declara explícitamente, ya que es el valor predeterminado).

#### Ejemplo de `position: static;`

```html
<div class="box static-box">Caja Estática 1</div>
<div class="box static-box">Caja Estática 2</div>
<div class="box static-box">Caja Estática 3</div>
```

```css
.box {
  width: 100px;
  height: 100px;
  background-color: lightblue;
  border: 1px solid blue;
  margin: 10px; /* Margen para separación */
  text-align: center;
  line-height: 100px;
  font-weight: bold;
}

.static-box {
  position: static; /* Esto no cambiará el comportamiento por defecto */
  /* top, bottom, left, right no tendrían efecto aquí */
}
```

#### `position: relative;`

  * **Uso / Explicación:** Posiciona un elemento en relación con su posición *normal* en el flujo del documento. Mueve el elemento de su posición original, pero **sigue ocupando el espacio** en el layout donde estaría si fuera `static`.
  * **Comportamiento:**
      * Las propiedades `top`, `bottom`, `left`, `right` desplazan el elemento desde su posición original.
      * Otros elementos en el documento **no se ven afectados** por este desplazamiento; actúan como si el elemento `relative` aún estuviera en su lugar original. Esto puede causar que se superponga con otros elementos o deje espacios vacíos visualmente.
      * Crea un **contexto de apilamiento** y un **contexto de posicionamiento** para sus hijos posicionados `absolute` o `fixed`. Esto significa que los elementos `absolute` dentro de un padre `relative` se posicionarán en relación con ese padre.

**Sintaxis:** `position: relative;` y luego `top: 10px;`, `left: 20px;` etc.

#### Ejemplo de `position: relative;`

```html
<div class="parent-relative-example">
  <div class="box relative-box">Caja Relative</div>
  <div class="box static-sibling">Caja Estática</div>
</div>
```

```css
.parent-relative-example {
  border: 2px dashed #ccc;
  padding: 20px;
  margin-bottom: 50px; /* Para espacio */
  background-color: #f9f9f9;
}

.box {
  width: 100px;
  height: 100px;
  background-color: lightblue;
  border: 1px solid blue;
  margin: 10px;
  text-align: center;
  line-height: 100px;
  font-weight: bold;
}

.relative-box {
  position: relative;
  top: 20px;   /* Se mueve 20px hacia abajo desde su posición original */
  left: 30px;  /* Se mueve 30px a la derecha desde su posición original */
  background-color: dodgerblue;
  color: white;
}

.static-sibling {
  /* Se renderiza como si 'relative-box' no se hubiera movido,
     potencialmente superponiéndose */
  background-color: lightgreen;
}
```

-----

#### `position: absolute;`

  * **Uso / Explicación:** Posiciona un elemento en relación con el ancestro posicionado más cercano (es decir, el ancestro cuya propiedad `position` no es `static`). Si no encuentra ningún ancestro posicionado, se posiciona en relación con el `<body>` del documento.
  * **Comportamiento:**
      * Un elemento con `position: absolute;` es **eliminado del flujo normal del documento**. No ocupa espacio y otros elementos se comportan como si no existiera.
      * Las propiedades `top`, `bottom`, `left`, `right` posicionan el elemento en relación con su contenedor posicionado.
      * Es ideal para elementos superpuestos, ventanas emergentes, tooltips, o cualquier elemento que deba colocarse con precisión sin afectar el layout general.

**Sintaxis:** `position: absolute;` y luego `top: 0;`, `left: 0;` etc.

#### Ejemplo de `position: absolute;`

```html
<div class="parent-absolute-example">
  <div class="box absolute-child">Caja Absoluta</div>
  <div class="box static-sibling-absolute">Otra Caja (estática)</div>
</div>
<div class="box sibling-after-absolute">Caja Hermana (después del padre)</div>
```

```css
.parent-absolute-example {
  position: relative; /* CRUCIAL: Esto convierte a este div en el contenedor de posicionamiento para 'absolute-child' */
  width: 300px;
  height: 200px;
  border: 2px dashed red;
  padding: 10px;
  margin: 20px;
  background-color: #ffe0e0;
}

.absolute-child {
  position: absolute;
  top: 10px;
  right: 10px;
  background-color: darkred;
  color: white;
  width: 80px; /* Ancho y alto para la caja absoluta */
  height: 80px;
  line-height: 80px;
  margin: 0; /* Los márgenes no suelen ser útiles con absolute */
}

.static-sibling-absolute {
  /* Este div se posiciona como si 'absolute-child' no existiera */
  background-color: lightgoldenrodyellow;
  margin-top: 100px; /* Para mostrar que el espacio no se respeta */
}

.sibling-after-absolute {
  background-color: lightgray;
  margin-top: 20px;
}
```

-----

#### `position: fixed;`

  * **Uso / Explicación:** Posiciona un elemento en relación con la **ventana del navegador (viewport)**. Esto significa que el elemento permanecerá en la misma posición en la pantalla, incluso cuando el usuario se desplaza.
  * **Comportamiento:**
      * Es **eliminado del flujo normal del documento**, no ocupa espacio.
      * Las propiedades `top`, `bottom`, `left`, `right` posicionan el elemento en relación con los bordes del viewport.
      * Ideal para encabezados o pies de página que siempre son visibles, botones de "volver arriba", o barras de navegación flotantes.
      * Un elemento `fixed` no crea un contexto de posicionamiento para sus hijos como lo haría un elemento `relative`.

**Sintaxis:** `position: fixed;` y luego `top: 0;`, `left: 0;` etc.

#### Ejemplo de `position: fixed;`

```html
<div class="fixed-header">
  Cabecera Fija
</div>
<p style="height: 1000px;">Contenido de la página para forzar el desplazamiento...</p>
<p>Más contenido para asegurar el desplazamiento...</p>
```

```css
body {
  margin: 0; /* Elimina el margen por defecto del body para que el fixed quede pegado */
  padding-top: 50px; /* Espacio para que el contenido no quede debajo del fixed header */
}

.fixed-header {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 50px;
  background-color: #333;
  color: white;
  text-align: center;
  line-height: 50px;
  font-weight: bold;
  z-index: 1000; /* Asegura que esté por encima de otros elementos */
  box-shadow: 0 2px 5px rgba(0,0,0,0.2);
}

p {
  padding: 10px 20px;
  margin-bottom: 10px;
}
```

-----

#### `float`

  * [cite\_start]**Uso / Explicación:** La propiedad `float` se utilizaba tradicionalmente para envolver texto alrededor de imágenes, pero también se ha usado para crear diseños de columnas simples[cite: 118]. [cite\_start]Mueve un elemento a la izquierda o derecha de su contenedor, permitiendo que el texto y los elementos en línea fluyan alrededor de él[cite: 119].
  * **Comportamiento:**
      * Un elemento flotante es sacado del flujo normal del documento, pero aún afecta el layout de los elementos no flotantes que lo rodean.
      * El elemento "flotará" tan a la izquierda o a la derecha como sea posible dentro de su contenedor.
      * [cite\_start]Es importante usar `clear` para evitar que los elementos siguientes floten junto a él cuando no se desea[cite: 120].

**Sintaxis:** `float: left;` o `float: right;`. También `float: none;` (por defecto) e `float: inherit;`.

#### Ejemplo de `float`

```html
<div class="container-float">
  <img src="https://via.placeholder.com/100" alt="Imagen flotante" class="float-image">
  <p>Este es un párrafo de texto que fluirá alrededor de la imagen flotante. El texto continuará ajustándose al espacio disponible junto a la imagen. Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.</p>
  <div class="clear"></div> <p>Este párrafo está debajo de la imagen flotante gracias al "clear".</p>
</div>
```

```css
.container-float {
  border: 1px solid #ddd;
  padding: 10px;
  margin-bottom: 20px;
}

.float-image {
  float: left; /* La imagen flota a la izquierda */
  margin-right: 15px; /* Espacio a la derecha de la imagen */
  margin-bottom: 10px;
}

.clear {
  clear: both; /* Limpia los floats tanto a la izquierda como a la derecha */
}
```

-----


#### `position: sticky;`

  * **Uso / Explicación:** Es una combinación de `relative` y `fixed`. Un elemento `sticky` se comporta como `relative` hasta que alcanza un determinado umbral de desplazamiento en el viewport, momento en el que se "pega" (se comporta como `fixed`) hasta que su contenedor padre deja la pantalla.
  * **Comportamiento:**
      * Inicialmente se comporta como `position: static;` (dentro del flujo del documento).
      * Cuando el usuario se desplaza y el elemento (o su borde) alcanza la posición definida por `top`, `bottom`, `left`, `right`, se vuelve "pegajoso" (sticky) y se comporta como `fixed` en relación con el viewport.
      * Cuando el elemento padre sale de la pantalla, el elemento `sticky` también desaparece. Esto lo diferencia de `fixed`, que siempre está en el viewport.
      * Requiere un contenedor padre con desplazamiento (scroll) y que el elemento `sticky` no tenga un `overflow: hidden;` en el padre.

**Sintaxis:** `position: sticky;` y luego al menos una propiedad de offset (`top`, `bottom`, `left`, `right`).

#### Ejemplo de `position: sticky;`

```html
<div class="sticky-container">
  <h2>Sección 1</h2>
  <div class="sticky-element">
    Elemento Sticky (Header de sección)
  </div>
  <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. ... (mucho texto)</p>
  <p>Más contenido para rellenar la sección.</p>
  <p style="height: 300px;"></p> <p>Fin de Sección 1.</p>
</div>

<div class="sticky-container">
  <h2>Sección 2</h2>
  <div class="sticky-element">
    Otro Elemento Sticky
  </div>
  <p>Contenido de la segunda sección...</p>
  <p style="height: 300px;"></p>
  <p>Fin de Sección 2.</p>
</div>
```

```css
body {
  margin: 0;
  font-family: sans-serif;
}

.sticky-container {
  border: 2px solid #ccc;
  padding: 10px;
  margin: 20px;
  height: 500px; /* Un contenedor con altura para que el sticky funcione dentro de él */
  overflow-y: auto; /* IMPORTANTE: Opcional, pero si el padre es scrollable, 'sticky' funciona dentro de él. Si no, se pegará al viewport cuando se haga scroll en el body */
}

h2 {
  padding: 5px;
  background-color: #f0f0f0;
  margin-top: 0;
}

.sticky-element {
  position: sticky;
  top: 0; /* Se pegará a 0px del top del viewport (o del contenedor con scroll si lo tiene) */
  background-color: #4CAF50;
  color: white;
  padding: 10px;
  text-align: center;
  font-weight: bold;
  border-bottom: 2px solid darkgreen;
  z-index: 10; /* Para que quede por encima del contenido */
}

p {
  margin-top: 15px;
  line-height: 1.6;
}
```

---

### 4\. Propiedad `visibility`

La propiedad `visibility` permite hacer invisible un elemento sin que pierda su espacio en el *layout* del documento.

**Uso / Explicación:** A diferencia de `display: none;`, que elimina el elemento del flujo del documento, `visibility: hidden;` simplemente oculta el elemento visualmente, pero su "caja" sigue ocupando espacio en la página. Esto significa que los elementos circundantes no se moverán para ocupar su lugar.

  * **Valores comunes:**
      * `visible` (por defecto): El elemento es visible.
      * `hidden`: El elemento es invisible, pero sigue ocupando su espacio en el *layout*.
      * `collapse`: Similar a `hidden`, pero su comportamiento exacto puede variar (especialmente en tablas, donde puede colapsar filas/columnas como si no existieran).

**Sintaxis:** `visibility: hidden;` o `visibility: visible;`

#### Ejemplos de `visibility`

```html
<div class="visible-box">Caja Visible</div>
<div class="hidden-box">Caja Oculta (ocupa espacio)</div>
<div class="another-visible-box">Otra Caja Visible</div>
```

```css
.base-visibility-box {
  width: 120px;
  height: 60px;
  border: 1px solid #333;
  margin: 10px;
  background-color: #f0f0f0;
  text-align: center;
  line-height: 60px;
}

.visible-box {
  @extend .base-visibility-box;
  visibility: visible; /* Por defecto */
  background-color: lightgreen;
}

.hidden-box {
  @extend .base-visibility-box;
  visibility: hidden; /* Oculta, pero reserva el espacio */
  background-color: lightcoral; /* El color de fondo no se verá */
}

.another-visible-box {
  @extend .base-visibility-box;
  visibility: visible;
  background-color: lightblue;
}
```

-----

### 5\. Comparativa: `display: none;` vs `opacity: 0;` vs `visibility: hidden;`

Existen varias formas de "ocultar" un elemento en CSS, pero cada una tiene un efecto diferente en el *layout* y la interacción. Es crucial entender estas diferencias para elegir la propiedad adecuada.

| Propiedad          | Efecto en la Visibilidad | Efecto en el Espacio (`layout`) | Accesibilidad (Lectores de pantalla) | Interactividad (Clics, eventos) |
| :------------------ | :----------------------- | :------------------------------ | :----------------------------------- | :------------------------------ |
| `display: none;`    | Totalmente invisible     | **No ocupa espacio** | **No es leído** | No interactivo                  |
| `visibility: hidden;` | Totalmente invisible     | **Ocupa espacio** | Generalmente **no es leído** | No interactivo                  |
| `opacity: 0;`       | Totalmente invisible     | **Ocupa espacio** | **Sí es leído** | **Sí es interactivo** |

**Uso de la comparativa:**

  * **`display: none;`:** Útil para ocultar elementos que no deben ser parte del *layout* o ser accesibles en absoluto (ej. menús desplegables que solo se muestran con JavaScript).
  * **`visibility: hidden;`:** Ideal para ocultar elementos que quieres que mantengan su lugar en el *layout* (ej. un espacio reservado para una animación que aparecerá después, o un elemento que desaparecerá pero no quieres que el contenido de abajo se mueva).
  * **`opacity: 0;`:** Perfecta para animaciones de desvanecimiento o para elementos que deben ser interactivos (recibir clics) incluso cuando son invisibles. También se usa para elementos que deben ser accesibles por lectores de pantalla incluso cuando no son visibles visualmente.

#### Ejemplos de Comparativa

```html
<button class="btn-display-none">Botón Display None</button>
<button class="btn-visibility-hidden">Botón Visibility Hidden</button>
<button class="btn-opacity-zero">Botón Opacity Zero</button>
<button class="btn-normal">Botón Normal</button>
```

```css
button {
  padding: 10px 20px;
  margin: 10px;
  border: 1px solid gray;
  background-color: #eee;
  cursor: pointer;
}

.btn-display-none {
  display: none; /* Desaparece completamente, los otros botones se moverán a su lugar */
}

.btn-visibility-hidden {
  visibility: hidden; /* Invisible, pero el espacio del botón se mantiene */
}

.btn-opacity-zero {
  opacity: 0; /* Invisible, pero el espacio del botón se mantiene Y ES CLICABLE */
}

.btn-normal {
  background-color: lightblue;
}
```

-----

#### `z-index` (Apilamiento)

  * **Uso / Explicación:** Cuando se modifica la posición de las cajas, puede ocurrir apilamiento entre los diferentes elementos. La propiedad `z-index` establece el nivel de profundidad en el que está un elemento sobre los demás. Permite que un elemento se coloque encima o debajo de otro.
  * **Comportamiento:**
      * Se le asigna un número que representa el nivel de profundidad del elemento. Los elementos con un número más alto estarán por encima de otros con un número más bajo.
      * `z-index` **solo funciona en elementos posicionados** (es decir, aquellos con `position` diferente de `static`: `relative`, `absolute`, `fixed`, o `sticky`). No tiene efecto en elementos con posicionamiento estático.

**Sintaxis:** `z-index: 1;` (puede ser cualquier número entero, positivo o negativo). Un número más alto significa más "arriba".

#### Ejemplo de `z-index`

```html
<div class="container-z-index">
  <div class="box z-index-back">Fondo (z-index: 1)</div>
  <div class="box z-index-front">Frente (z-index: 2)</div>
</div>
```

```css
.container-z-index {
  position: relative; /* Contenedor para los elementos posicionados */
  width: 300px;
  height: 150px;
  border: 2px solid purple;
  margin-top: 50px;
  background-color: #f5f5f5;
}

.box {
  width: 150px;
  height: 100px;
  position: absolute; /* Para que z-index tenga efecto */
  text-align: center;
  line-height: 100px;
  font-weight: bold;
  color: white;
  border: 1px solid black;
}

.z-index-back {
  background-color: #FF5733; /* Naranja */
  top: 20px;
  left: 20px;
  z-index: 1; /* Menor z-index */
}

.z-index-front {
  background-color: #33C7FF; /* Azul */
  top: 40px;
  left: 60px;
  z-index: 2; /* Mayor z-index, estará encima */
}
```

-----

