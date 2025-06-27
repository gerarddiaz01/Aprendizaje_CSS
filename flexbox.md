## 📝 Clase 20: Flexbox

Este documento introduce el concepto de Flexbox en CSS como un sistema de maquetación moderno y eficiente, comparándolo con los métodos tradicionales de posicionamiento. También repasa los tipos de caja fundamentales (`inline`, `block`, `inline-block`) y la propiedad `z-index` para el apilamiento de elementos.

-----

### 1\. Introducción a Flexbox

Históricamente, CSS utilizaba propiedades como `position` (static, relative, absolute), elementos `inline` o `block`, y `float` para la maquetación. Flexbox (también conocido como Flex) es un sistema más potente, limpio y personalizable que permite que los elementos HTML se adapten y posicionen automáticamente, facilitando el diseño de páginas web.

Para empezar a usar Flexbox, es fundamental entender sus elementos básicos:

  * **Contenedor (Flex Container):** Es el elemento padre que contiene a los ítems flexibles. En Flexbox, las propiedades se suelen establecer en el elemento padre.
  * **Ítem (Flex Item):** Cada uno de los hijos dentro del contenedor flex.

#### Ejes en Flexbox

Los contenedores flexibles tienen dos ejes principales que determinan la orientación y disposición de los ítems:

  * **Eje Principal:** La orientación principal de los ítems. Por defecto, es horizontal (en fila).
  * **Eje Secundario:** Es perpendicular al eje principal. Si el eje principal es horizontal, el secundario será vertical (y viceversa).

**Ejemplo de Estructura Flexbox:**

```html
<div class="container"> 
    <div class="item item-1">1</div> 
    <div class="item item-2">2</div>
    <div class="item item-3">3</div>
</div>
```

-----

### 2\. Tipos de Caja `display` (Repaso)

La propiedad `display` de CSS permite modificar el comportamiento de un elemento HTML, controlando su tipo de caja y cómo se renderiza en la página.

#### Valores comunes de `display` (repaso)

| Valor           | Características                                                                                                                                                                                                                            |
| :-------------- | :----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `block`         | Se apila verticalmente, ocupando todo el ancho disponible de su contenedor. Permite establecer `width`, `height`, `padding`, `margin`, etc..                                                                                   |
| `inline`        | Se coloca horizontalmente, adaptándose al ancho de su contenido. Ignora las propiedades `width` y `height`. Se comportan como palabras en una oración, separadas por un espacio en blanco.                             |
| `inline-block`  | Combina características de `inline` y `block`. Se comporta como `inline` (se coloca en línea) pero no ignora `width` ni `height`.                                                                                                |
| `flex` / `inline-flex` | Estos valores activan el contexto de Flexbox para el contenedor. `flex` se comporta como un elemento de bloque, mientras que `inline-flex` se comporta como un elemento en línea pero con sus contenidos distribuidos por flexbox. |

El comportamiento de los elementos en bloque y en línea es fundamental, y su disposición por defecto se conoce como "Flujo normal".

-----

### 3\. Propiedades del Contenedor Flex (`display: flex;`)

Una vez que un elemento se establece como contenedor flex (`display: flex;` o `display: inline-flex;`), se pueden aplicar varias propiedades para controlar la disposición de sus ítems hijos.

#### `flex-direction`

Define la dirección del eje principal, es decir, cómo se colocan los ítems flexibles en el contenedor.

| Valor           | Descripción                                   |
| :-------------- | :-------------------------------------------- |
| `row` (por defecto) | Los ítems se colocan en fila (horizontal, de izquierda a derecha). |
| `row-reverse`   | Los ítems se colocan en fila, pero en orden inverso (de derecha a izquierda). |
| `column`        | Los ítems se colocan en columna (vertical, de arriba abajo). |
| `column-reverse` | Los ítems se colocan en columna, pero en orden inverso (de abajo arriba). |

#### `flex-wrap`

