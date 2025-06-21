## 📝 Clase 12: Tipografías en CSS

### 1. Tipografías de Sistema

Las tipografías de sistema son aquellas que se encuentran instaladas por defecto en el sistema operativo del usuario. Su principal ventaja es que cargan rápidamente, ya que no necesitan ser descargadas, y son muy fiables. Sin embargo, su disponibilidad es limitada, y no siempre garantizan una estética uniforme en todos los dispositivos.

**Uso / Explicación:** Cuando se especifica una `font-family`, siempre es recomendable incluir una lista de fuentes de sistema (o "seguras para la web") como respaldo. Esto asegura que, si la primera fuente deseada no está disponible, el navegador tenga una alternativa cercana para mostrar el texto, evitando el uso de fuentes predeterminadas que podrían romper el diseño.

**Sintaxis:** Se utilizan en la propiedad `font-family` en el CSS, separadas por comas.

#### Ejemplos de Tipografías de Sistema

Algunas de las tipografías de sistema más comunes y sus familias genéricas son:

- `Arial`, `Helvetica`, `sans-serif`
- `Times New Roman`, `Times`, `serif`
- `Courier New`, `Courier`, `monospace`
- `Georgia`, `serif`
- `Verdana`, `Geneva`, `sans-serif`
- `Trebuchet MS`, `sans-serif`

```css
/* Ejemplo 1: Priorizando Arial, con Helvetica y sans-serif como respaldo */
body {
  font-family: Arial, Helvetica, sans-serif;
}

/* Ejemplo 2: Usando una fuente con serifa como Times New Roman */
h1 {
  font-family: "Times New Roman", Times, serif;
}

/* Ejemplo 3: Fuente monoespaciada para bloques de código */
pre {
  font-family: "Courier New", Courier, monospace;
}
```

---

### 2. Uso de Tipografías Custom (Personalizadas)

Las tipografías custom o personalizadas son fuentes que no están preinstaladas en el sistema del usuario, sino que deben ser proporcionadas por el sitio web. Esto permite una mayor libertad creativa y un diseño más coherente y único. El método principal para incluir estas fuentes es mediante la regla `@font-face`.

#### `@font-face`

**Uso / Explicación:** La regla `@font-face` permite definir fuentes personalizadas para que sean utilizadas en las páginas web. Al definir una fuente con `@font-face`, se especifica el nombre que se le dará a esa fuente (`font-family`) y la ubicación de sus archivos (`src`). El navegador descargará el archivo de la fuente y lo aplicará al texto que utilice el `font-family` definido.

- **`font-family`**: El nombre que le darás a esta fuente dentro de tu CSS.
- **`src`**: Especifica la URL del archivo de la fuente. Es crucial proporcionar múltiples formatos de fuente (`.woff2`, `.woff`, `.ttf`, `.otf`, `.svg`, `.eot`) para asegurar la compatibilidad con diferentes navegadores. El formato `woff2` es el más recomendado por su tamaño reducido y eficiencia. Se pueden listar múltiples formatos con `format()` para que el navegador elija el que mejor soporte.
- **`font-weight` y `font-style`**: Permiten asociar diferentes variantes (regular, negrita, cursiva) de la misma familia de fuentes a pesos y estilos específicos. Esto evita tener que declarar una `@font-face` diferente para cada peso si la fuente original incluye esas variaciones.

**Sintaxis básica:**

```css
@font-face {
  font-family: "MiFuentePersonalizada";
  src: url("path/to/mifuente.woff2") format("woff2"), url("path/to/mifuente.woff")
      format("woff");
  font-weight: normal;
  font-style: normal;
}
```

#### Ejemplos de `@font-face`

