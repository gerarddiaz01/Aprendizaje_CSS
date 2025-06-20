## 📝 Clase 10: Texto en CSS - Un Resumen Visual

Este documento resume las propiedades clave de CSS para manipular texto, organizadas para una fácil comprensión y referencia. La correcta elección y aplicación de estas propiedades es fundamental para la legibilidad y la estética de cualquier página web.

---

### 1. Tipografías

Las tipografías (o fuentes) son un pilar del diseño web, impactando directamente en cómo los usuarios perciben e interpretan el contenido.

#### Tipos de Tipografías

Existen diferentes tipos de tipografías que influyen en la percepción del texto:

- **Con Serifas (Serif):** Estas tipografías tienen pequeños remates o adornos al final de los trazos, como la `A` con serifa. Transmiten una sensación de tradición y formalidad.
- **Sin Serifas (Sans-serif o Paloseco):** A diferencia de las serifas, estas fuentes no tienen remates, como la `A` sin serifa. Ofrecen un aspecto moderno, limpio y son muy legibles en pantallas digitales.
- **Monoespaciadas:** En estas tipografías, cada carácter ocupa el mismo ancho, lo que las hace ideales para mostrar código o para lograr una alineación precisa, por ejemplo, `mono` siempre ocupará el mismo ancho.

---

### 2. `font-family`

La propiedad `font-family` es fundamental para especificar la fuente que se utilizará para el texto de un elemento. Es crucial proporcionar una lista de fuentes "de respaldo" por si la primera opción no está disponible en el sistema del usuario.

**Uso / Explicación:** Esta propiedad define la fuente principal y una o varias fuentes alternativas (genéricas o específicas). El navegador intentará cargar la primera fuente de la lista; si no la encuentra, pasará a la siguiente y así sucesivamente. Es vital terminar siempre con una familia genérica (como `serif`, `sans-serif`, `monospace`) para asegurar que el texto siempre tenga una fuente legible.

**Sintaxis:** Puedes especificar `font-family` de la siguiente manera: `font-family: "Nombre de Fuente", 'Otra Fuente', serif;`

#### Ejemplos de `font-family`

```css
/* Ejemplo 1: Fuente principal Arial, con Helvetica y una fuente genérica sans-serif como respaldo */
p {
  font-family: Arial, Helvetica, sans-serif;
}

/* Ejemplo 2: Fuente específica con espacio, debe ir entre comillas */
h1 {
  font-family: "Times New Roman", Times, serif;
}

/* Ejemplo 3: Uso de una fuente monoespaciada para un bloque de código */
pre {
  font-family: "Courier New", Courier, monospace;
}
```

---

### 3. `font-size` y `font-style`

Estas propiedades controlan el tamaño y el estilo (normal, cursiva, oblicua) del texto, respectivamente.

#### `font-size`

**Uso / Explicación:** La propiedad `font-size` establece el tamaño del texto. Se recomienda encarecidamente usar unidades relativas como `em`, `rem`, o porcentajes para asegurar la escalabilidad y accesibilidad de la tipografía en diferentes dispositivos y configuraciones de usuario.

- **Unidades comunes:**
  - **`px` (píxeles):** Es una unidad absoluta. El tamaño del texto será fijo y no escalará con la configuración de tamaño de fuente del navegador del usuario.
  - **`em`:** Es una unidad relativa al `font-size` del elemento padre. Si el elemento padre no tiene un `font-size` definido, la hereda del abuelo y así sucesivamente. Esto puede generar cascadas complejas.
  - **`rem`:** Es una unidad relativa al `font-size` del elemento raíz (`<html>`). Es más predecible que `em` para la escalabilidad global del sitio, ya que solo depende de un único valor base.
  - **`%` (porcentaje):** Relativa al `font-size` del elemento padre. Funciona de manera similar a `em`.
  - **`vw` (viewport width) / `vh` (viewport height):** Relativas al ancho o alto del viewport (área visible del navegador). Son útiles para crear tipografía fluida que se ajusta dinámicamente al tamaño de la pantalla.
  - **Palabras clave:** También se pueden usar palabras clave predefinidas como `xx-small`, `x-small`, `small`, `medium`, `large`, `x-large`, `xx-large` para tamaños preestablecidos, o `smaller` y `larger` para ajustar el tamaño en relación con el elemento padre.

