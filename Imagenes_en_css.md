## 📝 Clase 15: Manejo de Imágenes en CSS (Parte I) - Un Resumen Visual

Este documento aborda las propiedades CSS fundamentales para la manipulación de imágenes, especialmente como fondos de elementos. Se explora cómo controlar la imagen de fondo, su posición, repetición, tamaño, y su relación con el modelo de cajas.

-----

### 1\. Introducción: Imágenes de Contenido vs. Imágenes de Decoración

Es crucial diferenciar entre los dos tipos de imágenes en el desarrollo web para aplicar las mejores prácticas y el CSS adecuado.

  * **Imágenes de Contenido:** Son imágenes esenciales para la comprensión del contenido de la página (ej. la foto de un producto en una tienda online, el gráfico principal de un artículo). Se insertan directamente en el HTML con la etiqueta `<img>`. Suelen ser relevantes para el SEO y la accesibilidad (con atributos `alt`).
  * **Imágenes de Decoración:** Son imágenes puramente estéticas que no aportan información crucial al contenido (ej. texturas de fondo, patrones, iconos que ya están descritos por texto). Se aplican generalmente con CSS como imágenes de fondo. No suelen tener impacto en el SEO y pueden ser omitidas por lectores de pantalla si no se gestionan con cuidado.

**Modelo de Cajas y Fondos:** Es importante recordar el Modelo de Cajas. Las imágenes de fondo se aplican *dentro* del área de contenido, extendiéndose por el padding y hasta el borde, dependiendo de la propiedad `background-clip`.

-----

### 2\. `background-image`

La propiedad `background-image` permite establecer una o más imágenes como fondo de un elemento.

**Uso / Explicación:** Esta propiedad es el punto de partida para colocar una imagen como fondo de cualquier elemento HTML (un `div`, `body`, `button`, etc.).

  * **Valores comunes:**
      * `none`: No se muestra ninguna imagen de fondo.
      * `url('ruta/a/imagen.jpg')`: Especifica la ruta a la imagen que se usará como fondo. Se pueden especificar múltiples URLs separadas por comas para apilar imágenes (la primera de la lista estará más arriba).
      * `linear-gradient()`, `radial-gradient()`, etc.: También se pueden usar funciones de CSS para crear gradientes como imágenes de fondo.

**Sintaxis:** `background-image: url('imagen.png');` o `background-image: url('imagen1.png'), url('imagen2.svg');`

#### Ejemplos de `background-image`

```html
<div class="header-banner">
  <h1>Bienvenidos</h1>
  <p>Un fondo de imagen para tu encabezado.</p>
</div>

<div class="pattern-background">
  <p>Este div tiene un patrón repetitivo como fondo.</p>
</div>
```

```css
/* Ejemplo 1: Una única imagen de fondo */
.header-banner {
  width: 100%;
  height: 300px;
  background-image: url('https://via.placeholder.com/800x300/ADD8E6/FFFFFF?text=Fondo+de+Cabecera');
  background-size: cover; /* Asegura que la imagen cubra todo el espacio */
  background-position: center; /* Centra la imagen */
  color: white;
  text-align: center;
  padding-top: 50px;
}

/* Ejemplo 2: Múltiples imágenes de fondo (capas) */
.pattern-background {
  width: 300px;
  height: 200px;
  /* La primera imagen es un patrón, la segunda es un gradiente */
  background-image: url('https://via.placeholder.com/50x50/FFD700/000000?text=.'),
                    linear-gradient(to right, lightgray, white);
  background-repeat: repeat; /* Repetir el patrón */
  background-size: 50px 50px, cover; /* Tamaño del patrón, y del gradiente */
  color: #333;
  padding: 20px;
}
```

-----

### 3\. `background-position`

La propiedad `background-position` especifica la posición inicial de una imagen de fondo.