```css
/* Ejemplo 1: Definición básica de una fuente personalizada */
@font-face {
  font-family: "RobotoSlab";
  src: url("/fonts/RobotoSlab-Regular.woff2") format("woff2"), url("/fonts/RobotoSlab-Regular.woff")
      format("woff");
  font-weight: 400;
  font-style: normal;
}

/* Ejemplo 2: Definiendo la versión en negrita de la misma fuente */
@font-face {
  font-family: "RobotoSlab";
  src: url("/fonts/RobotoSlab-Bold.woff2") format("woff2"), url("/fonts/RobotoSlab-Bold.woff")
      format("woff");
  font-weight: 700; /* Asignamos el peso de negrita */
  font-style: normal;
}

/* Una vez definidas, se usan como cualquier otra fuente */
body {
  font-family: "RobotoSlab", serif; /* Se usa el nombre definido en @font-face */
}

h1 {
  font-family: "RobotoSlab", serif;
  font-weight: 700; /* Esto usará el archivo Bold.woff2 si está definido */
}
```

---

### 3. Conversor de Tipografías

El uso de múltiples formatos de fuente (`.woff2`, `.woff`, `.ttf`, etc.) es esencial para la compatibilidad con diferentes navegadores. Originalmente, las fuentes se distribuían principalmente en formatos `.ttf` (TrueType) y `.otf` (OpenType). Sin embargo, los navegadores modernos prefieren formatos más optimizados para la web como `.woff` (Web Open Font Format) y especialmente `.woff2`.

**Uso / Explicación:** Los conversores de tipografías son herramientas (online o de escritorio) que toman un archivo de fuente en un formato (por ejemplo, `.ttf`) y lo transforman en otros formatos web optimizados. Esto asegura que la fuente se cargue eficientemente en una amplia gama de navegadores y dispositivos.

**Herramientas comunes:**

- **Font Squirrel (Generador de @font-face):** Una de las herramientas más populares. Permite subir una fuente y genera un paquete completo con todos los formatos necesarios (`.woff2`, `.woff`, `.ttf`, `.svg`, `.eot`) junto con el código CSS `@font-face` listo para usar.
- **Transfonter:** Otra herramienta online robusta para la conversión de fuentes y generación de `@font-face`.
- **Google Fonts (para fuentes alojadas localmente):** Aunque Google Fonts se usa principalmente para alojar fuentes externamente, también permite descargar las fuentes para alojarlas localmente, proporcionando los formatos `.ttf` o `.woff2` que luego se pueden usar con `@font-face`.

**Recomendación:** Siempre que uses fuentes personalizadas, es una buena práctica utilizar un generador de `@font-face` para obtener todos los formatos y el CSS optimizado para una compatibilidad máxima y un mejor rendimiento.

**Pasos:**

- Descargamos la fuente que queremos, por ejemplo por Google Fonts, y nos dan solo un archivo ttf. Sabemos que por compatibilidad con los navegadores no es muy conveniente, necesitamos los archivos woff, woff2, svg y eot.
- Para conseguirlos usamos Transfonter por ejemplo, un conversor de fuentes, ponemos el archivo ttf y nos dan todas las otras fuentes de compatibilidad junto con un stylesheet.css con un bloque de có digo para añadir a nuestro archivo style.css.
- Crear una carpeta fonts y poner dentro las fuentes en todas sus compatibilidades.
- Obviamente tenemos que juntar style.css al archivo html que lo requiera (pueden ser varios) y en el archivo css poner el bloque de código que tenemos en la carpeta que nos hemos descargado de Transfonter, el font-face con todas las fuentes compatibles, y ojo que hay que modificar el src para que apunte a la adecuada carpeta donde tenemos las fuentes.
- Luego podemos usar las fuentes en nuestros selectores de forma normal usando font-family, en el mismo archivo style.css.

---

### 4. Tipografías Externas: Google Fonts

Google Fonts es un servicio de Google que permite a los desarrolladores web utilizar una amplia biblioteca de fuentes de código abierto directamente en sus sitios web. Es una forma muy popular y sencilla de incorporar tipografías de alta calidad sin necesidad de alojarlas localmente.

**Uso / Explicación:** Para usar una fuente de Google Fonts, generalmente hay dos métodos principales:

1.  **Enlace (`<link>` en HTML):** El método más común. Se añade una etiqueta `<link>` en la sección `<head>` de tu documento HTML que apunta al servicio de Google Fonts, el cual se encarga de servir el archivo de la fuente.
2.  **Importación (`@import` en CSS):** Se puede importar la fuente directamente desde una hoja de estilos CSS utilizando la regla `@import`. Este método es menos recomendado que el `<link>` en términos de rendimiento.

**Sintaxis (`<link>`):**

```html
<head>
  <link rel="preconnect" href="https://fonts.googleapis.com" />
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
  <link
    href="https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap"
    rel="stylesheet"
  />
</head>
```

**Sintaxis (`@import` en CSS):**

```css
@import url("https://fonts.googleapis.com/css2?family=Open+Sans:wght@400;700&display=swap");
```

**Definir la tipografía a usar:** Una vez que la fuente ha sido importada (ya sea por `<link>` o `@import`), se utiliza en el CSS mediante la propiedad `font-family`, igual que cualquier otra fuente:

```css
body {
  font-family: "Roboto", sans-serif;
}

h1 {
  font-family: "Roboto", sans-serif;
  font-weight: 700; /* Si se importó el peso 700 */
}
```

#### Ejemplos de Google Fonts

```html
<!DOCTYPE html>
<html lang="es">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Uso de Google Fonts</title>
    <link rel="preconnect" href="https://fonts.googleapis.com" />
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
    <link
      href="https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap"
      rel="stylesheet"
    />
    <style>
      body {
        font-family: "Roboto", sans-serif; /* Aplicar Roboto al cuerpo */
        font-size: 18px;
        line-height: 1.6;
      }

      h1 {
        font-family: "Roboto", sans-serif;
        font-weight: 700; /* Usar el peso negrita de Roboto */
        color: #333;
      }

      p {
        margin-bottom: 1em;
      }
    </style>
  </head>
  <body>
    <h1>¡Bienvenidos a mi sitio!</h1>
    <p>Este párrafo utiliza la fuente Roboto con el peso normal (400).</p>
    <p style="font-weight: 700;">
      Este párrafo también usa Roboto, pero con el peso en negrita (700).
    </p>
  </body>
</html>
```

---

### 5. Uso Correcto de Google Fonts

Aunque Google Fonts es muy conveniente, hay consideraciones importantes para un uso óptimo y legal.

#### Optimización de Rendimiento

**Uso / Explicación:** Para mejorar la velocidad de carga de la página, es recomendable:

- **Seleccionar solo los pesos y estilos necesarios:** No importes todos los pesos de una fuente si solo usarás uno o dos. Cada peso es un archivo separado que el navegador debe descargar.
- **Usar `display=swap`:** Este parámetro en la URL de importación de Google Fonts le dice al navegador que muestre el texto con una fuente de respaldo (del sistema) mientras la fuente de Google se está descargando. Una vez descargada, la fuente de Google "intercambiará" la fuente de respaldo. Esto evita el "texto invisible durante la carga de la web" (FOIT - Flash Of Invisible Text) y mejora la percepción de rendimiento.
- **Usar `font-display: swap;` en `@font-face`:** Si alojas las fuentes localmente, esta es la propiedad CSS equivalente a `display=swap` en la URL de Google Fonts.

#### Consideraciones de la GDPR (Reglamento General de Protección de Datos)

**Uso / Explicación:** La privacidad de los usuarios es un aspecto crítico. Al usar Google Fonts directamente (importando desde los servidores de Google), la dirección IP del usuario se envía a Google. En Europa, esto ha generado preocupaciones bajo la GDPR, ya que podría considerarse una transferencia de datos personales sin el consentimiento explícito del usuario.

**Solución para la GDPR:**