**Sintaxis:** Puedes establecer `font-size` de varias maneras: `font-size: 16px;`, `font-size: 1.2em;`, `font-size: 1.5rem;`, `font-size: 120%;`

#### Ejemplos de `font-size`

```css
/* Ejemplo 1: Tamaño fijo en píxeles */
.titulo {
  font-size: 24px;
}

/* Ejemplo 2: Tamaño relativo al padre (1.2 veces el tamaño del padre) */
.parrafo-secundario {
  font-size: 1.2em;
}

/* Ejemplo 3: Tamaño relativo al elemento raíz (HTML) */
body {
  font-size: 16px; /* Establece el tamaño base del documento */
}
h2 {
  font-size: 1.8rem; /* 1.8 veces el tamaño base del HTML (16px * 1.8 = 28.8px) */
}

/* Ejemplo 4: Tamaño con porcentaje */
.descripcion {
  font-size: 90%; /* 90% del tamaño del elemento padre */
}
```

#### `font-style`

**Uso / Explicación:** La propiedad `font-style` define el estilo de la fuente.

**Sintaxis:** Los valores posibles son: `font-style: normal;`, `font-style: italic;` (para cursiva), o `font-style: oblique;` (para una versión inclinada).

#### Ejemplos de `font-style`

```css
/* Ejemplo 1: Texto en estilo normal (por defecto) */
p {
  font-style: normal;
}

/* Ejemplo 2: Texto en cursiva */
em {
  font-style: italic;
}

/* Ejemplo 3: Texto inclinado (a menudo similar a italic, pero puede ser una versión sintetizada de la fuente) */
.inclinado {
  font-style: oblique;
}
```

---

### 4. `font-weight`

La propiedad `font-weight` controla el grosor o la negrita del texto.

**Uso / Explicación:** Esta propiedad establece el grosor de la fuente. Los valores pueden ser palabras clave o números.

- **Valores comunes:**
  - **`normal`:** Equivalente a un valor numérico de `400`.
  - **`bold`:** Equivalente a un valor numérico de `700`.
  - **`bolder`:** Hace el texto más grueso que el grosor heredado del elemento padre.
  - **`lighter`:** Hace el texto más delgado que el grosor heredado del elemento padre.
  - **Valores numéricos:** Se pueden usar números de `100` a `900` (en múltiplos de 100). Es importante tener en cuenta que no todas las fuentes soportan todos los valores; si un valor específico no está disponible, el navegador elegirá el grosor más cercano que sí esté disponible para esa fuente.

**Sintaxis:** Puedes especificar `font-weight` de estas maneras: `font-weight: normal;`, `font-weight: bold;`, `font-weight: 700;`, `font-weight: 300;`

#### Ejemplos de `font-weight`

```css
/* Ejemplo 1: Texto normal */
.texto-regular {
  font-weight: normal; /* o font-weight: 400; */
}

/* Ejemplo 2: Texto en negrita */
strong {
  font-weight: bold; /* o font-weight: 700; */
}

/* Ejemplo 3: Texto más ligero (si la fuente lo soporta) */
.subtitulo-ligero {
  font-weight: lighter;
}

/* Ejemplo 4: Uso de valores numéricos para control más fino del grosor */
.titulo-seccion {
  font-weight: 600; /* Un poco más grueso que normal, pero no tan negrita */
}
```

---

### 5. `line-height`

La propiedad `line-height` define la altura de cada línea de texto (interlineado), afectando el espacio vertical entre las líneas. Es crucial para la legibilidad del contenido.

**Uso / Explicación:** Esta propiedad establece la altura de una línea. Se recomienda usar un valor numérico sin unidad para una mejor escalabilidad y accesibilidad. Este valor numérico representa un múltiplo del `font-size` del elemento al que se aplica, lo que significa que el interlineado escalará proporcionalmente con el tamaño de la fuente.