**Uso / Explicación:** Permite controlar dónde se coloca la imagen de fondo dentro de su elemento. Es crucial cuando la imagen de fondo no se repite o cuando necesitas que una parte específica de la imagen sea visible.

  * **Valores comunes:**
      * **Palabras clave:** `top`, `bottom`, `left`, `right`, `center`. Se pueden combinar (ej. `top left`, `center center`).
      * **Longitudes (`px`, `em`, `rem`, etc.):** Valores absolutos o relativos para las coordenadas X e Y. El `0 0` es la esquina superior izquierda.
      * **Porcentajes (`%`):** Los porcentajes en `background-position` son especiales. Un porcentaje de `X% Y%` significa que el punto `X%` de la imagen se alinea con el punto `X%` del contenedor. Por ejemplo, `50% 50%` (o `center`) centra la imagen.

**Sintaxis:** `background-position: center;` o `background-position: 10px 20px;` o `background-position: 50% 50%;`

#### Ejemplos de `background-position`

```html
<div class="box-position-top-left"></div>
<div class="box-position-center"></div>
<div class="box-position-bottom-right"></div>
<div class="box-position-custom"></div>
```

```css
.base-box-bg-position {
  width: 250px;
  height: 150px;
  border: 1px solid #333;
  background-image: url('https://via.placeholder.com/100x100/FF5733/FFFFFF?text=IMG');
  background-repeat: no-repeat; /* Para ver el efecto de posicionamiento claramente */
  margin-bottom: 10px;
}

.box-position-top-left {
  @extend .base-box-bg-position;
  background-position: top left; /* Por defecto, pero explícito */
}

.box-position-center {
  @extend .base-box-bg-position;
  background-position: center center; /* Centrado */
}

.box-position-bottom-right {
  @extend .base-box-bg-position;
  background-position: bottom right; /* Esquina inferior derecha */
}

.box-position-custom {
  @extend .base-box-bg-position;
  background-position: 20px 30px; /* 20px desde la izquierda, 30px desde arriba */
}
```

-----

### 4\. `background-size`

La propiedad `background-size` especifica el tamaño de la imagen de fondo.

**Uso / Explicación:** Es esencial para controlar cómo la imagen de fondo se ajusta al tamaño del elemento, especialmente cuando la imagen y el elemento tienen diferentes proporciones.

  * **Valores comunes:**
      * `auto` (por defecto): El tamaño original de la imagen.
      * **Longitudes (`px`, `em`, `rem`, etc.):** Tamaños fijos para el ancho y/o alto (ej. `background-size: 100px 50px;` o `background-size: 100px;` para ancho, con alto automático).
      * **Porcentajes (`%`):** Un porcentaje del ancho y/o alto del contenedor.
      * `cover`: La imagen se escala para que cubra completamente el área de fondo del elemento, recortando la imagen si es necesario para mantener sus proporciones. Es excelente para fondos de "banner".
      * `contain`: La imagen se escala para que quepa completamente dentro del área de fondo del elemento, sin ser recortada, pero pudiendo dejar espacio vacío (similar a un "letterbox" o "pillarbox"). La imagen se ajustará al lado más largo del contenedor.

**Sintaxis:** `background-size: cover;` o `background-size: 100% auto;` o `background-size: 200px 150px;`

#### Ejemplos de `background-size`

```html
<div class="box-size-auto"></div>
<div class="box-size-cover"></div>
<div class="box-size-contain"></div>
<div class="box-size-custom"></div>
```

```css
.base-box-bg-size {
  width: 300px;
  height: 200px;
  border: 1px solid #333;
  background-image: url('https://via.placeholder.com/150x100/4CAF50/FFFFFF?text=IMG'); /* Imagen de 150x100 */
  background-repeat: no-repeat;
  background-position: center; /* Para ver bien el efecto */
  margin-bottom: 10px;
}

.box-size-auto {
  @extend .base-box-bg-size;
  background-size: auto; /* Tamaño original de la imagen (150x100) */
}

.box-size-cover {
  @extend .base-box-bg-size;
  background-size: cover; /* La imagen cubre todo el 300x200, se recorta si es necesario */
}

.box-size-contain {
  @extend .base-box-bg-size;
  background-size: contain; /* La imagen se ajusta dentro del 300x200, dejando espacio si es necesario */
}

.box-size-custom {
  @extend .base-box-bg-size;
  background-size: 100% 100%; /* Estira la imagen para llenar 100% de ancho y alto, distorsionándola */
}
```

-----

### 5\. `background-repeat`

La propiedad `background-repeat` define cómo se repite una imagen de fondo.

