## 🎯 CSS – Unidades de Medida

En CSS, las unidades de medida permiten definir el tamaño de elementos como el ancho, alto, márgenes, padding, fuente, etc. Existen diferentes tipos según su naturaleza: absolutas, relativas, del viewport y funciones matemáticas. Añado sólo los que Bienvenido nos ha indicado que son los más usado y que él personalmente cree que vamos a utilizar todo el tiempo.

---

### 📏 Unidades absolutas

| Unidad           | Uso / Explicación                                            | Ejemplo            |
| ---------------- | ------------------------------------------------------------ | ------------------ |
| `px`             | Píxeles. Unidad más utilizada en pantalla. No escalable.     | `width: 200px;`    |
| `pt`             | Puntos tipográficos. Usado en impresión.                     | `font-size: 12pt;` |

✅ **Ventaja:** son predecibles.
⚠️ **Desventaja:** no se adaptan a pantallas o zoom del usuario.

---

### 📐 Unidades relativas

| Unidad | Basada en                           | Uso / Explicación                     | Ejemplo              |
| ------ | ----------------------------------- | ------------------------------------- | -------------------- |
| `%`    | Elemento padre                      | Ideal para layouts fluidos.           | `width: 50%;`        |
| `em`   | Fuente del elemento                 | Escala respecto al `font-size` local. | `font-size: 2em;`    |
| `rem`  | Fuente del elemento raíz (`<html>`) | Más predecible que `em`.              | `font-size: 1.5rem;` |

---

### # Unidades de medida en CSS: em, rem y %
- em: 
El tamaño en em se basa en el tamaño de fuente del elemento padre inmediato. Por ejemplo, si el padre tiene font-size: 20px y el hijo tiene font-size: 2em, el hijo tendrá 40px.

- rem: 
El tamaño en rem se basa en el tamaño de fuente del elemento raíz (root element), que es siempre el elemento <html>. Por ejemplo, si en CSS tienes html { font-size: 16px; } y un elemento tiene font-size: 2rem, ese elemento tendrá 32px, sin importar el tamaño de fuente de sus padres.

- %: 
El porcentaje en font-size también se basa en el tamaño de fuente del elemento padre inmediato. Por ejemplo, si el padre tiene font-size: 20px y el hijo tiene font-size: 150%, el hijo tendrá 30px.

A continuación tienes un ejemplo visual para entender cómo funcionan `em`, `rem` y `%` en el tamaño de fuente (`font-size`). Es mejor poner el style en un archivo a parte pero era más fácil ponerlo en el html para el ejemplo.

```html
<!DOCTYPE html>
<html>
<head>
  <style>
    html {
      font-size: 16px;
    }
    body {
      font-size: 1.5em; /* 16px * 1.5 = 24px */
    }
    .em-example {
      font-size: 2em; /* 24px * 2 = 48px (relativo a body) */
    }
    .rem-example {
      font-size: 2rem; /* 16px * 2 = 32px (relativo a html) */
    }
    .percent-example {
      font-size: 150%; /* 24px * 1.5 = 36px (relativo a body) */
    }
  </style>
</head>
<body>
  <p>Este es el tamaño base del <b>body</b> (1.5em = 24px).</p>
  <p class="em-example">Este texto usa <b>2em</b> (48px, relativo a body).</p>
  <p class="rem-example">Este texto usa <b>2rem</b> (32px, relativo a html).</p>
  <p class="percent-example">Este texto usa <b>150%</b> (36px, relativo a body).</p>
</body>
</html>
```

- **em**: relativo al tamaño de fuente del padre inmediato.
- **rem**: relativo al tamaño de fuente del elemento raíz (`html`).
- **%**: relativo al tamaño de fuente del padre inmediato.

Puedes copiar este código en un archivo `.html` y abrirlo en tu navegador para ver la diferencia visualmente.

---

### 🖥️ Unidades del viewport

| Unidad | Significado         | Explicación                                                    | Ejemplo            |
| ------ | ------------------- | -------------------------------------------------------------- | ------------------ |
| `vw`   | Viewport width      | 1vw = 1% del ancho de la ventana.                              | `width: 50vw;`     |
| `vh`   | Viewport height     | 1vh = 1% del alto de la ventana.                               | `height: 80vh;`    |
| `vmin` | Viewport mínimo     | % del lado más pequeño del viewport.                           | `width: 50vmin;`   |
| `vmax` | Viewport máximo     | % del lado más grande del viewport.                            | `width: 50vmax;`   |
| `vi`   | Viewport inline     | 1vi = 1% del tamaño del eje inline del viewport (horizontal en escritura LTR/RTL). | `width: 50vi;`     |
| `vb`   | Viewport block      | 1vb = 1% del tamaño del eje block del viewport (vertical en escritura LTR/RTL).     | `height: 50vb;`    |

📌 **Ideal para diseño responsive**. Permite adaptar el contenido a la pantalla sin media queries.
📌 **OJO** con la diferencia entre % y vh/vw, el % se usa para calcular el porcentaje de la ventana entera y el vh o vw se utiliza para calcular LO VISIBLE de la ventana, por ejemplo sin el scroll bar, cuidado, los márgenes (margin) del body por ejemplo influira en el tamaño final de lo que pongamos con vh y vw.

---

### 🧮 Funciones de cálculo

| Función  | Uso                                                | Ejemplo                     |
| -------- | -------------------------------------------------- | --------------------------- |
| `calc()` | Suma, resta, multiplicación o división de valores. | `width: calc(100% - 20px);` |
| `min()`  | Devuelve el menor de los valores dados.            | `width: min(90vw, 600px);`  |
| `max()`  | Devuelve el mayor de los valores dados.            | `width: max(300px, 50%);`   |

Estas funciones permiten crear diseños más adaptativos y expresivos sin depender de JavaScript.

---

### Ejemplo práctico de uso de `calc()` con diferentes unidades

```css
.caja-calc {
  width: calc(50% - 40px);
  height: 100px;
  background: #4fa3f7;
  color: white;
  display: flex;
  align-items: center;
  justify-content: center;
  margin: 20px;
  font-size: 1.2rem;
}
```

En este ejemplo de CSS, el ancho de la clase `.caja-calc` será el 50% del contenedor menos 40 píxeles. Puedes combinar %, px, em, rem, etc. dentro de `calc()` para lograr diseños flexibles y precisos.

---

### 🎨 Colores en CSS

| Método         | Sintaxis             | Ejemplo                             |
| -------------- | -------------------- | ----------------------------------- |
| Palabras clave | color por nombre     | `color: red;`                       |
| Hexadecimal    | `#rrggbb` o `#rgb`   | `color: #ff6600;`                   |
| RGB            | `rgb(r, g, b)`       | `color: rgb(255, 0, 0);`            |
| RGBA           | `rgba(r, g, b, a)`   | `color: rgba(0, 0, 0, 0.5);`        |
| HSL            | `hsl(h, s%, l%)`     | `color: hsl(120, 100%, 50%);`       |
| HSLA           | `hsla(h, s%, l%, a)` | `color: hsla(240, 100%, 50%, 0.3);` |
¿Qué atributos aceptan colores? `color`y `background-color`.