- **Valores comunes:**
  - **`normal`:** Es el valor predeterminado del navegador, que puede variar ligeramente entre diferentes navegadores.
  - **Número (sin unidad):** La altura de la línea será el resultado de multiplicar este número por el `font-size` del elemento. **Este es el método más recomendado** por su predictibilidad y adaptabilidad.
  - **`em`:** Relativo al `font-size` del propio elemento.
  - **`px`:** Un valor absoluto en píxeles. Su uso no se recomienda generalmente porque el interlineado no se adaptará si el tamaño de la fuente cambia.
  - **`%` (porcentaje):** Relativo al `font-size` del propio elemento.

**Sintaxis:** Algunos ejemplos de cómo se utiliza `line-height`: `line-height: normal;`, `line-height: 1.5;`, `line-height: 24px;`, `line-height: 150%;`

#### Ejemplos de `line-height`

```css
/* Ejemplo 1: Interlineado estándar para buena legibilidad (1.5 veces el tamaño de la fuente) */
p {
  line-height: 1.5;
}

/* Ejemplo 2: Interlineado más ajustado para títulos o bloques de texto cortos */
h3 {
  line-height: 1.2;
}

/* Ejemplo 3: Interlineado en píxeles (menos recomendado por falta de escalabilidad) */
.caja-info {
  line-height: 20px;
}
```

---

### 6. `text-indent`

La propiedad `text-indent` añade una sangría al texto de la primera línea de un bloque.

**Uso / Explicación:** Esta propiedad permite especificar la cantidad de espacio horizontal que se debe aplicar antes de la primera línea de texto de un elemento. Los valores pueden ser positivos (la sangría empuja la primera línea hacia la derecha) o negativos (la sangría mueve la primera línea hacia la izquierda, lo que a menudo saca el texto del contenedor y requiere compensación con padding).

**Sintaxis:** Se puede definir con: `text-indent: 50px;` o `text-indent: 3em;`

#### Ejemplos de `text-indent`

```css
/* Ejemplo 1: Sangría positiva, la primera línea se mueve hacia la derecha */
.articulo p {
  text-indent: 30px;
}

/* Ejemplo 2: Sangría negativa (creando un efecto de "hanging indent") */
.lista-definiciones dt {
  text-indent: -2em; /* Mueve el texto de la primera línea hacia la izquierda */
  padding-left: 2em; /* Compensa con padding para que el resto del texto se alinee */
}

/* Ejemplo 3: Sangría con porcentaje, relativa al ancho del contenedor del texto */
.introduccion {
  text-indent: 5%;
}
```

---

### 7. `word-spacing`

La propiedad `word-spacing` ajusta el espacio entre las palabras de un texto.

**Uso / Explicación:** Esta propiedad controla la distancia horizontal entre las palabras. Puede ser útil para mejorar la legibilidad o para ajustar el diseño de textos con tipografías que tengan un espaciado predeterminado insuficiente o excesivo. Acepta valores positivos (para aumentar el espacio) y negativos (para disminuir el espacio).

**Sintaxis:** Se puede usar: `word-spacing: normal;`, `word-spacing: 5px;`, `word-spacing: -2px;`

#### Ejemplos de `word-spacing`

```css
/* Ejemplo 1: Espaciado normal entre palabras (por defecto del navegador) */
body {
  word-spacing: normal;
}

/* Ejemplo 2: Aumentar el espacio entre palabras para un efecto más amplio */
.titulo-expandido {
  word-spacing: 10px;
}

/* Ejemplo 3: Disminuir el espacio entre palabras (debe usarse con cuidado para no afectar la legibilidad) */
.texto-compacto {
  word-spacing: -1px;
}

/* Ejemplo 4: Espaciado relativo al tamaño de la fuente del elemento */
.parrafo-espaciado {
  word-spacing: 0.3em; /* 0.3 veces el tamaño de la fuente del párrafo */
}
```

---

### 8. `letter-spacing`

La propiedad `letter-spacing` ajusta el espacio entre los caracteres (letras) individuales de un texto.

**Uso / Explicación:** Esta propiedad permite controlar el espacio horizontal entre los caracteres de un texto. Se utiliza para mejorar la legibilidad en algunos casos, o más comúnmente, para crear efectos de diseño específicos. Acepta valores positivos (para aumentar el espacio entre letras) y negativos (para disminuir el espacio, creando un efecto de texto más "apretado").

