## CSS Clase 03: Tipos de Etiqueta y CSS del Navegador

### 🧱 Etiquetas de bloque

| Etiqueta / Elemento       | Uso / Explicación                                                      |
| ------------------------- | ---------------------------------------------------------------------- |
| `<div>`                   | Contenedor genérico de bloque. No aporta semántica.                    |
| `<p>`                     | Párrafo de texto.                                                      |
| `<h1>` a `<h6>`           | Encabezados jerárquicos. `<h1>` es el más importante, `<h6>` el menos. |
| `<ul>` / `<ol>`           | Listas no ordenadas / ordenadas.                                       |
| `<li>`                    | Ítem de lista dentro de `<ul>` o `<ol>`.                               |
| `<section>` / `<article>` | Secciones semánticas de contenido.                                     |
| `<blockquote>`            | Cita en bloque, para destacar citas largas.                            |
| `<fieldset>`              | Agrupa controles dentro de un formulario.                              |
| `<form>`                  | Define un formulario interactivo.                                      |
| `<thead>`                 | Sección de encabezado de una tabla.                                    |
| `<tbody>`                 | Sección de cuerpo de una tabla.                                        |
| `<tfoot>`                 | Sección de pie de una tabla.                                           |
| `<tr>`                    | Fila de una tabla.                                                     |
| `<td>`                    | Celda de datos en una tabla.                                           |
| `<th>`                    | Celda de encabezado en una tabla.                                      |

Las etiquetas de **bloque** ocupan todo el ancho disponible y comienzan en una nueva línea.

---

### 📍 Etiquetas en línea

| Etiqueta / Elemento   | Uso / Explicación                                    |
| --------------------- | ---------------------------------------------------- |
| `<span>`              | Contenedor genérico en línea. No aporta semántica.   |
| `<a>`                 | Enlace.                                              |
| `<strong>` / `<b>`    | Texto importante / en negrita (sin semántica).       |
| `<em>` / `<i>`        | Texto enfatizado / en cursiva (sin semántica).       |
| `<img>`               | Imagen en línea.                                     |
| `<input>` / `<label>` | Elementos de formularios que se renderizan en línea. |
| `<textarea>`          | Área de texto multilínea para formularios.           |
| `<br>`                | Salto de línea.                                      |

Las etiquetas **en línea** sólo ocupan el espacio necesario y no fuerzan salto de línea.

---

### 🔍 Inspector de elementos

El **Inspector de Elementos** es una herramienta clave para desarrolladores:

* Permite inspeccionar el DOM y los estilos CSS aplicados.
* Puedes modificar los estilos en tiempo real.
* Disponible en la mayoría de navegadores (F12 o clic derecho > "Inspeccionar").

Paneles útiles:

* **Elementos**: muestra la estructura HTML (DOM).
* **Estilos**: muestra las reglas CSS aplicadas.
* **Consola / Red / Rendimiento**: herramientas de depuración y análisis.

---

### 🌐 Navegadores y motores de renderizado

* Cada navegador tiene un **motor de render** diferente:

  * Chrome / Edge: **Blink**
  * Firefox: **Gecko**
  * Safari: **WebKit**

* Los motores de render interpretan el HTML/CSS y lo convierten en lo que vemos.

* No todos los motores soportan del mismo modo las nuevas propiedades CSS.

📌 **Prefijos de navegador** permiten dar compatibilidad a propiedades nuevas:

```css
.example {
  -webkit-border-radius: 10px; /* Safari, Chrome */
  -moz-border-radius: 10px;    /* Firefox */
  border-radius: 10px;         /* estándar */
}
```

---

### 🧾 CSS por defecto y Normalización

Todos los navegadores aplican una hoja de estilos **por defecto** (user-agent stylesheet), lo que puede generar diferencias visuales no deseadas.

🛠️ **Soluciones:**

#### 1. Normalize.css

* Ajusta sólo las inconsistencias entre navegadores.
* Preserva los estilos útiles por defecto.
* Ideal para proyectos modernos con semántica.

🔗 [https://github.com/necolas/normalize.css](https://github.com/necolas/normalize.css)

#### 2. Reset.css

* Elimina todos los estilos por defecto.
* Tienes que aplicar tú todos los estilos desde cero.
* Enfoque más "agresivo".

🔗 [https://meyerweb.com/eric/tools/css/reset/](https://meyerweb.com/eric/tools/css/reset/)

---

### ✅ Recomendación
> En proyectos modernos, se recomienda **Normalize.css** por mantener mayor control y accesibilidad sin partir de cero.
