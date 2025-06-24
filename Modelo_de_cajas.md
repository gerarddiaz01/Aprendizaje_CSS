## 📝 Clase 14: El Modelo de Cajas en CSS - Un Resumen Visual

Este documento explica en detalle el Modelo de Cajas de CSS, un concepto fundamental para entender cómo los elementos HTML son renderizados y cómo se relacionan entre sí en una página web. Se cubren las propiedades `width`, `height`, `margin`, `padding`, `border`, `box-sizing`, `opacity` y `overflow`.

---

### 1\. ¿Qué es el Modelo de Cajas?

El Modelo de Cajas de CSS es un sistema que utiliza el navegador para interpretar y representar visualmente los elementos HTML en la pantalla. Cada elemento HTML se renderiza como una caja rectangular, y comprender las partes que componen esta caja es esencial para el diseño y la alineación en CSS.

**Uso / Explicación:** Todo en CSS tiene una caja alrededor. Incluso elementos que parecen no tener bordes visibles o fondo, siguen siendo tratados como cajas por el navegador. Entender cómo se calculan las dimensiones de estas cajas y cómo interactúan entre sí (a través de márgenes, rellenos y bordes) es la clave para crear diseños web precisos y responsivos.

**Conceptos clave de la "caja":**

- **Contenido (Content):** El área donde se muestra el contenido real del elemento (texto, imágenes, videos, etc.).
- **Relleno (Padding):** Espacio transparente que rodea el contenido, dentro del borde. Aumenta el tamaño visual de la caja pero no el del contenido en sí.
- **Borde (Border):** Una línea que rodea el padding y el contenido.
- **Margen (Margin):** Espacio transparente que rodea el borde de la caja, separándola de otros elementos adyacentes.

---

### 2\. Dimensiones: `width` y `height`

Las propiedades `width` y `height` controlan las dimensiones del área de contenido de un elemento.

#### `width`

**Uso / Explicación:** La propiedad `width` establece el ancho del área de contenido de un elemento.

- **Valores comunes:**
  - **`auto` (por defecto):** El navegador calcula automáticamente el ancho del elemento. Para elementos de bloque, esto generalmente significa que ocupan el 100% del ancho disponible de su contenedor.
  - **Longitudes (`px`, `em`, `rem`, `vw`, `vh`, etc.):** Un valor fijo en píxeles, o un valor relativo a la fuente, al viewport, etc.
  - **Porcentajes (`%`):** Un porcentaje del ancho del elemento padre.

**Sintaxis:** `width: 200px;`, `width: 50%;`, `width: auto;`

#### `height`

**Uso / Explicación:** La propiedad `height` establece la altura del área de contenido de un elemento.

- **Valores comunes:**
  - **`auto` (por defecto):** La altura del elemento se ajusta automáticamente al tamaño de su contenido.
  - **Longitudes (`px`, `em`, `rem`, `vh`, `vw`, etc.):** Un valor fijo en píxeles, o un valor relativo a la fuente, al viewport, etc.
  - **Porcentajes (`%`):** Un porcentaje de la altura del elemento padre. Para que los porcentajes funcionen correctamente en `height`, el elemento padre debe tener una altura explícitamente definida.

**Sintaxis:** `height: 150px;`, `height: 100%;`, `height: auto;`

#### Ejemplos de `width` y `height`

```html
<div class="box-width">Contenido con ancho fijo.</div>
<div class="box-height">Contenido con altura fija.</div>
<div class="box-responsive">Contenido con ancho relativo.</div>
<div class="box-auto">
  Contenido con ancho y alto automáticos. Este texto se ajustará dentro.
</div>
```

```css
/* Ancho fijo en píxeles */
.box-width {
  width: 300px;
  border: 1px solid blue;
  margin-bottom: 10px;
}

/* Altura fija en píxeles */
.box-height {
  height: 100px;
  border: 1px solid green;
  overflow: auto; /* Para ver cómo se maneja el contenido si desborda */
  margin-bottom: 10px;
}

/* Ancho responsivo (50% del contenedor padre) */
.box-responsive {
  width: 50%;
  border: 1px solid red;
  margin-bottom: 10px;
}

/* Ancho y alto automáticos (por defecto para elementos de bloque, se ajusta al contenido) */
.box-auto {
  width: auto; /* Ocupará el 100% disponible */
  height: auto; /* Se ajustará al contenido */
  border: 1px solid purple;
  margin-bottom: 10px;
}
```