**Sintaxis:** Se puede aplicar con: `letter-spacing: normal;`, `letter-spacing: 2px;`, `letter-spacing: -0.5px;`

#### Ejemplos de `letter-spacing`

```css
/* Ejemplo 1: Espaciado normal entre letras (por defecto del navegador) */
h1 {
  letter-spacing: normal;
}

/* Ejemplo 2: Aumentar el espacio entre letras para un efecto de "ensanchamiento" */
.marca {
  letter-spacing: 3px;
  text-transform: uppercase; /* A menudo se combina con mayúsculas para mejor efecto */
}

/* Ejemplo 3: Disminuir el espacio entre letras (útil para textos grandes o efectos artísticos muy específicos) */
.titulo-compacto {
  letter-spacing: -0.8px;
  font-size: 3em;
}

/* Ejemplo 4: Espaciado relativo al tamaño de la fuente del elemento */
.slogan {
  letter-spacing: 0.1em; /* 0.1 veces el tamaño de la fuente del eslogan */
}
```

---

### 9. `text-align`

La propiedad `text-align` especifica la alineación horizontal del texto dentro de un elemento de bloque.

**Uso / Explicación:** Esta propiedad define cómo se alinean las líneas de un texto dentro de su contenedor. Es importante recordar que afecta a bloques de texto y no a elementos `inline` individuales.

**Sintaxis:** Se utiliza con valores como: `text-align: left;`, `text-align: center;`

#### Valores de `text-align`

- **`left`:** Alinea el texto a la izquierda. Este es el valor predeterminado para la mayoría de los idiomas que se leen de izquierda a derecha.
- **`right`:** Alinea el texto a la derecha.
- **`center`:** Centra el texto horizontalmente dentro de su contenedor.
- **`justify`:** Justifica el texto, lo que significa que el navegador estira el espacio entre las palabras para que cada línea (excepto la última) ocupe todo el ancho disponible del contenedor, creando una apariencia de bloque uniforme.

#### Ejemplos de `text-align`

```css
/* Ejemplo 1: Texto alineado a la izquierda */
.parrafo-izquierda {
  text-align: left;
}

/* Ejemplo 2: Título centrado */
h2 {
  text-align: center;
}

/* Ejemplo 3: Pie de página alineado a la derecha */
footer p {
  text-align: right;
}

/* Ejemplo 4: Texto justificado para una apariencia de bloque uniforme en párrafos largos */
.contenido-principal p {
  text-align: justify;
}
```

---

### 10. `text-decoration`

La propiedad `text-decoration` se utiliza para añadir o quitar líneas al texto, como subrayado, línea superior, tachado o parpadeo. Es importante destacar que la opción `blink` (parpadeo) está obsoleta y rara vez es soportada por los navegadores modernos.

**Uso / Explicación:** Esta propiedad permite aplicar varias decoraciones visuales al texto. Además de los tipos de línea, CSS3 y versiones posteriores permiten especificar el color y el estilo de la línea de decoración.

- **Valores comunes para el tipo de línea (`text-decoration-line`):**
  - **`none`:** Elimina cualquier decoración, útil para quitar el subrayado predeterminado de los enlaces.
  - **`underline`:** Añade un subrayado al texto.
  - **`overline`:** Añade una línea por encima del texto.
  - **`line-through`:** Añade una línea que atraviesa el texto (tachado).
- **Propiedades adicionales (sub-propiedades de `text-decoration`):**
  - **`text-decoration-color`:** Define el color de la línea de decoración.
  - **`text-decoration-style`:** Define el estilo de la línea (por ejemplo, `solid`, `double`, `dotted`, `dashed`, `wavy`).
  - **`text-decoration-thickness`:** Define el grosor de la línea.

**Sintaxis:** Se puede usar la propiedad abreviada `text-decoration` o las propiedades individuales:

- Forma abreviada: `text-decoration: underline red wavy;` (tipo, color, estilo)
- Propiedades individuales:
  - `text-decoration-line: underline;`
  - `text-decoration-color: blue;`
  - `text-decoration-style: dotted;`
  - `text-decoration-thickness: 2px;`

#### Ejemplos de `text-decoration`