Controla si los ítems flex deben ajustarse a una sola línea o envolverse en varias líneas si no caben en el contenedor.

| Valor           | Descripción                                                                 |
| :-------------- | :-------------------------------------------------------------------------- |
| `nowrap` (por defecto) | Los ítems se mantienen en una sola línea, pudiendo desbordar el contenedor. |
| `wrap`          | Los ítems se envuelven en múltiples líneas de arriba hacia abajo si no hay suficiente espacio. |
| `wrap-reverse`  | Los ítems se envuelven en múltiples líneas de abajo hacia arriba.           |

#### `gap`

Define el espacio (hueco) entre las filas y columnas de los ítems flexibles. Permite establecer un espacio uniforme sin depender de márgenes complejos.

  * **Sintaxis:** `gap: <longitud>;` (ej. `gap: 10px;`) o `gap: <row-gap> <column-gap>;` (ej. `gap: 10px 30px;`).

#### `justify-content`

Alinea los ítems a lo largo del **eje principal** del contenedor flex.

| Valor             | Descripción                                                                 |
| :---------------- | :-------------------------------------------------------------------------- |
| `flex-start` (por defecto) | Los ítems se agrupan al inicio del eje principal.                         |
| `flex-end`        | Los ítems se agrupan al final del eje principal.                           |
| `center`          | Los ítems se centran en el eje principal.                                  |
| `space-between`   | Los ítems se distribuyen uniformemente, con el primer ítem al inicio y el último al final. |
| `space-around`    | Los ítems se distribuyen uniformemente, con espacio igual alrededor de cada ítem. |
| `space-evenly`    | Los ítems se distribuyen uniformemente, con espacio igual entre ellos y en los extremos. |

#### `align-items`

Alinea los ítems a lo largo del **eje secundario** (perpendicular al eje principal) dentro de una línea flex.

| Valor           | Descripción                                                                   |
| :-------------- | :---------------------------------------------------------------------------- |
| `stretch` (por defecto) | Los ítems se estiran para llenar el contenedor en el eje secundario (si no tienen un `height` o `width` definido). |
| `flex-start`    | Los ítems se alinean al inicio del eje secundario.                          |
| `flex-end`      | Los ítems se alinean al final del eje secundario.                            |
| `center`        | Los ítems se centran en el eje secundario.                                    |
| `baseline`      | Los ítems se alinean en sus líneas de base.                                   |

#### `align-content`

Esta propiedad alinea las líneas flex del contenedor cuando hay espacio adicional en el eje secundario, y cuando `flex-wrap` está establecido en `wrap` o `wrap-reverse`.

| Valor             | Descripción                                                                 |
| :---------------- | :-------------------------------------------------------------------------- |
| `flex-start`      | Las líneas se agrupan al inicio del eje secundario.                         |
| `flex-end`        | Las líneas se agrupan al final del eje secundario.                           |
| `center`          | Las líneas se centran en el eje secundario.                                  |
| `stretch` (por defecto) | Las líneas se estiran para ocupar el espacio disponible.                  |
| `space-between`   | Las líneas se distribuyen uniformemente, con la primera al inicio y la última al final. |
| `space-around`    | Las líneas se distribuyen uniformemente, con espacio igual alrededor de cada línea. |

-----

### 4\. Propiedades de los Ítems Flex

Estas propiedades se aplican directamente a los elementos hijos (`flex items`) dentro de un contenedor flex.

#### `align-self`

Permite anular la alineación predeterminada (`align-items`) para un ítem flex individual, alineándolo a lo largo del eje secundario.

| Valor           | Descripción                                                                   |
| :-------------- | :---------------------------------------------------------------------------- |
| `auto` (por defecto) | Hereda el valor de `align-items` de su padre.                               |
| `flex-start`    | El ítem se alinea al inicio del eje secundario.                              |
| `flex-end`      | El ítem se alinea al final del eje secundario.                                |
| `center`        | El ítem se centra en el eje secundario.                                       |
| `baseline`      | El ítem se alinea en su línea de base.                                       |
| `stretch`       | El ítem se estira para llenar el contenedor en el eje secundario.            |