**Uso / Explicación:** Controla si y cómo una imagen de fondo se mosaica (repite) para cubrir el área de fondo del elemento.

  * **Valores comunes:**
      * `repeat` (por defecto): La imagen se repite tanto horizontal como verticalmente para cubrir todo el espacio.
      * `repeat-x`: La imagen se repite solo horizontalmente.
      * `repeat-y`: La imagen se repite solo verticalmente.
      * `no-repeat`: La imagen no se repite; se muestra solo una vez.
      * `space`: La imagen se repite tantas veces como sea posible sin recortarse, distribuyendo el espacio restante uniformemente entre las imágenes.
      * `round`: La imagen se repite tantas veces como sea posible sin recortarse; si no cabe un número entero de veces, se escalan las imágenes para que quepa un número entero.

**Sintaxis:** `background-repeat: no-repeat;` o `background-repeat: repeat-x;`

#### Ejemplos de `background-repeat`

```html
<div class="box-repeat-x"></div>
<div class="box-no-repeat"></div>
<div class="box-repeat"></div>
```

```css
.base-box-bg-repeat {
  width: 300px;
  height: 150px;
  border: 1px solid #333;
  background-image: url('https://via.placeholder.com/50x50/3498DB/FFFFFF?text=.'); /* Pequeña imagen para ver el patrón */
  margin-bottom: 10px;
}

.box-repeat-x {
  @extend .base-box-bg-repeat;
  background-repeat: repeat-x; /* Solo se repite horizontalmente */
}

.box-no-repeat {
  @extend .base-box-bg-repeat;
  background-repeat: no-repeat; /* No se repite, se muestra solo una vez */
  background-position: center;
}

.box-repeat {
  @extend .base-box-bg-repeat;
  background-repeat: repeat; /* Se repite horizontal y verticalmente (por defecto) */
}
```

-----

### 6\. `background-attachment`

La propiedad `background-attachment` establece si una imagen de fondo se desplaza con el contenido de un elemento o si es fija.

**Uso / Explicación:** Controla el comportamiento de desplazamiento de la imagen de fondo cuando el contenido del elemento (o de la página) se desplaza.

  * **Valores comunes:**
      * `scroll` (por defecto): La imagen de fondo se desplaza con el contenido del elemento.
      * `fixed`: La imagen de fondo se fija en la ventana del navegador (viewport), no se desplaza con el contenido. Esto crea un efecto de "paralaje".
      * `local`: La imagen de fondo se desplaza con el contenido del elemento, incluso si el contenido del elemento es desplazable (tiene `overflow: scroll`).

**Sintaxis:** `background-attachment: fixed;` o `background-attachment: scroll;`

#### Ejemplos de `background-attachment`

```html
<div class="scrollable-content">
  <div class="background-scroll">
    <p>Este es un texto de ejemplo que se desplaza.</p>
    <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.</p>
    <p>Más texto para asegurar el desplazamiento y ver el efecto del fondo.</p>
    <p>Fin del contenido.</p>
  </div>
</div>

<div class="background-fixed">
  <p>Este es un texto de ejemplo sobre un fondo fijo.</p>
  <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.</p>
  <p>Más texto para asegurar el desplazamiento y ver el efecto del fondo.</p>
  <p>Fin del contenido.</p>
</div>
```

```css
body {
  height: 200vh; /* Para asegurar que la página pueda desplazarse */
  margin: 0;
}

.scrollable-content {
  width: 80%;
  height: 300px;
  margin: 20px auto;
  overflow: scroll; /* Hace que este div sea desplazable internamente */
  border: 2px solid #555;
  background-color: #f9f9f9;
}

/* Ejemplo 1: Fondo se desplaza con el contenido del div */
.background-scroll {
  width: 100%;
  height: auto; /* Se ajusta al contenido */
  background-image: url('https://via.placeholder.com/200x200/F08080/FFFFFF?text=Fondo');
  background-repeat: repeat;
  background-attachment: scroll; /* Comportamiento por defecto, se desplaza con el scroll del div */
  padding: 15px;
  color: #333;
}

/* Ejemplo 2: Fondo fijo en el viewport, crea efecto paralaje */
.background-fixed {
  width: 100%;
  height: 400px;
  background-image: url('https://via.placeholder.com/1200x800/87CEEB/FFFFFF?text=Fondo+Fijo');
  background-repeat: no-repeat;
  background-position: center;
  background-size: cover;
  background-attachment: fixed; /* El fondo se mantiene fijo en el viewport */
  color: white;
  text-align: center;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 1.5em;
  text-shadow: 2px 2px 4px rgba(0,0,0,0.7);
}
```