```css
/* Ejemplo 1: Eliminar el subrayado predeterminado de los enlaces */
a {
  text-decoration: none;
}

/* Ejemplo 2: Texto subrayado */
.destacado {
  text-decoration: underline;
}

/* Ejemplo 3: Texto con una línea por encima */
.encabezado-superior {
  text-decoration: overline;
}

/* Ejemplo 4: Texto tachado (por ejemplo, para indicar un precio anterior) */
.precio-antiguo {
  text-decoration: line-through;
  color: #888;
}

/* Ejemplo 5: Subrayado con color y estilo personalizados (sintaxis abreviada) */
.enlace-personalizado {
  text-decoration: underline 2px solid #007bff; /* Subrayado azul sólido de 2px */
}

/* Ejemplo 6: Usando propiedades individuales para un tachado ondulado de color rojo */
.tarea-completa {
  text-decoration-line: line-through;
  text-decoration-color: red;
  text-decoration-style: wavy;
  text-decoration-thickness: 1px;
}
```

---

## 📝 Clase 11: Texto en CSS

Este documento profundiza en propiedades de texto en CSS, incluyendo el control de espacios en blanco, la gestión de saltos de línea y palabras, transformaciones de texto y decoraciones adicionales.

---

### 1. Espacios en Blanco

El manejo de los espacios en blanco en HTML y CSS es crucial para controlar cómo el texto se presenta y se ajusta dentro de los elementos. La propiedad principal para esto es `white-space`.

#### `white-space`

**Uso / Explicación:** La propiedad `white-space` controla cómo se manejan los espacios en blanco, los saltos de línea y los saltos de página dentro de un elemento. Es muy útil para preservar el formato de texto preformateado o para evitar que el texto se ajuste en nuevas líneas.

- **Valores comunes:**
  - **`normal` (por defecto):** Secuencia de espacios en blanco colapsados en un solo espacio. Las líneas se ajustan cuando es necesario.
  - **`nowrap`:** Los espacios en blanco se colapsan, pero las líneas no se ajustan (el texto no salta de línea), permaneciendo en una sola línea hasta que se encuentre una etiqueta `<br>`.
  - **`pre`:** Los espacios en blanco son preservados por el navegador, y las líneas solo se rompen en los saltos de línea dentro del código fuente (similar a la etiqueta `<pre>` de HTML).
  - **`pre-wrap`:** Los espacios en blanco son preservados, pero las líneas se ajustan cuando es necesario para evitar desbordamiento del contenedor, y también se rompen en los saltos de línea del código fuente.
  - **`pre-line`:** Los espacios en blanco se colapsan, pero las líneas se rompen en los saltos de línea del código fuente y también se ajustan si el contenido desborda el contenedor.
  - **`break-spaces`:** Similar a `pre-wrap`, pero los espacios en blanco al final de la línea no se cuelgan y se incluyen en el tamaño mínimo intrínseco de la línea.

**Sintaxis:** `white-space: normal;` o `white-space: nowrap;`

#### Ejemplos de `white-space`

```html
<div class="normal">Este es un texto con espacios extra y saltos de línea.</div>

<div class="nowrap">
  Este es un texto que no debería saltar de línea a menos que se fuerce con
  <br />.
</div>

<div class="pre">Este texto mantiene su formato pre-existente.</div>

<div class="pre-wrap">
  Este texto preserva espacios y saltos, pero se ajusta al ancho del contenedor.
</div>

<div class="pre-line">
  Este texto colapsa espacios, pero rompe las líneas y se ajusta.
</div>
```

```css
/* Ejemplo 1: Comportamiento por defecto */
.normal {
  white-space: normal;
  border: 1px solid #ccc;
  width: 200px;
}

/* Ejemplo 2: El texto se mantiene en una sola línea */
.nowrap {
  white-space: nowrap;
  overflow: auto; /* Para ver el scroll horizontal */
  border: 1px solid #ccc;
  width: 200px;
}

/* Ejemplo 3: Preserva todos los espacios y saltos de línea del código fuente */
.pre {
  white-space: pre;
  border: 1px solid #ccc;
  width: 200px;
}

/* Ejemplo 4: Preserva espacios pero ajusta al contenedor */
.pre-wrap {
  white-space: pre-wrap;
  border: 1px solid #ccc;
  width: 200px;
}

/* Ejemplo 5: Colapsa espacios pero respeta saltos de línea del código y ajusta */
.pre-line {
  white-space: pre-line;
  border: 1px solid #ccc;
  width: 200px;
}
```

