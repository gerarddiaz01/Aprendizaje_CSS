## CSS - Selectores Completos

CSS permite aplicar estilos de forma selectiva a elementos HTML mediante **selectores**. Aquí tienes una síntesis clara, organizada por tipo de selector, con explicaciones, ejemplos y estructura visual pensada para facilitar el aprendizaje.

---

### 🟦 1. Selectores Básicos

| Selector   | Uso / Explicación                  | Ejemplo CSS                   | Resultado HTML                        |
| ---------- | ---------------------------------- | ----------------------------- | ------------------------------------- |
| `*`        | Selector universal. Afecta a todo. | `* { margin: 0; }`            | Aplica margen 0 a todos los elementos |
| `elemento` | Selector de tipo (etiqueta HTML)   | `p { color: red; }`           | `<p>Texto</p>` será rojo              |
| `.clase`   | Selecciona elementos con una clase | `.rojo { color: red; }`       | `<p class="rojo">Texto</p>`           |
| `#id`      | Selecciona un elemento por su ID   | `#titulo { font-size: 2em; }` | `<h1 id="titulo">Hola</h1>`           |

---

### 🟩 2. Selectores Combinadores

| Selector | Explicación                           | Ejemplo CSS                     | HTML que lo activa          |
| -------- | ------------------------------------- | ------------------------------- | --------------------------- |
| `A B`    | Selector descendiente (B dentro de A) | `div p { color: blue; }`        | `<div><p>Hola</p></div>`    |
| `A > B`  | Selector de hijo directo              | `ul > li { list-style: none; }` | `<ul><li>Item</li></ul>`    |
| `A + B`  | Selector de hermano adyacente         | `h1 + p { color: green; }`      | `<h1></h1><p>Texto</p>`     |
| `A ~ B`  | Selector de hermanos generales        | `h1 ~ p { font-weight: bold; }` | `<h1></h1><p>1</p><p>2</p>` |

📌 **Nota:** Combinadores permiten estilizar según relaciones entre elementos.

---

### 🟨 3. Selectores de Atributo

| Selector           | Uso                        | Ejemplo CSS                            | HTML relevante                |
| ------------------ | -------------------------- | -------------------------------------- | ----------------------------- |
| `[attr]`           | Elementos con ese atributo | `[required] { border: red; }`          | `<input required>`            |
| `[attr="valor"]`   | Con valor exacto           | `[type="email"] { color: blue; }`      | `<input type="email">`        |
| `[attr^="inicio"]` | Valor que empieza con...   | `[href^="https"] { color: green; }`    | `<a href="https://...">`      |
| `[attr$="fin"]`    | Valor que termina con...   | `[src$=".png"] { border: 1px solid; }` | `<img src="logo.png">`        |
| `[attr*="parte"]`  | Contiene esa parte         | `[class*="error"] { color: red; }`     | `<div class="mensaje-error">` |

---

### 🟧 4. Selectores de Pseudo-clases

| Selector         | Explicación                   | Ejemplo CSS                            |
| ---------------- | ----------------------------- | -------------------------------------- |
| `:hover`         | Al pasar el cursor            | `a:hover { text-decoration: none; }`   |
| `:first-child`   | Primer hijo de su padre       | `p:first-child { font-weight: bold; }` |
| `:last-child`    | Último hijo de su padre       | `li:last-child { color: blue; }`       |
| `:nth-child(n)`  | Elemento hijo n (o patrón)    | `li:nth-child(2n) { color: gray; }`    |
| `:not(selector)` | Excluye elementos             | `p:not(.rojo) { color: black; }`       |
| `:focus`         | Cuando un input está enfocado | `input:focus { border: blue; }`        |

📌 Muy útiles para interacción y reglas dinámicas.

---

### 🟥 5. Selectores de Pseudo-elementos

| Selector         | Explicación                          | Ejemplo CSS                           |
| ---------------- | ------------------------------------ | ------------------------------------- |
| `::before`       | Inserta contenido antes del elemento | `h1::before { content: "★ "; }`       |
| `::after`        | Inserta contenido después            | `h1::after { content: " ✨"; }`        |
| `::first-letter` | Afecta solo la primera letra         | `p::first-letter { font-size: 2em; }` |
| `::first-line`   | Afecta solo la primera línea         | `p::first-line { color: blue; }`      |

---

### 🧠 Ejemplo práctico combinando selectores

```html
<style>
  ul li:first-child { color: green; }
  ul li:last-child { font-weight: bold; }
  ul li:nth-child(2n) { background-color: #eee; }
</style>

<ul>
  <li>Item 1</li>
  <li>Item 2</li>
  <li>Item 3</li>
  <li>Item 4</li>
</ul>
```

---

### 📌 Buenas prácticas

* No uses IDs si vas a reutilizar reglas: mejor clases.
* Evita la sobreespecificidad (demasiados selectores encadenados).
* Usa pseudoclases para mejorar la accesibilidad y experiencia de usuario.
* Pseudoelementos ayudan a decorar sin modificar HTML.

Este resumen cubre todos los selectores que aparecen en los 4 módulos PDF (Clases 5 a 8). Ya puedes usar selectores básicos, combinados, avanzados, de atributo y pseudo para estilizar con potencia y precisión.