-----

### 7\. `background-clip`

La propiedad `background-clip` especifica hasta dónde se extiende el fondo de un elemento.

**Uso / Explicación:** Define el área de pintura del fondo del elemento, permitiendo que la imagen o color de fondo se extienda hasta el borde, el padding, o solo el contenido.

  * **Valores comunes:**
      * `border-box` (por defecto): El fondo se extiende por debajo del borde.
      * `padding-box`: El fondo se extiende hasta el borde del padding (sin incluir el borde).
      * `content-box`: El fondo se extiende solo por debajo del área de contenido.
      * `text`: Recorta el fondo al texto del elemento. Solo funciona si el texto tiene un color transparente y el fondo es una imagen o gradiente. **Requiere prefijos de navegador (`-webkit-background-clip`) para una mejor compatibilidad.**

**Sintaxis:** `background-clip: padding-box;` o `background-clip: text;`

#### Ejemplos de `background-clip`

```html
<div class="box-clip-border">
  <p>Fondo en border-box</p>
</div>
<div class="box-clip-padding">
  <p>Fondo en padding-box</p>
</div>
<div class="box-clip-content">
  <p>Fondo en content-box</p>
</div>
<div class="box-clip-text">
  Texto con fondo de imagen
</div>
```

```css
.base-box-bg-clip {
  width: 300px;
  height: 100px;
  border: 10px dashed blue; /* Un borde visible para diferenciar */
  padding: 20px; /* Un padding visible */
  background-image: linear-gradient(to right, #FFD700, #FF6347); /* Un gradiente para el fondo */
  background-color: lightgray; /* Color de fondo de respaldo */
  margin-bottom: 20px;
  color: white; /* Color del texto */
  text-align: center;
  line-height: 60px; /* Para centrar verticalmente el texto en content-box */
  box-sizing: border-box;
}

.box-clip-border {
  @extend .base-box-bg-clip;
  background-clip: border-box; /* Fondo se extiende bajo el borde (por defecto) */
}

.box-clip-padding {
  @extend .base-box-bg-clip;
  background-clip: padding-box; /* Fondo se extiende hasta el borde del padding */
}

.box-clip-content {
  @extend .base-box-bg-clip;
  background-clip: content-box; /* Fondo se extiende solo bajo el contenido */
}

.box-clip-text {
  @extend .base-box-bg-clip;
  background-image: url('https://via.placeholder.com/300x100/FF0000/FFFFFF?text=Text+Background');
  color: transparent; /* Hace que el texto sea transparente */
  -webkit-background-clip: text; /* Recorta el fondo al texto (prefijo para compatibilidad) */
  background-clip: text; /* Versión estándar */
  font-size: 3em; /* Tamaño grande para ver el efecto */
  font-weight: bold;
  line-height: 100px; /* Centra el texto verticalmente */
  border: none; /* Sin borde para este ejemplo */
  padding: 0;
  background-color: transparent; /* No un color sólido debajo */
}
```

-----

### 8\. `background-blend-mode`

La propiedad `background-blend-mode` especifica cómo se mezcla la imagen de fondo de un elemento con su color de fondo u otras imágenes de fondo.

**Uso / Explicación:** Permite crear efectos de fusión entre las capas de fondo, similares a los modos de fusión en programas de edición de imágenes como Photoshop. Aplica a cada capa de `background-image` con la capa inferior y/o el `background-color`.

  * **Valores comunes:** `normal`, `multiply`, `screen`, `overlay`, `darken`, `lighten`, `color-dodge`, `color-burn`, `hard-light`, `soft-light`, `difference`, `exclusion`, `hue`, `saturation`, `color`, `luminosity`.

**Sintaxis:** `background-blend-mode: multiply;` o `background-blend-mode: screen;`

#### Ejemplos de `background-blend-mode`