---

### 3\. Espaciado y Líneas: `margin`, `padding` y `border`

Estas propiedades controlan los espacios entre el contenido y el borde (`padding`), la línea del borde en sí (`border`), y el espacio entre el borde de un elemento y otros elementos (`margin`).

#### `margin`

**Uso / Explicación:** La propiedad `margin` crea espacio transparente alrededor del exterior de un elemento, separándolo de otros elementos adyacentes. Los márgenes no son parte del elemento en sí y no se ven afectados por el color de fondo del elemento.

- **Valores comunes:**
  - **Longitudes (`px`, `em`, `rem`, etc.):** Un valor fijo.
  - **Porcentajes (`%`):** Un porcentaje del ancho del _elemento padre_.
  - **`auto`:** Usado comúnmente con elementos de bloque para centrar horizontalmente (ej. `margin: 0 auto;`).
- **Propiedades individuales:** `margin-top`, `margin-right`, `margin-bottom`, `margin-left`.
- **Shorthand:** Puedes especificar todos los márgenes en una sola declaración:
  - `margin: 20px;` (todos los lados)
  - `margin: 10px 20px;` (arriba/abajo, izquierda/derecha)
  - `margin: 5px 10px 15px;` (arriba, izquierda/derecha, abajo)
  - `margin: 1px 2px 3px 4px;` (arriba, derecha, abajo, izquierda - sentido horario)

**Sintaxis:** `margin: 10px;`, `margin: 20px 0;`

#### `padding`

**Uso / Explicación:** La propiedad `padding` crea espacio transparente entre el contenido de un elemento y su borde. A diferencia del margen, el `padding` forma parte del elemento y toma el color de fondo del elemento.

- **Valores comunes:**
  - **Longitudes (`px`, `em`, `rem`, etc.):** Un valor fijo.
  - **Porcentajes (`%`):** Un porcentaje del ancho del _elemento padre_.
- **Propiedades individuales:** `padding-top`, `padding-right`, `padding-bottom`, `padding-left`.
- **Shorthand:** Se usa igual que `margin` para especificar los rellenos en una sola declaración:
  - `padding: 15px;` (todos los lados)
  - `padding: 10px 20px;` (arriba/abajo, izquierda/derecha)
  - `padding: 5px 10px 15px 20px;` (arriba, derecha, abajo, izquierda - sentido horario)

**Sintaxis:** `padding: 15px;`, `padding: 10px 20px;`

#### `border`

**Uso / Explicación:** La propiedad `border` dibuja una línea alrededor del `padding` y el contenido de un elemento. Se puede especificar el ancho, el estilo y el color del borde.

- **Propiedades individuales:**
  - **`border-width`:** Define el grosor del borde (ej. `2px`, `medium`, `thick`).
  - **`border-style`:** Define el estilo de la línea (ej. `solid`, `dotted`, `dashed`, `double`, `groove`, `ridge`, `inset`, `outset`, `none`, `hidden`). **Sin un `border-style`, el borde no será visible.**
  - **`border-color`:** Define el color del borde.
- **Shorthand:** La forma más común de definir un borde es utilizando la propiedad abreviada `border`, que combina ancho, estilo y color.

**Sintaxis:** `border: 1px solid black;` (ancho, estilo, color)

#### Ejemplos de `margin`, `padding` y `border`

```html
<div class="box-model-example">Contenido de la caja</div>
<div class="another-box">Otra caja</div>
```