#### `order`

Controla el orden visual de los ítems flexibles, independientemente de su orden en el código fuente HTML. Los ítems se ordenan de menor a mayor valor de `order`.

  * **Sintaxis:** `order: <número_entero>;` (ej. `order: 1;`, `order: -1;`, `order: 99;`).
      * Por defecto, todos los ítems tienen `order: 0`.

#### `flex-basis`

Define el tamaño base por defecto que tendrán los ítems antes de que se les aplique cualquier distribución de espacio flexible.

  * **Sintaxis:** `flex-basis: <longitud> | auto;` (ej. `flex-basis: 100px;`, `flex-basis: auto;`).
      * `auto` (por defecto): El navegador determina el tamaño basado en el contenido o el ancho/alto del ítem.

#### `flex-grow`

Especifica el factor de crecimiento de un ítem flexible en relación con los demás ítems dentro del contenedor, en caso de que haya espacio adicional disponible.

  * **Sintaxis:** `flex-grow: <número>;` (ej. `flex-grow: 1;`, `flex-grow: 0;`).
      * Por defecto, `flex-grow: 0`, lo que significa que el ítem no crecerá más allá de su `flex-basis` o su tamaño de contenido.
      * Si se establece `flex-grow: 1` a un ítem, este crecerá para ocupar el espacio restante, mientras que otros ítems con `flex-grow: 0` mantendrán su tamaño base.
      * Actúa cuando la suma de los espacios de los ítems hijos no supera el 100% del contenedor padre.

#### `flex-shrink`

Define el factor de decrecimiento de un ítem flexible en relación con los demás ítems, en caso de que el espacio disponible en el contenedor sea insuficiente y los ítems necesiten encogerse.

  * **Sintaxis:** `flex-shrink: <número>;` (ej. `flex-shrink: 1;`, `flex-shrink: 0;`).
      * Por defecto, `flex-shrink: 1`, lo que permite que el ítem se encoja.
      * Si `flex-shrink: 0`, el ítem no se encogerá por debajo de su `flex-basis` o tamaño de contenido.
      * Actúa en situaciones donde hay un `flex-basis` definido y los ítems no cubren el tamaño total del contenedor flex padre.

-----

### 5\. `z-index` (Apilamiento)

La propiedad `z-index` establece el nivel de profundidad en el que un elemento está apilado sobre los demás cuando hay elementos superpuestos. Permite que un elemento se coloque visualmente encima o debajo de otro.

  * **Valores:** Se le asigna un número entero (positivo o negativo). Los elementos con un número más alto estarán por encima de los elementos con un número más bajo.
  * **Funcionamiento:** `z-index` **solo tiene efecto en elementos posicionados** (es decir, aquellos con `position` diferente de `static`, como `relative`, `absolute`, `fixed` o `sticky`). No funciona con elementos que tienen `position: static;`.

**Ejemplo:**

```css
/* Un elemento con z-index alto estará encima */
.elemento-superior {
  position: relative; /* O absolute, fixed, sticky */
  z-index: 10;
}

/* Un elemento con z-index bajo estará debajo */
.elemento-inferior {
  position: relative;
  z-index: 5;
}
```

-----

## 📝 Clase 23: Posicionamiento Grid - Capítulo 1

Aqui introducimos el sistema de maquetación CSS Grid, un método moderno para organizar elementos en dos dimensiones, comparándolo con Flexbox y los sistemas de grid tradicionales. Cubre los conceptos fundamentales de Grid, cómo definir la estructura de la cuadrícula con `grid-template-columns` y `grid-template-rows`, el uso de unidades como `fr` y la función `repeat()`, la propiedad `gap` para espaciado, `order` para el orden de los ítems, y la definición de áreas con `grid-template-areas`.

-----

### 1\. Introducción a Display Grid