```html
<div class="blend-multiply">
  <p>Modo de fusión: multiply</p>
</div>
<div class="blend-screen">
  <p>Modo de fusión: screen</p>
</div>
<div class="blend-overlay">
  <p>Modo de fusión: overlay</p>
</div>
```

```css
.base-box-blend {
  width: 300px;
  height: 200px;
  border: 1px solid #333;
  margin-bottom: 20px;
  padding: 10px;
  color: white;
  text-align: center;
  line-height: 180px; /* Aproximado para centrar el texto */
  font-size: 1.5em;
  text-shadow: 1px 1px 2px rgba(0,0,0,0.8);
  /* Imagen de fondo común para todos los ejemplos */
  background-image: url('https://via.placeholder.com/300x200/0000FF/FFFFFF?text=Imagen'); /* Azul */
  background-size: cover;
  background-position: center;
}

.blend-multiply {
  @extend .base-box-blend;
  background-color: #FF0000; /* Color de fondo rojo */
  background-blend-mode: multiply; /* Multiplica imagen azul con color rojo -> morado oscuro */
}

.blend-screen {
  @extend .base-box-blend;
  background-color: #FF0000; /* Color de fondo rojo */
  background-blend-mode: screen; /* Pantalla imagen azul con color rojo -> morado brillante */
}

.blend-overlay {
  @extend .base-box-blend;
  background-color: #FFD700; /* Color de fondo amarillo */
  background-blend-mode: overlay; /* Superpone imagen azul con color amarillo -> verde o turquesa */
}
```

---

¡Perfecto\! He analizado el PDF "CSS-Clase-16-Manejo-de-imagenes-en-CSS-II.pdf" y he preparado el resumen manteniendo la estructura y el estilo que te han gustado. Nos centraremos en `object-fit`, `aspect-ratio` y `gradient`, con explicaciones detalladas y ejemplos de código.

Aquí tienes el resumen:

-----

## 📝 Clase 16: Manejo de Imágenes en CSS (Parte II) - Un Resumen Visual

Este documento profundiza en la manipulación de imágenes en CSS, introduciendo propiedades clave como `object-fit` para controlar el ajuste de imágenes de contenido, `aspect-ratio` para mantener proporciones, y la creación de `gradient`s como fondos.

-----

### 1\. `object-fit`

La propiedad `object-fit` especifica cómo el contenido de un elemento `<img>` o `<video>` debe ajustarse a su caja de contenido. Es crucial para mantener la relación de aspecto original y evitar que las imágenes se distorsionen.

**Uso / Explicación:** Cuando trabajamos con imágenes de contenido (es decir, insertadas con la etiqueta `<img>` en el HTML) y queremos que se ajusten a un contenedor de tamaño fijo sin perder su proporción original, `object-fit` es la solución. Permite controlar cómo la imagen "rellena" o "se contiene" dentro de un espacio, de forma similar a `background-size` pero para imágenes de contenido.

#### Valores de `object-fit`

| Valor         | Uso / Explicación                                                                                                                                                                                                    |
| :------------ | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `fill`        | Rellena la imagen en el espacio del contenedor padre. Esto habitualmente estira o aplasta la imagen, distorsionándola, para que ocupe completamente el `width` y `height` del contenedor. Es el valor por defecto. |
| `contain`     | Mantiene la relación de aspecto original de la imagen, escalándola hacia abajo (o hacia arriba) para que la imagen completa sea visible dentro del contenedor. Pueden aparecer "barras" (espacio vacío) si las proporciones no coinciden. |
| `cover`       | Mantiene la relación de aspecto original de la imagen, escalándola hacia abajo (o hacia arriba) para que cubra completamente el contenedor. Partes de la imagen pueden ser recortadas si sus proporciones no coinciden con las del contenedor. |
| `none`        | La imagen no se redimensiona. Mantiene su tamaño original, centrándose en el contenedor. Si la imagen es más grande que el contenedor, se recortará; si es más pequeña, no se agrandará para llenar el espacio. |
| `scale-down` | Compara el tamaño de la imagen con lo que produciría `none` y `contain`, y usa el menor de los dos. Esto asegura que la imagen nunca sea más grande que su tamaño intrínseco, ni se estire si ya cabe dentro del contenedor. |