```css
.box-model-example {
  width: 200px;
  height: 100px;
  background-color: lightblue;
  /* Relleno: 20px en todos los lados */
  padding: 20px;
  /* Borde: 5px sólido de color rojo */
  border: 5px solid red;
  /* Margen: 30px en todos los lados */
  margin: 30px;
}

.another-box {
  width: 180px;
  height: 80px;
  background-color: lightgreen;
  padding: 15px;
  border: 3px dashed purple;
  margin-top: 50px; /* Sólo margen superior */
  margin-left: auto; /* Centrar horizontalmente si el contenedor lo permite */
  margin-right: auto;
}
```

---

### 4\. Control Avanzado del Modelo de Cajas: `box-sizing`, `opacity` y `overflow`

Estas propiedades ofrecen un control más fino sobre cómo se calculan las dimensiones de las cajas, su visibilidad y cómo se maneja el contenido que desborda.

#### `box-sizing`

**Uso / Explicación:** La propiedad `box-sizing` define cómo se calcula el ancho y la altura total de un elemento. Por defecto, CSS calcula el `width` y `height` de un elemento basándose solo en el área de contenido (`content-box`). Esto significa que el `padding` y el `border` se _añaden_ al ancho y alto especificados, haciendo que la caja total sea más grande de lo esperado. `box-sizing` permite cambiar este comportamiento.

- **Valores comunes:**
  - **`content-box` (por defecto):** El `width` y `height` se refieren solo al contenido. `padding` y `border` se añaden a estas dimensiones.
    - Ancho Total = `width` + `padding-left` + `padding-right` + `border-left-width` + `border-right-width`
    - Altura Total = `height` + `padding-top` + `padding-bottom` + `border-top-width` + `border-bottom-width`
  - **`border-box`:** El `width` y `height` incluyen el `padding` y el `border`. Esto hace que el tamaño de los elementos sea más intuitivo y predecible, ya que el tamaño total del elemento es exactamente el `width` y `height` especificados.
    - Ancho Total = `width` (incluye padding y border)
    - Altura Total = `height` (incluye padding y border)

**Sintaxis:** `box-sizing: border-box;`

#### Ejemplos de `box-sizing`

```html
<div class="box-content-box">Caja con content-box</div>
<div class="box-border-box">Caja con border-box</div>
```

```css
/* Ejemplo con content-box (comportamiento por defecto) */
.box-content-box {
  width: 200px;
  height: 100px;
  padding: 20px;
  border: 5px solid blue;
  background-color: lightblue;
  box-sizing: content-box; /* Explícitamente definido, aunque es el valor por defecto */
  margin-bottom: 20px;
  /* El ancho total real será 200px (contenido) + 2*20px (padding) + 2*5px (border) = 250px */
  /* La altura total real será 100px (contenido) + 2*20px (padding) + 2*5px (border) = 150px */
}

/* Ejemplo con border-box (más fácil de trabajar para el diseño) */
.box-border-box {
  width: 200px;
  height: 100px;
  padding: 20px;
  border: 5px solid red;
  background-color: lightcoral;
  box-sizing: border-box; /* El padding y el borde se "comen" el espacio del width/height */
  /* El ancho total real será 200px */
  /* La altura total real será 100px */
}
```

**Recomendación:** Es una práctica común y altamente recomendada aplicar `box-sizing: border-box;` a todos los elementos del CSS para facilitar el diseño y evitar problemas de cálculo de tamaños:

```css
html {
  box-sizing: border-box;
}
*,
*::before,
*::after {
  box-sizing: inherit;
}
```

#### `opacity`

**Uso / Explicación:** La propiedad `opacity` especifica la transparencia de un elemento. Un valor de `1` (o `1.0`) significa totalmente opaco (visible), y un valor de `0` (o `0.0`) significa totalmente transparente (invisible). Los valores intermedios (ej. `0.5`) hacen que el elemento sea semitransparente.

- **Valores:** Un número entre `0` y `1`.

**Sintaxis:** `opacity: 0.5;`, `opacity: 1;`

#### Ejemplos de `opacity`

```html
<div class="box-opacity-full">Totalmente visible (opacity: 1)</div>
<div class="box-opacity-half">Semitransparente (opacity: 0.5)</div>
<div class="box-opacity-none">Invisible (opacity: 0)</div>
```