- **Alojar las fuentes localmente (`self-hosting`):** La forma más segura de cumplir con la GDPR es descargar las fuentes de Google Fonts y alojarlas en tu propio servidor. De esta manera, el navegador del usuario no realiza ninguna solicitud directa a Google para obtener los archivos de la fuente, y no se comparte ninguna dirección IP.

**Cómo alojar fuentes de Google Fonts localmente:**

1.  **Descarga la familia con los pesos seleccionados:** Ve a Google Fonts, selecciona la fuente y los pesos que necesitas, y luego descarga la familia completa (generalmente un archivo ZIP con `.ttf` o `.woff2`).
2.  **Usa `@font-face`:** Coloca los archivos de la fuente descargados en tu servidor (por ejemplo, en una carpeta `/fonts`) y luego define la fuente en tu CSS usando la regla `@font-face`, apuntando a tus archivos locales.

#### Ejemplo de uso correcto de Google Fonts (Auto-alojado)

Este es el enfoque recomendado para la privacidad y el control total:

```css
/* Ejemplo de CSS con fuente Roboto auto-alojada */
@font-face {
  font-family: "Roboto";
  src: url("/fonts/Roboto-Regular.woff2") format("woff2"), url("/fonts/Roboto-Regular.woff")
      format("woff");
  font-weight: 400;
  font-style: normal;
  font-display: swap; /* Muestra el texto con una fuente de respaldo mientras se carga */
}

@font-face {
  font-family: "Roboto";
  src: url("/fonts/Roboto-Bold.woff2") format("woff2"), url("/fonts/Roboto-Bold.woff")
      format("woff");
  font-weight: 700;
  font-style: normal;
  font-display: swap;
}

body {
  font-family: "Roboto", sans-serif;
}
```

---

## 📝 Clase 13: Iconos Tipográficos

### 1. ¿Qué son los Iconos Tipográficos?

Los iconos tipográficos son, esencialmente, fuentes de caracteres especiales que, en lugar de letras o números, representan gráficos o símbolos. Se les llama "tipográficos" porque se comportan como texto: se les puede aplicar color, tamaño, sombras, y otras propiedades CSS de texto.

**Uso / Explicación:** Permiten reemplazar imágenes pequeñas para representar iconos (como un icono de casa, un carrito de compras, flechas, etc.). En lugar de incrustar una imagen (JPG, PNG, SVG), se incrusta un carácter de una fuente especial.

#### Ventajas de los Iconos Tipográficos

- **Escalabilidad:** Al ser vectores, se escalan a cualquier tamaño sin perder calidad (no se pixelan), lo que los hace ideales para pantallas de alta densidad (Retina).
- **Personalización fácil con CSS:** Se pueden cambiar su tamaño (`font-size`), color (`color`), añadir sombras (`text-shadow`), e incluso aplicarles transformaciones CSS o animaciones, todo con CSS, sin necesidad de herramientas de edición de imágenes.
- **Menor tamaño de archivo:** Un solo archivo de fuente que contiene muchos iconos suele ser más pequeño que múltiples archivos de imagen separados, lo que mejora los tiempos de carga.
- **Compatibilidad con navegadores:** Ampliamente soportados por los navegadores modernos.
- **Accesibilidad:** Pueden ser leídos por lectores de pantalla si se implementan correctamente con atributos ARIA.
- **Consistencia:** Permiten mantener un estilo visual coherente en todos los iconos del sitio, ya que provienen de la misma familia de fuentes.

---

### 2. Propiedades y Mejoras de los Iconos Tipográficos VS. Imágenes

La elección entre iconos tipográficos e imágenes depende de las necesidades específicas del proyecto. Sin embargo, los iconos tipográficos ofrecen ventajas significativas en la mayoría de los casos.

#### Propiedades y Mejoras

- **Modificables con CSS:** Como se mencionó, `font-size`, `color`, `text-shadow` son fácilmente aplicables. También se pueden usar pseudo-clases como `:hover` para cambiar su estilo al pasar el ratón.
- **Rendimiento:** Un solo archivo de fuente HTTP request (solicitud) para cargar muchos iconos es más eficiente que múltiples solicitudes HTTP para cada imagen individual. Esto es especialmente cierto para iconos simples.
- **Flexibilidad:** Facilidad para cambiar estilos globalmente o por componente sin modificar el HTML.