---

### 2. Límites de Línea y Palabras (Overflow)

Estas propiedades controlan cómo se maneja el texto cuando desborda su contenedor, especialmente en casos donde no hay espacios o cuando se desea forzar un salto de palabra.

#### `overflow-wrap` (anteriormente `word-wrap`)

**Uso / Explicación:** La propiedad `overflow-wrap` especifica si el navegador puede romper una palabra larga (que no contiene espacios ni guiones) para evitar que desborde su contenedor. Esto es especialmente útil para URLs largas o cadenas de texto sin espacios.

- **Valores comunes:**
  - **`normal` (por defecto):** Las palabras solo se rompen en los puntos de ruptura permitidos (espacios, guiones).
  - **`break-word`:** Permite que las palabras largas se rompan en cualquier punto si no hay un punto de ruptura adecuado que evite el desbordamiento. La palabra se romperá incluso en el medio.

**Sintaxis:** `overflow-wrap: normal;` o `overflow-wrap: break-word;`

#### Ejemplos de `overflow-wrap`

```html
<div class="normal-wrap">
  Aquí hay una
  palabra-extremadamente-larga-que-podría-desbordar-el-contenedor-si-no-se-rompe.
</div>

<div class="break-word-wrap">
  Aquí hay una
  palabra-extremadamente-larga-que-podría-desbordar-el-contenedor-si-no-se-rompe.
</div>
```

```css
/* Ejemplo 1: Comportamiento normal, si la palabra es muy larga, desborda */
.normal-wrap {
  width: 150px;
  border: 1px solid blue;
  margin-bottom: 10px;
  overflow-wrap: normal; /* No romperá la palabra a menos que haya un guion o espacio */
}

/* Ejemplo 2: La palabra se romperá en cualquier punto para ajustarse */
.break-word-wrap {
  width: 150px;
  border: 1px solid red;
  overflow-wrap: break-word; /* Forzará la rotura de la palabra */
}
```

#### `word-break`

**Uso / Explicación:** La propiedad `word-break` especifica cómo se deben romper las palabras cuando alcanzan el final de la línea. A diferencia de `overflow-wrap`, que se enfoca en el desbordamiento de palabras _largas_, `word-break` se centra en las reglas generales de rotura de palabras para ajustar el texto.

- **Valores comunes:**
  - **`normal` (por defecto):** Utiliza las reglas de salto de línea predeterminadas del idioma (por ejemplo, en inglés, las palabras no se rompen a menos que haya un guion o espacio).
  - **`break-all`:** Las palabras pueden romperse en cualquier carácter para ajustar el texto al contenedor, incluso en medio de palabras cortas o sin espacios. Esto es útil para textos en idiomas asiáticos.
  - **`keep-all`:** Las palabras no se rompen en ningún punto. Esto es especialmente útil para idiomas como el coreano, donde se deben evitar las roturas de caracteres. Puede causar desbordamiento si no hay espacios.
  - **`break-word`:** (En este contexto, es un alias heredado de `overflow-wrap: break-word;`. Es mejor usar `overflow-wrap` para ese propósito específico).

**Sintaxis:** `word-break: normal;` o `word-break: break-all;`

#### Ejemplos de `word-break`

```html
<div class="normal-break">
  This is a very very long sentence that might not fit in a narrow container.
</div>

<div class="break-all">
  Este es un texto muy largo para probar la rotura de todas las palabras.
  日本語の長い文章をテストします。
</div>

<div class="keep-all">Estaesunapalabrasinespaciosquedebedesbordar.</div>
```

```css
/* Ejemplo 1: Comportamiento normal de rotura de palabra */
.normal-break {
  width: 150px;
  border: 1px solid blue;
  margin-bottom: 10px;
  word-break: normal;
}

/* Ejemplo 2: Rompe las palabras en cualquier carácter si es necesario */
.break-all {
  width: 150px;
  border: 1px solid red;
  margin-bottom: 10px;
  word-break: break-all;
}

/* Ejemplo 3: No rompe palabras, incluso si causan desbordamiento */
.keep-all {
  width: 150px;
  border: 1px solid green;
  overflow: auto; /* Para ver el desbordamiento */
  word-break: keep-all;
}
```