```css
.box-opacity-full {
  width: 200px;
  height: 50px;
  background-color: dodgerblue;
  margin-bottom: 10px;
  opacity: 1; /* Valor por defecto */
  color: white;
  text-align: center;
  line-height: 50px;
}

.box-opacity-half {
  width: 200px;
  height: 50px;
  background-color: dodgerblue;
  margin-bottom: 10px;
  opacity: 0.5; /* 50% de transparencia */
  color: white;
  text-align: center;
  line-height: 50px;
}

.box-opacity-none {
  width: 200px;
  height: 50px;
  background-color: dodgerblue;
  margin-bottom: 10px;
  opacity: 0; /* Totalmente transparente, pero sigue ocupando espacio */
  color: white;
  text-align: center;
  line-height: 50px;
}
```

#### `overflow`

**Uso / Explicación:** La propiedad `overflow` controla lo que sucede con el contenido de un elemento cuando es demasiado grande para caber en su área.

- **Valores comunes:**
  - **`visible` (por defecto):** El contenido que desborda simplemente se muestra fuera de la caja, sin ser recortado.
  - **`hidden`:** El contenido que desborda es recortado y no visible.
  - **`scroll`:** Se añaden barras de desplazamiento (scrollbars) al elemento para que el usuario pueda ver el contenido desbordado, incluso si no es necesario en una de las direcciones.
  - **`auto`:** Las barras de desplazamiento solo se añaden si son necesarias (si el contenido desborda en esa dirección). Esta es generalmente la opción más flexible y recomendada.

**Sintaxis:** `overflow: hidden;`, `overflow: scroll;`, `overflow: auto;`

#### Ejemplos de `overflow`

```html
<div class="box-overflow-visible">
  Este es un contenido muy largo que probablemente desbordará la caja si tiene
  un ancho o alto fijo. Aquí hay más texto para asegurarnos de que exceda los
  límites de la caja.
</div>

<div class="box-overflow-hidden">
  Este contenido se recortará si es demasiado largo para la caja. No verás lo
  que desborda.
</div>

<div class="box-overflow-scroll">
  Este contenido tendrá barras de desplazamiento para ver todo, incluso si no es
  necesario en ambas direcciones.
</div>

<div class="box-overflow-auto">
  Este contenido tendrá barras de desplazamiento solo si son necesarias para ver
  todo el texto. Es la opción más flexible para la mayoría de los casos.
</div>
```

```css
.fixed-size-box {
  width: 200px;
  height: 100px;
  border: 1px solid black;
  margin-bottom: 15px;
  padding: 10px;
  background-color: #f0f0f0;
}

.box-overflow-visible {
  @extend .fixed-size-box; /* O copiar las propiedades base */
  overflow: visible; /* El texto desborda la caja */
}

.box-overflow-hidden {
  @extend .fixed-size-box;
  overflow: hidden; /* El texto que desborda se recorta */
}

.box-overflow-scroll {
  @extend .fixed-size-box;
  overflow: scroll; /* Siempre muestra barras de desplazamiento */
}

.box-overflow-auto {
  @extend .fixed-size-box;
  overflow: auto; /* Muestra barras de desplazamiento solo si el contenido desborda */
}
```

---

He analizado el PDF "CSS-Clase-14.1-Ejercicios-de-modelo-de-caja.pdf". Este PDF, a diferencia de los anteriores, se centra casi exclusivamente en la **práctica y demostración de ejercicios visuales** relacionados con el modelo de cajas, `width`, `height`, `margin`, `padding` y `border`.

Dado que el contenido son principalmente imágenes de resultados esperados de ejercicios y descripciones breves de los mismos (que ya fueron cubiertas en el resumen de la Clase 14), **no hay nueva información teórica que resumir en este documento**. Las propiedades y conceptos ya fueron explicados en el resumen de la Clase 14 (Modelo de Cajas).

Sin embargo, puedo ofrecerte un documento que **recapitule los objetivos de cada ejercicio y las propiedades CSS clave** que se deberían aplicar para lograrlos, siguiendo la estructura de prosa y ejemplos de código que te ha gustado, pero enfocado en la aplicación práctica.