**Sintaxis:** `object-fit: cover;` o `object-fit: contain;`

#### Ejemplos de `object-fit`

```html
<div class="container-object-fit">
  <img src="https://via.placeholder.com/600x400/FF0000/FFFFFF?text=Original+IMG" alt="Imagen original 600x400" class="img-fill">
  <img src="https://via.placeholder.com/600x400/00FF00/FFFFFF?text=Original+IMG" alt="Imagen original 600x400" class="img-contain">
  <img src="https://via.placeholder.com/600x400/0000FF/FFFFFF?text=Original+IMG" alt="Imagen original 600x400" class="img-cover">
  <img src="https://via.placeholder.com/600x400/FFFF00/000000?text=Original+IMG" alt="Imagen original 600x400" class="img-none">
</div>
```

```css
.container-object-fit {
  display: grid; /* Para organizar los ejemplos */
  grid-template-columns: repeat(2, 1fr);
  gap: 20px;
  width: 600px; /* Ancho del contenedor de ejemplo */
  margin: 20px auto;
  border: 1px dashed #ccc;
  padding: 10px;
}

.container-object-fit img {
  width: 250px; /* Ancho fijo para todas las imágenes */
  height: 150px; /* Altura fija para todas las imágenes */
  border: 1px solid #555;
  background-color: lightgray; /* Color de fondo si la imagen no cubre todo */
}

.img-fill {
  object-fit: fill; /* La imagen se estira/aplasta para llenar 250x150 */
}

.img-contain {
  object-fit: contain; /* La imagen se escala para caber dentro de 250x150, manteniendo proporciones */
}

.img-cover {
  object-fit: cover; /* La imagen se escala para cubrir 250x150, manteniendo proporciones (puede recortarse) */
}

.img-none {
  object-fit: none; /* La imagen mantiene su tamaño original (600x400) y se recorta a 250x150 */
}
```

-----

### 2\. `aspect-ratio`

La propiedad `aspect-ratio` permite especificar la relación de aspecto preferida de un elemento, lo que le permite escalar el ancho o el alto de manera que se mantenga esa proporción.

**Uso / Explicación:** Antes de `aspect-ratio`, mantener la proporción de un elemento (especialmente para `div`s con imágenes de fondo o videos) requería trucos con `padding-top` en porcentaje. Esta propiedad simplifica enormemente esa tarea, permitiendo que la altura (o el ancho) de un elemento se ajuste automáticamente en función de su otra dimensión y una relación de aspecto definida.

  * **Valores comunes:**
      * `auto` (por defecto): El navegador determina la relación de aspecto predeterminada (generalmente la del contenido intrínseco si existe, como una imagen o video).
      * `width / height`: Un valor de relación de aspecto como `16 / 9`, `4 / 3`, `1 / 1` (cuadrado).
      * `initial`, `inherit`, `unset`.

**Sintaxis:** `aspect-ratio: 16 / 9;` o `aspect-ratio: 1 / 1;`

#### Ejemplos de `aspect-ratio`

```html
<div class="box-aspect-16-9">
  Contenido con relación de aspecto 16:9
</div>
<div class="box-aspect-1-1">
  Contenido con relación de aspecto 1:1
</div>
<img src="https://via.placeholder.com/800x600/FF5733/FFFFFF?text=Imagen+original+4:3" alt="Imagen con aspect-ratio" class="img-aspect">
```

```css
.box-aspect-16-9 {
  width: 80%; /* El ancho se define, la altura se calcula */
  aspect-ratio: 16 / 9; /* La altura será (9/16) * ancho */
  background-color: #f0f0f0;
  border: 2px solid #333;
  margin: 20px auto;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 1.2em;
  text-align: center;
}

.box-aspect-1-1 {
  width: 200px; /* Ancho fijo */
  aspect-ratio: 1 / 1; /* La altura será igual al ancho */
  background-color: #e0ffe0;
  border: 2px solid green;
  margin: 20px auto;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 1.2em;
  text-align: center;
}

.img-aspect {
  width: 100%; /* La imagen puede tener un ancho fluido */
  height: auto; /* La altura se calcula automáticamente para mantener la proporción */
  aspect-ratio: 4 / 3; /* Asegura que la imagen mantenga una proporción 4:3 sin distorsión, incluso si la imagen original no lo es */
  object-fit: cover; /* Para manejar cómo se ajusta si la proporción original difiere */
  display: block; /* Para eliminar el espacio debajo de la imagen */
  margin: 20px auto;
  max-width: 500px; /* Limita el ancho máximo */
}
```