Grid CSS es un sistema de maquetación más potente que Flexbox, ya que está diseñado para estructuras en dos dimensiones (filas y columnas), a diferencia de Flexbox que se orienta a una sola dimensión. Grid toma la filosofía y muchos de los conceptos de Flexbox.

#### Elementos Fundamentales de Grid

  * **Contenedor (Grid Container)**: El elemento padre que define la cuadrícula o rejilla.
  * **Ítem (Grid Item)**: Cada uno de los elementos hijos dentro del contenedor Grid.
  * **Celda (Grid Cell)**: La unidad mínima de la cuadrícula, cada uno de los cuadritos.
  * **Área (Grid Area)**: Una región o conjunto de celdas dentro de la cuadrícula.
  * **Banda (Grid Track)**: Una banda horizontal o vertical de celdas de la cuadrícula.
  * **Línea (Grid Line)**: El separador horizontal o vertical de las celdas de la cuadrícula.

**Ejemplo de Estructura Grid:**

```html
<div class="grid"> 
    <div class="item item-1">Item 1</div> 
    <div class="item item-2">Item 2</div>
    <div class="item item-3">Item 3</div>
    <div class="item item-4">Item 4</div>
</div>
```

-----

### 2\. `Grid Template Columns` y `Grid Template Rows`

Estas propiedades son la forma principal de definir explícitamente el tamaño de las filas y columnas de una cuadrícula en CSS Grid. Al usar `display: grid;` en un contenedor, estas propiedades permiten establecer las dimensiones de la rejilla.

  * **`grid-template-columns`**: Establece el tamaño (`SIZE`) de cada columna.
  * **`grid-template-rows`**: Establece el tamaño (`SIZE`) de cada fila.

**Sintaxis y Comportamiento:**

```css
.grid {
  display: grid;
  grid-template-columns: 50px 300px; /* Define dos columnas: una de 50px y otra de 300px */
  grid-template-rows: 200px 75px;    /* Define dos filas: una de 200px y otra de 75px */
}
```

Este ejemplo crea una cuadrícula de 4 celdas en total (2 columnas x 2 filas). Es importante que el número de elementos hijos en el HTML se corresponda con la estructura definida. Si hay más ítems de los indicados, los restantes se incluirán sin formato. Si hay menos, solo se ocuparán los ítems implicados. Se pueden utilizar unidades relativas y absolutas.

-----

### 3\. `Fr` y `Repeat`

#### Unidad `fr` (Fracción Restante)

La unidad `fr` (fracción restante) es una unidad especial de Grid que permite distribuir el espacio restante en el contenedor de forma proporcional entre las columnas o filas. Es muy útil para diseños flexibles.

**Ejemplo de `fr`:**

```css
.grid {
  display: grid;
  grid-template-columns: 1fr 1fr; /* Dos columnas de igual ancho (ocupan la mitad del espacio restante cada una) */
  grid-template-rows: 2fr 1fr;    /* Dos filas: la primera ocupa el doble que la segunda */
}
```

Se pueden combinar diferentes unidades (píxeles, porcentajes, `auto`, `fr`) en las propiedades `grid-template-columns` y `grid-template-rows`.

#### Función `repeat()`

La función `repeat()` se utiliza para evitar la repetición de valores en `grid-template-columns` y `grid-template-rows` cuando se necesitan varias columnas o filas del mismo tamaño.

**Sintaxis:** `repeat(cantidad, tamaño)`

**Ejemplo de `repeat()`:**

```css
.grid {
  display: grid;
  grid-template-columns: 100px repeat(4, 50px) 200px; /* Una columna de 100px, 4 de 50px, y una de 200px */
  grid-template-rows: repeat(2, 1fr 2fr);           /* Se repite el patrón 1fr 2fr dos veces */
}
/* Esto es equivalente a: */
/* grid-template-columns: 100px 50px 50px 50px 50px 200px; */
/* grid-template-rows: 1fr 2fr 1fr 2fr; */
```