Por favor, confirma si esto sería lo que buscas, ya que un resumen "teórico" de este PDF en particular no aportaría valor adicional a lo ya cubierto. Si el objetivo es solo listar los ejercicios y las propiedades implicadas, puedo hacerlo.

---

**Resumen Propuesto (Enfoque en Ejercicios):**

## 📝 Clase 14.1: Ejercicios de Modelo de Cajas - Aplicación Práctica

Este documento detalla los ejercicios propuestos en la Clase 14.1, enfocándose en las propiedades CSS del Modelo de Cajas que se aplican en cada uno para lograr los resultados visuales deseados. Se asume un conocimiento previo de las propiedades `width`, `height`, `margin`, `padding`, `border`, `background-color` y `color`.

---

### 1\. Ejercicio 1: Width y Height (Dimensiones Básicas)

Este ejercicio se centra en la aplicación directa de las propiedades `width` y `height` para definir las dimensiones de las cajas, combinadas con `border`, `padding`, `margin` y `background-color`.

**Objetivo:** Crear dos cajas con dimensiones, bordes, rellenos, márgenes y colores de fondo específicos.

#### Caja 1: `250x200px` con bordes, relleno y margen.

- **Propiedades clave a aplicar:**
  - `width`: `250px`
  - `height`: `200px`
  - `border`: `5px solid red;`
  - `background-color`: `lightgray;` (o un gris claro similar)
  - `padding`: `10px;`
  - `margin`: `25px;`

**Fragmento CSS esperable:**

```css
.caja-ejercicio-1a {
  width: 250px;
  height: 200px;
  border: 5px solid red;
  background-color: lightgray; /* O #D3D3D3 */
  padding: 10px;
  margin: 25px;
}
```

#### Caja 2: `300x200px` con bordes, fondo gris, texto blanco, relleno y margen.

- **Propiedades clave a aplicar:**
  - `width`: `300px`
  - `height`: `200px`
  - `border`: `7px solid green;`
  - `background-color`: `gray;` (o un gris similar)
  - `color`: `white;`
  - `padding`: `5px;`
  - `margin`: `0;`

**Fragmento CSS esperable:**

```css
.caja-ejercicio-1b {
  width: 300px;
  height: 200px;
  border: 7px solid green;
  background-color: gray;
  color: white;
  padding: 5px;
  margin: 0;
}
```

---

### 2\. Ejercicio 2: Margin (Espaciado Externo)

Este ejercicio ilustra cómo controlar el espaciado externo de las cajas usando la propiedad `margin`, centrándose en el `margin-top` y `margin-left` para posicionamiento relativo a un contenedor. También se refuerza el uso de `width` en porcentaje.

**Objetivo:** Crear tres cajas con `50%` de ancho y diferentes márgenes superiores e izquierdos dentro de un contenedor.

- **Propiedades clave a aplicar:**
  - `width`: `50%`
  - `margin-top`: Valores específicos (`10px`, `10px`, `10px`)
  - `margin-left`: Valores específicos (`10px`, `50px`, `100px`)
  - Propiedades básicas de `border` y `background-color` para visibilidad.

**Fragmento CSS esperable (asumiendo un contenedor para visualización):**

```html
<div class="contenedor-ejercicio-2">
  <div class="caja-ejercicio-2a">Caja A</div>
  <div class="caja-ejercicio-2b">Caja B</div>
  <div class="caja-ejercicio-2c">Caja C</div>
</div>
```

```css
.contenedor-ejercicio-2 {
  border: 1px dashed #ccc; /* Para visualizar el contenedor padre */
  padding: 10px;
  margin-bottom: 20px;
}

.contenedor-ejercicio-2 div {
  /*Éste selector aplica estilos a los tres hijos de manera común*/
  width: 50%;
  height: 70px; /* Altura fija para el ejemplo */
  border: 1px solid blue;
  background-color: lightblue;
  margin-bottom: 15px; /* Espacio entre las cajas para que no se peguen */
}

.caja-ejercicio-2a {
  margin-top: 10px;
  margin-left: 10px;
  padding: 10px 0;
}

.caja-ejercicio-2b {
  margin-top: 10px;
  margin-left: 50px;
}

.caja-ejercicio-2c {
  margin-top: 10px;
  margin-left: 100px;
}
```