#### Casos donde las Imágenes (SVG, PNG, JPG) pueden ser más apropiadas:

- **Detalle muy preciso:** Si necesitas iconos con muchos detalles finos, gradientes, o efectos complejos que son difíciles de lograr con una sola capa de color (como lo permite una fuente).
- **Ilustraciones complejas:** Para gráficos que son más ilustraciones que iconos simples, o logotipos complejos.
- **Variedad de colores:** Si un icono requiere múltiples colores distintos que no se pueden controlar con una única propiedad `color`. Aunque SVG puede ser una buena alternativa aquí, los iconos tipográficos generalmente se limitan a un color principal.

**Conclusión:** En general, usar tipografías de iconos en CSS es una práctica común en el diseño web moderno debido a sus beneficios en términos de rendimiento, personalización y accesibilidad. Las imágenes se reservan para casos donde la complejidad visual del gráfico supera las capacidades de una fuente.

---

### 3. Ejemplos de Uso (Librerías de Iconos Tipográficos)

Existen varias librerías populares que facilitan la integración de iconos tipográficos en tus proyectos web.

#### **Font Awesome**

- **Uso / Explicación:** Es una de las librerías de iconos más conocidas y utilizadas. Ofrece una vasta colección de iconos que se pueden integrar fácilmente con una etiqueta `<link>` en el HTML o mediante `@import` en CSS. Los iconos se usan con etiquetas `<i>` o `<span>` y clases específicas.

- **Ventajas:** Gran variedad de iconos, muy bien documentada, comunidad activa, opciones gratuitas y de pago.

- **Ejemplo de integración (versión gratuita CDN):**

  ```html
  <head>
    <link
      rel="stylesheet"
      href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.2/css/all.min.css"
      integrity="sha512-SnH5WK+bZxgPHs44uWIX+LLJAJ9/2PkPKZ5QiAj6Ta86w+fsb2TkcmfRyVX3pBnMFcV7oQPJkl9QevSCWr3W6A=="
      crossorigin="anonymous"
      referrerpolicy="no-referrer"
    />
  </head>
  <body>
    <i class="fas fa-home"></i> <i class="fab fa-github"></i>
    <span style="font-size: 2em; color: blue;"
      ><i class="fas fa-star"></i
    ></span>
  </body>
  ```

#### **Google Material Icon Font**

- **Uso / Explicación:** Ofrecido por Google, esta librería proporciona iconos que siguen los principios de Material Design. Son limpios, modernos y están optimizados para web. Se pueden integrar de manera similar a Google Fonts.

- **Ventajas:** Alta calidad visual, consistencia con Material Design, ligereza.

- **Ejemplo de integración:**

  ```html
  <head>
    <link
      href="https://fonts.googleapis.com/icon?family=Material+Icons"
      rel="stylesheet"
    />
  </head>
  <body>
    <i class="material-icons">home</i> <i class="material-icons">settings</i>
    <span style="font-size: 36px; color: green;"
      ><i class="material-icons">check_circle</i></span
    >
  </body>
  ```

#### **Bootstrap Icons**

- **Uso / Explicación:** Si ya estás usando el framework Bootstrap en tu proyecto, Bootstrap Icons es una excelente opción para mantener la coherencia de diseño. Es una colección de iconos SVG que se pueden insertar directamente como SVG o usar como fuente de iconos.

- **Ventajas:** Integración perfecta con Bootstrap, iconos de alta calidad, personalización con CSS (si se usan como fuente).