#### Función `minmax()`

La función `minmax(min, max)` establece un rango de tamaño para una pista (columna o fila). La pista tendrá el tamaño `max`, a menos que el contenedor se redimensione, en cuyo caso el tamaño de la pista podrá disminuir hasta `min`.

**Ejemplo de `minmax()`:**

```css
.container {
  display: grid;
  grid-template-columns: repeat(2, minmax(400px, 600px)); /* Dos columnas que serán entre 400px y 600px */
  grid-template-rows: repeat(2, 1fr);
  gap: 5px;
}
```

-----

### 4\. Propiedad `gap`

La propiedad `gap` (o sus variantes `column-gap` y `row-gap`) permite definir el espacio (huecos o gutters) entre las celdas de la cuadrícula. Esto es una alternativa más apropiada que usar `margin` en los ítems para crear separación.

  * **`column-gap`**: Establece el tamaño de los huecos entre columnas (líneas verticales).
  * **`row-gap`**: Establece el tamaño de los huecos entre filas (líneas horizontales).
  * **`gap`**: Es una propiedad abreviada para establecer `row-gap` y `column-gap` al mismo tiempo.

**Sintaxis:**

```css
.grid {
  column-gap: 100px; /* 100px de espacio entre columnas */
  row-gap: 10px;     /* 10px de espacio entre filas */
}
/* O la versión shorthand: */
/* .grid { gap: 10px 100px; } /* gap: row-gap column-gap */
/* .grid { gap: 10px; }     /* mismo gap para filas y columnas */
```

-----

### 5\. Propiedad `order`

La propiedad `order` en Grid CSS funciona de manera idéntica a como lo hace en Flexbox. Permite modificar el orden visual de los ítems dentro del contenedor Grid, independientemente de su orden en el código HTML.

  * Por defecto, todos los ítems tienen un `order` de `0`.
  * Los ítems con un valor `order` más pequeño se colocarán antes, y los que tienen un valor más alto se colocarán después (se admiten números negativos).

**Sintaxis:**

```css
.item-1 {
  order: 2;
}
.item-2 {
  order: 1; /* Este ítem aparecerá antes que item-1 */
}
```

-----

### 6\. Áreas (Grid Template Areas)

Grid por áreas permite nombrar y posicionar áreas específicas dentro de la cuadrícula, haciendo el diseño más legible y flexible. No es una alternativa a los grids explícitos (definidos por filas y columnas), sino que pueden trabajar conjuntamente.

  * **`grid-template-areas`**: Se usa en el **contenedor padre** para indicar la disposición de las áreas en el grid. Cada texto entre comillas simboliza una fila, y los nombres separados por espacios dentro de las comillas representan las columnas de esa fila.
  * **`grid-area`**: Se usa en cada **ítem hijo** para indicar a qué área pertenece.

**Sintaxis y Ejemplo:**

```html
<div class="container">
  <div class="item item-1"></div> <div class="item item-2"></div> <div class="item item-3"></div> <div class="item item-4"></div> </div>
```

```css
.container {
  display: grid;
  grid-template-areas: 
    "head head"  /* Primera fila: dos columnas ocupadas por el área 'head' */
    "menu main"  /* Segunda fila: 'menu' en la primera columna, 'main' en la segunda */
    "foot foot"; /* Tercera fila: dos columnas ocupadas por el área 'foot' */
}

.item-1 { grid-area: head; }
.item-2 { grid-area: menu; }
.item-3 { grid-area: main; }
.item-4 { grid-area: foot; }
```

**Valores para `grid-template-areas`:**

  * `"nombre_area"`: Crea una fila con una columna que ocupa el área indicada.
  * `"nombre1 nombre2"`: Crea una fila con dos columnas, cada una con un área diferente.
  * `"nombre nombre"`: Crea una fila donde un área ocupa múltiples columnas.
  * `.`: Indica una celda sin nombre (nula) en esa posición.

-----