---

### 3\. Ejercicio 3: Padding (Espaciado Interno)

Este ejercicio demuestra el efecto de la propiedad `padding` al añadir espacio entre el contenido y el borde de un elemento.

**Objetivo:** Crear tres cajas con diferentes valores de `padding` para observar cómo afecta el tamaño visible y el espaciado interno.

- **Propiedades clave a aplicar:**
  - `padding`: Valores específicos (`0`, `25px`, `50px`)
  - Propiedades básicas de `width`, `height`, `border` y `background-color`.
  - Es importante considerar el `box-sizing` para ver el efecto real del padding en el tamaño total. Si no se especifica `box-sizing: border-box;`, el padding _aumentará_ el tamaño total de la caja.

**Fragmento CSS esperable:**

```html
<div class="caja-padding-0">Esta es una caja sin relleno</div>
<div class="caja-padding-25">Esta es una caja con 25px de relleno</div>
<div class="caja-padding-50">Esta es una caja con 50px de relleno</div>
```

```css
/* Estilos base para todas las cajas de padding */
.caja-padding-0,
.caja-padding-25,
.caja-padding-50 {
  width: 200px; /* Ancho fijo */
  height: 80px; /* Altura fija */
  border: 2px solid green;
  background-color: lightgreen;
  margin-bottom: 15px;
  box-sizing: border-box; /* Para que el padding no aumente el tamaño total */
}

.caja-padding-0 {
  padding: 0;
}

.caja-padding-25 {
  padding: 25px;
}

.caja-padding-50 {
  padding: 50px;
}
```

---

### 4\. Ejercicio 4: Border (Estilos de Borde)

Este ejercicio explora las diferentes propiedades de `border`, incluyendo `border-style`, `border-color` y `border-width`, así como su aplicación en cajas anidadas.

**Objetivo:** Aplicar diferentes estilos de borde (sólido, punteado, rayado, doble, etc.) y colores a varias cajas, incluyendo ejemplos de cajas dentro de otras cajas para observar cómo los bordes las delimitan.

- **Propiedades clave a aplicar:**
  - `border` (shorthand) o `border-width`, `border-style`, `border-color`.
  - Diferentes `border-style` valores: `solid`, `dotted`, `dashed`, `double`, `groove`, `ridge`, `inset`, `outset`.
  - Combinación de colores y anchos de borde.

**Fragmento CSS esperable:**

```html
<div class="caja-borde-1">Esta es una caja con diferentes tipos de bordes</div>
<div class="caja-borde-2">Esta es otra caja con diferentes tipos de bordes</div>

<div class="caja-exterior">
  Esta es una caja con diferentes tipos de bordes dentro de otra caja
  <div class="caja-interior">Estas son cajas dentro de cajas</div>
</div>
```

```css
/* Estilos base */
.caja-borde-1,
.caja-borde-2,
.caja-exterior,
.caja-interior {
  width: 250px;
  height: 100px;
  background-color: #f9f9f9;
  margin-bottom: 15px;
  padding: 10px;
  box-sizing: border-box;
}

.caja-borde-1 {
  border: 3px solid blue;
}

.caja-borde-2 {
  /* Combinando diferentes estilos de borde en cada lado */
  border-width: 5px;
  border-style: dotted solid dashed double; /* Arriba, Derecha, Abajo, Izquierda */
  border-color: red green blue purple;
}

.caja-exterior {
  border: 4px groove orange;
  width: 300px; /* Un poco más grande para el anidamiento */
  height: 150px;
  background-color: #eee;
  padding: 20px;
}

.caja-interior {
  border: 2px inset gray;
  width: auto; /* Ocupa el espacio disponible en el padre */
  height: 80px;
  margin-top: 10px; /* Separa del texto del padre */
  background-color: white;
}
```