- **Ejemplo de integración (usando CSS):**

  ```html
  <head>
    <link
      rel="stylesheet"
      href="https://cdn.jsdelivr.net/npm/bootstrap-icons@1.11.3/font/bootstrap-icons.min.css"
    />
  </head>
  <body>
    <i class="bi bi-house"></i> <i class="bi bi-gear"></i>
    <span style="color: purple;"><i class="bi bi-heart-fill"></i></span>
  </body>
  ```

#### **Flaticon**

- **Uso / Explicación:** Flaticon es una plataforma que ofrece una enorme base de datos de iconos en varios formatos, incluyendo colecciones de iconos que puedes descargar y usar como fuentes tipográficas personalizadas (`@font-face`). Te permite crear tus propias fuentes de iconos personalizadas seleccionando los que necesitas.
- **Ventajas:** Enorme variedad, posibilidad de crear fuentes personalizadas con solo los iconos que necesitas, diferentes estilos.

#### **Icomoon**

- **Uso / Explicación:** Icomoon es una herramienta poderosa que te permite importar iconos SVG (incluyendo los tuyos propios o de otras librerías), seleccionarlos, y luego exportar una fuente de iconos personalizada con solo los glifos que necesitas. Genera el archivo de fuente optimizado y el código CSS `@font-face`.
- **Ventajas:** Control total sobre qué iconos incluyes, ideal para optimización de rendimiento (solo cargas lo necesario), soporta tus propios diseños SVG.
- **Ejemplo de flujo de trabajo:**
  1.  Seleccionar iconos en la web de Icomoon.
  2.  Descargar el paquete (contiene archivos `.woff`, `.ttf`, etc., y un archivo `style.css`).
  3.  Incluir el archivo CSS generado (`style.css`) en tu proyecto.
  4.  Usar los iconos con las clases generadas (ej. `<span class="icon-home"></span>`).

**Conclusión:** La elección de la librería de iconos depende de tus necesidades de diseño, la coherencia con otros frameworks que uses y tus preferencias de flujo de trabajo. Todas ofrecen beneficios significativos sobre el uso de imágenes individuales para iconos.

**Pasos para Fontawesome:**

- Ir a fontawesome, buscar el embed code de nuestro kit de iconos free, ponerlo en el head de los html que queramos usar dichos iconos.
- El embed code es así <script src="https://kit.fontawesome.com/89caaf1462.js" crossorigin="anonymous"></script>
- Luego ir al icono, editarlo con color u animaciones y copiar el link del icono, sería algo así <i class="fa-solid fa-earth-americas"></i>
- Poner directamente el link donde queramos en el documento html dentro de una etiqueta que funciona cómo si fuese una palabra.

#### Limitaciones

Poner el link de cada librería para sólo utilizar un par de iconos no es para nada óptimo porqué el user está descargando todos los iconos al acceder a la página web, sería mejor descargarse los iconos y adjuntos los archivos svg en la carpeta icons de nuestra web, y acceder a esos iconos directamente sin redireccionar la IP del usuario para descargar los iconos cada vez que se accede a la web.

**Pasos para bajarse e instalar iconos de icomoon:**

- Vamos a Icomoon (free), hacemos una selección de los iconos que queremos, le damos a generar tipografía (font), descargamos la carpeta con las tipografias (iconos) y el demo file.
- Ponemos las tipografias dentro de la carpeta icons en nuestra web.
- Copiamos el texto del documento css de icomoon y lo ponemos en nuestro style.css, le cambiamos el src de las fuentas para encontrarlos, están en la carpeta icons.
- usamos la siguiente sintaxis para poner los iconos en nuestro html, reemplazando "icon-world" por el nombre de la tipografía.
  <span class="icon-world" style="font-size: 25px;"></span>

**Pasos para crear iconos custom e instalarlos en nuestra web:**

- Buscar una librería de iconos svg de figma
- Abrir el archivo con figma, seleccionar con "frame" el que queremos y lo exportamos en svg, también podemos crearlo nosotros en figma.
- Vamos a icomoon y los importamos allí en otra librería vacía nuestra.
- Seleccionamos nuestros iconos, y le damos a generate font.