---

### 3. Alineación Vertical (`vertical-align`)

La propiedad `vertical-align` se utiliza para alinear verticalmente elementos `inline` y `inline-block`, así como el contenido de las celdas de una tabla. Es importante entender que **no funciona en elementos de bloque**.

#### `vertical-align`

**Uso / Explicación:** Esta propiedad define la alineación vertical de un elemento `inline` o `inline-block` con respecto a su línea base o con respecto al elemento que lo contiene. También se usa para el contenido de las celdas de tabla (`<td>`).

- **Valores comunes:**
  - **`baseline` (por defecto):** Alinea la línea base del elemento con la línea base del padre.
  - **`sub`:** Alinea la línea base del elemento con la posición de subíndice del padre.
  - **`super`:** Alinea la línea base del elemento con la posición de superíndice del padre.
  - **`top`:** Alinea la parte superior del elemento con la parte superior del elemento más alto de la línea.
  - **`text-top`:** Alinea la parte superior del elemento con la parte superior de la fuente del padre.
  - **`middle`:** Alinea el punto medio del elemento con la línea base más la mitad de la altura 'x' del padre. (No el centro geométrico de la línea).
  - **`bottom`:** Alinea la parte inferior del elemento con la parte inferior del elemento más bajo de la línea.
  - **`text-bottom`:** Alinea la parte inferior del elemento con la parte inferior de la fuente del padre.
  - **Longitudes (`px`, `em`, etc.):** Desplaza el elemento hacia arriba (valores positivos) o hacia abajo (valores negativos) desde la línea base.
  - **Porcentajes (`%`):** Similar a las longitudes, pero relativo a la `line-height` del propio elemento.

**Sintaxis:** `vertical-align: middle;` o `vertical-align: 5px;`

#### Ejemplos de `vertical-align`

```html
<p style="font-size: 20px;">
  Texto normal
  <img
    src="https://via.placeholder.com/20x20"
    alt="tiny square"
    style="vertical-align: baseline;"
  />
  Baseline (defecto)
  <img
    src="https://via.placeholder.com/20x20"
    alt="tiny square"
    style="vertical-align: top;"
  />
  Top
  <img
    src="https://via.placeholder.com/20x20"
    alt="tiny square"
    style="vertical-align: middle;"
  />
  Middle
  <img
    src="https://via.placeholder.com/20x20"
    alt="tiny square"
    style="vertical-align: bottom;"
  />
  Bottom
  <img
    src="https://via.placeholder.com/20x20"
    alt="tiny square"
    style="vertical-align: -5px;"
  />
  -5px
  <img
    src="https://via.placeholder.com/20x20"
    alt="tiny square"
    style="vertical-align: super;"
  />
  <sup>Super</sup>
</p>

<table>
  <tr>
    <td style="height: 60px; vertical-align: top; border: 1px solid;">Top</td>
    <td style="height: 60px; vertical-align: middle; border: 1px solid;">
      Middle
    </td>
    <td style="height: 60px; vertical-align: bottom; border: 1px solid;">
      Bottom
    </td>
  </tr>
</table>
```

```css
/* No se requiere CSS adicional para los ejemplos inline en el HTML,
   pero aquí está cómo se aplicaría en una hoja de estilos: */
.icon {
  vertical-align: middle;
  margin-right: 5px;
}

/* Para celdas de tabla */
table td {
  padding: 5px;
}

.cell-top {
  vertical-align: top;
}

.cell-middle {
  vertical-align: middle;
}

.cell-bottom {
  vertical-align: bottom;
}
```

---

### 4. Transformaciones de Texto (`text-transform`)

La propiedad `text-transform` se utiliza para convertir el texto de un elemento entre mayúsculas, minúsculas o capitalizado.

#### `text-transform`

**Uso / Explicación:** Esta propiedad controla la capitalización del texto de un elemento sin necesidad de cambiar el contenido HTML original.