-----

### 3\. Gradientes (`gradient`)

Los gradientes en CSS permiten crear transiciones suaves entre dos o más colores. Se utilizan como valores para propiedades de fondo, como `background-image`. Son puramente CSS, lo que los hace ligeros y escalables.

**Uso / Explicación:** Los gradientes eliminan la necesidad de usar imágenes para crear fondos degradados, reduciendo el tamaño de los archivos y mejorando la flexibilidad. Hay varios tipos de gradientes, siendo los más comunes los lineales y radiales.

#### `linear-gradient()`

**Uso / Explicación:** Crea un degradado que transita a lo largo de una línea recta.

  * **Parámetros:**
      * **Dirección:** Puede ser un ángulo (ej. `45deg`), o palabras clave (`to top`, `to bottom`, `to left`, `to right`, `to top right`, etc.). Si no se especifica, por defecto es `to bottom`.
      * **Colores y puntos de color:** Se especifican los colores que forman el gradiente. Opcionalmente, se pueden añadir puntos de parada (en porcentajes o longitudes) para controlar dónde comienza o termina la transición de cada color.

**Sintaxis:** `linear-gradient(direction, color1 [stop], color2 [stop], ...);`

#### `radial-gradient()`

**Uso / Explicación:** Crea un degradado que transita desde un punto central, propagándose hacia afuera en forma circular o elíptica.

  * **Parámetros:**
      * **Forma y tamaño:** Opcional. Puede ser `circle` o `ellipse`. También se puede definir el tamaño (ej. `closest-side`, `farthest-corner`, `100px`, `50%`).
      * **Posición:** Opcional. Define el centro del gradiente (ej. `at center`, `at 20% 30%`).
      * **Colores y puntos de color:** Igual que en `linear-gradient()`.

**Sintaxis:** `radial-gradient([shape] [size] at [position], color1 [stop], color2 [stop], ...);`

#### Ejemplos de Gradientes

```html
<div class="linear-gradient-basic"></div>
<div class="linear-gradient-angle"></div>
<div class="linear-gradient-stops"></div>
<div class="radial-gradient-circle"></div>
<div class="radial-gradient-ellipse"></div>
```

```css
.base-box-gradient {
  width: 300px;
  height: 150px;
  border: 1px solid #333;
  margin-bottom: 20px;
  display: flex;
  align-items: center;
  justify-content: center;
  color: white;
  font-weight: bold;
}

.linear-gradient-basic {
  @extend .base-box-gradient;
  background-image: linear-gradient(red, yellow); /* De rojo a amarillo, de arriba a abajo */
}

.linear-gradient-angle {
  @extend .base-box-gradient;
  background-image: linear-gradient(45deg, blue, green); /* De azul a verde en un ángulo de 45 grados */
}

.linear-gradient-stops {
  @extend .base-box-gradient;
  background-image: linear-gradient(to right, red 0%, red 25%, yellow 25%, yellow 75%, blue 75%, blue 100%);
  /* Múltiples colores con puntos de parada definidos */
}

.radial-gradient-circle {
  @extend .base-box-gradient;
  background-image: radial-gradient(circle at center, purple, orange); /* Círculo desde el centro */
}

.radial-gradient-ellipse {
  @extend .base-box-gradient;
  background-image: radial-gradient(ellipse at top left, cyan, magenta); /* Elipse desde la esquina superior izquierda */
}
```

#### Herramientas y consideraciones

  * **Generadores de gradientes online:** Existen numerosas herramientas web que facilitan la creación visual de gradientes y generan el código CSS automáticamente, como CSS Gradient Generator (cssgradient.io).
  * **Compatibilidad:** Los gradientes modernos son ampliamente compatibles, pero para navegadores muy antiguos podría ser necesario usar prefijos de proveedor (`-webkit-`, `-moz-`). Sin embargo, en la actualidad rara vez es necesario.

---

