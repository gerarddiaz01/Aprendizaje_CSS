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