- **Valores comunes:**
  - **`none` (por defecto):** El texto se muestra tal cual está en el HTML.
  - **`capitalize`:** Convierte la primera letra de cada palabra a mayúscula.
  - **`uppercase`:** Convierte todo el texto a mayúsculas.
  - **`lowercase`:** Convierte todo el texto a minúsculas.
  - **`full-width`:** Convierte caracteres de ancho completo (útil para ideogramas, por ejemplo, en japonés).

**Sintaxis:** `text-transform: uppercase;` o `text-transform: capitalize;`

#### Ejemplos de `text-transform`

```html
<p class="normal-text">Este es un texto normal.</p>
<p class="capitalized-text">este es un texto que será capitalizado.</p>
<p class="uppercase-text">Este texto estará en mayúsculas.</p>
<p class="lowercase-text">ESTE TEXTO ESTARÁ EN MINÚSCULAS.</p>
```

```css
/* Ejemplo 1: Sin transformación (comportamiento por defecto) */
.normal-text {
  text-transform: none;
}

/* Ejemplo 2: La primera letra de cada palabra en mayúscula */
.capitalized-text {
  text-transform: capitalize;
}

/* Ejemplo 3: Todo el texto en mayúsculas */
.uppercase-text {
  text-transform: uppercase;
  font-weight: bold; /* A menudo combinado */
}

/* Ejemplo 4: Todo el texto en minúsculas */
.lowercase-text {
  text-transform: lowercase;
}
```

---

### 5. Dirección del Texto (`direction`)

La propiedad `direction` establece la dirección base del texto para elementos de bloque, y la dirección de los elementos en línea dentro de un bloque bidireccional. Es fundamental para idiomas que se leen de derecha a izquierda.

#### `direction`

**Uso / Explicación:** Esta propiedad es clave para la internacionalización, permitiendo que el texto fluya de izquierda a derecha (L-T-R) o de derecha a izquierda (R-T-L).

- **Valores comunes:**
  - **`ltr` (left-to-right):** El texto se lee de izquierda a derecha (valor predeterminado para la mayoría de los idiomas occidentales).
  - **`rtl` (right-to-left):** El texto se lee de derecha a izquierda (para idiomas como el árabe, hebreo, persa, urdu).

**Sintaxis:** `direction: rtl;` o `direction: ltr;`

#### Ejemplos de `direction`

```html
<div class="texto-ltr">
  This is a left-to-right text. Este es un texto de izquierda a derecha.
</div>

<div class="texto-rtl">
  هذا نص يقرأ من اليمين إلى اليسار. .שמאל לימין מימין נקרא טקסט זה
</div>
```

```css
/* Ejemplo 1: Dirección de texto de izquierda a derecha */
.texto-ltr {
  direction: ltr;
  border: 1px solid blue;
  padding: 10px;
  margin-bottom: 10px;
}

/* Ejemplo 2: Dirección de texto de derecha a izquierda */
.texto-rtl {
  direction: rtl;
  border: 1px solid red;
  padding: 10px;
}
```

---

### 6. Pseudo-clases y Pseudo-elementos Relacionados con Texto

Mientras que el PDF de la Clase 11 no los detalla explícitamente, es importante mencionar que existen pseudo-clases y pseudo-elementos que son muy relevantes para dar estilo al texto, como ya se vio en el documento de "Selectores".

- **`::first-line`**: Selecciona la primera línea formateada de un elemento de bloque.
  - **Ejemplo:** `p::first-line { font-weight: bold; color: navy; }`
- **`::first-letter`**: Selecciona la primera letra de la primera línea formateada de un elemento de bloque.
  - **Ejemplo:** `p::first-letter { font-size: 2em; float: left; margin-right: 5px; }`
- **`::selection`**: Aplica estilos al fragmento de texto seleccionado por el usuario.
  - **Ejemplo:** `::selection { background-color: yellow; color: black; }`

---

## 📝 Clase 12: Tipografías en CSS

Este documento aborda las diferentes formas de gestionar y utilizar tipografías en CSS, desde las fuentes seguras del sistema hasta la integración de fuentes externas y personalizadas, destacando las mejores prácticas y consideraciones importantes.

---

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
