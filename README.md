<style>html {scroll-behavior: smooth;}</style>
# **v-grid**

Framework CSS para la creación de layouts responsivos con Grid y Flexbox. Inspirado en Tailwind CSS.

### **Autor:** [Víctor Álvarez](https://vicventum.web.app)

> Demo en [v-grid](https://vicventum/github.io/v-grid.index.html)

---
## **Tabla de contenidos**
||
|- |
| [Optimización](#optimización) |
| [Responsive Design](#responsive-design) |
| [Utilidades Responsive](#utilidades-responsive) |
| [Display](#display) |
| [Espaciado](#espaciado) |
| [Propiedades Grid](#propiedades-grid) |
| [Propiedades Flex](#propiedades-flex) |
| [Alineamiento](#alineamiento) |
| [Tamaño](#tamaño) |
| [Configuraciones](#configuraciones) |

---

## **Optimización**

Debido a que la mayoría de las propiedades para crear layouts en CSS serán aplicadas como una sola clase para muchos elementos HTML, se ahorrarán muchas líneas de código CSS. 

Aún así, para una experiencia de desarrollo ágil, v-grid genera cientos de clases para la construcción de layouts, en donde al finalizar un proyecto notará que la mayoría no serán usadas. 

Por ello se recomienda usar v-grid junto a otra librería llamada [PurgeCSS](https://purgecss.com/), la cual eliminará todas las clases no usadas en la versión de producción del proyecto.

> **Nota:** Es por ello que hay que tener en cuenta que los elementos HTML generados dinámicamente es mejor que no se le agreguen clases de v-grid

Dando como resultado que la versión de producción de v-grid no pese más de **4KB** en la mayoría de los proyectos.

---

## **Responsive Design**

Usando la metodología mobile first, cada clase en v-grid se puede aplicar condicionalmente en diferentes puntos de interrupción, lo que hace fácil cambiar el layout para distintos tamaños de pantallas sin salir del HTML.

Hay 4 puntos de interrupción

| Prefijo de punto <br>de interrupción | Ancho mínimo | 
|-|-|
|m| 420px|
|t| 768px|
|l| 1024px|
|d| 1280px|

Para que una clase solo aplique sus estilos hasta cierto punto de interrupción solo se agrega el prefijo antes de la clase seguido del carácter "`:`". 

Por ejemplo, el siguiente `div` tendrá ancho completo en móviles, medirá la mitad en tablets, y una tercera parte a partir de laptops.

```html
<div class="w-full t:w-1/2 l:w-1/3"></div>
```

---

## **Utilidades Responsive**

Clases para crear layouts intrínsecamente responsive con Grid o Flexbox (da diferentes resultados cada uno).

> `$min-responsive-size` es una variable cuyo valor indica el tamaño mínimo que tendrán los elementos afectados por alguna de las clases **reponsives**

- **responsive-grid**:<br>

```scss
display: grid;
grid-template-columns: repeat(
  auto-fit,
  minmax(min($min-responsive-size, 100%), 1fr)
);
```

- **responsive-flex**:<br>

```scss
display: flex;
flex-wrap: wrap;
& > * {
  flex: 1 1 $min-responsive-size;
}
```

- **responsive-flex**:<br>

```scss
display: flex;
flex-wrap: wrap;
justify-content: center;

& > * {
  flex: 0 1 $min-responsive-size;
}
```

---

## **Display**

- **v-grid**:<br>
  ```css
  display: grid;
  ```
- **v-inline-grid**:<br>

  ```css
  display: inline-grid;
  ```

- **v-flex**:<br>
  ```css
  display: flex;
  ```
- **v-inline-flex**:<br>
  ```css
  display: inline-flex;
  ```
- **v-initial**:<br>
  ```css
  display: inline-initial;
  ```

---

## **Espaciado**
### **Gap's**

Siendo `n` un numero del 0 al 20 representando cada unidad `1rem`:

- **gap-`n`**:<br>
  `css gap: nrem `

  Ejemplo:

- **gap-1**:<br>
  ```css
  gap: 1rem;
  ```

También se puede usar mediadas intermedias para valores `n`,5:

- **gap-1,5**:<br>
  ```css
  gap: 1.5rem;
  ```

### **Espacio entre elementos**

Controla el espacio entre los hijos del elemento al que se le aplique la clase.

> Si bien estas clases se pueden usar para cualquier tipo de elementos, un bueno uso es para dar espaciados a hijos de elementos `flex`. Actualmente también se puede usar la propiedad `gap` para dar espaciado en `flex`, pero aún no es totalmente soportada por todos los navegador. Por lo que esta puede ser una buena solución en estos casos.

Funciona de manera horizontal

-  **col-space-`n`**
```scss
.col-space-n > * + * {
    --reverse: 0; 
    margin-right: calc(n * var(--reverse));
    margin-left: calc(n * calc(1 - var(--reverse)));
}
```

O vertical

-  **row-space-`n`**
```scss
.row-space-n > * + * {
    --reverse: 0; 
    margin-bottom: calc(n * var(--reverse));
    margin-top: calc(n * calc(1 - var(--reverse)));
}
```

En el caso de que se quiera colocar los valores por defecto

- **row-space-initial**

```scss
.row-space-initial > * + * {
    --y-initial: initial;
    --y-reverse-initial: 0;
    margin-top: var(--y-initial);
    margin-bottom: var(--y-reverse-initial);
}
```

- **col-space-initial**

```scss
.col-space-initial > * + * {
    --x-initial: initial;
    --x-reverse-initial: 0;
    margin-left: var(--x-initial);
    margin-right: var(--x-reverse-initial);
}
```

O el valor `auto` 
> Asemeja el resultado de `space-between` de elementos `flex` o `grid` sin ser uno

- **row-space-auto**

```scss
.row-space-auto > * + * {
    --y-auto: auto;
    --y-reverse-auto: 0;
    margin-top: var(--y-auto);
    margin-bottom: var(--y-reverse-auto);
}

```

- **col-space-auto**

```scss
.col-space-auto > * + * {
    --x-auto: auto;
    --x-reverse-auto: 0;
    margin-left: var(--x-auto);
    margin-right: var(--x-reverse-auto);
}
```

### **Invertir el orden de los elementos hijos**

- **space-reverse**

Si los elementos hijos están en orden inverso (por haber usado clases cómo `flex-row-reverse` o `flex-col-reverese` en el elemento padre), use las utilidades `space-reverse` para asegurarse de que el espacio se agregue al lado correcto del elemento de los elementos.

```css
.space-reverse > * + * {
    --reverse: 1;
    --x-initial: 0;
    --y-initial: 0;
    --x-reverse-initial: initial;
    --y-reverse-initial: initial;
    --x-auto: 0;
    --y-auto: 0;
    --x-reverse-auto: auto;
    --y-reverse-auto: auto;
}
```

---

## **Propiedades Grid**

### **grid-template-columns** | **grid-template-rows**

Siendo `n` un numero del 1 al 12 o `none`

- **grid-cols-`n`**: <br>

  ```css
  grid-template-columns: repeat(n, minmax(0, 1fr));
  ```

- **grid-rows-`n`**: <br>
  ```css
  grid-template-rows: repeat(n, minmax(0, 1fr));
  ```

---

### **grid-column** | **grid-row** (cantidad en `span`)

Siendo `n` un numero del 1 al 12

- **col-span-`n`**: <br>

  ```css
  grid-column: span n / span n;
  ```

- **row-span-`n`**: <br>
  ```css
  grid-row: span n / span n;
  ```

o auto:

- **col-auto**: <br>
  ```css
  grid-column: auto;
  ```
- **row-auto**: <br>
  ```css
  grid-row: auto;
  ```

---

### **grid-column-start** | **grid-row-start** || **grid-column-end** | **grid-row-end**

Siendo `n` un numero del 1 al 13

- **col-start-`n`**: <br>

  ```css
  grid-column-start: n;
  ```

- **row-start-`n`**: <br>

  ```css
  grid-column-start: n;
  ```

- **col-end-`n`**: <br>

  ```css
  grid-column-end: n;
  ```

- **row-end-`n`**: <br>
  ```css
  grid-column-end: n;
  ```

o auto:

- **col-start-auto**: <br>
  ```css
  grid-column-start: auto;
  ```
- **row-start-auto**: <br>
  ```css
  grid-row-start: auto;
  ```
- **col-end-auto**: <br>
  ```css
  grid-column-end: auto;
  ```
- **row-end-auto**: <br>
  ```css
  grid-row-end: auto;
  ```

o full:

- **col-full**: <br>
  ```css
  grid-column: 1 / -1;
  ```

---

### **grid-auto-flow**

- **grid-flow-row**:<br>
  ```css
  grid-auto-flow: row;
  ```
- **grid-flow-col**:<br>
  ```css
  grid-auto-flow: column;
  ```
- **grid-flow-row-dense**:<br>
  ```css
  grid-auto-flow: row dense;
  ```
- **grid-flow-row-dense**:<br>
  ```css
  grid-auto-flow: column dense;
  ```

---


## **Propiedades Flex**

### **flex-direction**

- **flex-row**:<br>
  ```css
  flex-direction: row;
  ```
- **flex-row-reverse**:<br>
  ```css
  flex-direction: row-reverse;
  ```
- **flex-col**:<br>
  ```css
  flex-direction: col;
  ```
- **flex-col-reverse**:<br>
  ```css
  flex-direction: col-reverse;
  ```

### **flex-wrap**

- **flex-wrap**:<br>
  ```css
  flex-wrap: wrap;
  ```
- **flex-wrap-reverse**:<br>
  ```css
  flex-wrap: wrap-reverse;
  ```
- **flex-nowrap**:<br>
  ```css
  flex-wrap: nowrap;
  ```

### **flex**

- **flex-1**:<br>
  ```css
  flex: 1 1 0%;
  ```
- **flex-auto**:<br>
  ```css
  flex: 1 1 auto;
  ```
- **flex-initial**:<br>
  ```css
  flex: 0 1 initial;
  ```
- **flex-none**:<br>
  ```css
  flex: none;
  ```

### **flex-grow**

- **flex-grow**:<br>
  ```css
  flex-grow: 1;
  ```
- **flex-grow-0**:<br>
  ```css
  flex-grow: 0;
  ```

### **flex-shrink**

- **flex-shrink**:<br>
  ```css
  flex-shrink: 1;
  ```
- **flex-shrink-0**:<br>
  ```css
  flex-shrink: 0;
  ```

### **order**

Siendo `n` un numero del 1 al 12

- **order-`n`**: <br>
  ```css
  order: n;
  ```

O valores específicos:

- **order-first**: <br>
  ```css
  order: -9999;
  ```
- **order-last**: <br>
  ```css
  order: 9999;
  ```
- **order-none**: <br>
  ```css
  order: none;
  ```


---

## **Alineamiento**

### **text-align**

Alinea texto. Siendo `align` algunos de estos valores: (`left | right | center`)

- **text-`align`:**
  ```css
  text-align: align;
  ```

### **block-center**

Centra un elemento de bloque usando `margin-left: auto` y `margin-right: auto`

- **block-center:**
  ```css
  margin-left: auto;
  margin-right: auto;
  ```

---

### **justify-items | align-items | justify-self | align-self**

Siendo `align` algunos de estos valores: (`start | flex-start | end | flex-end | center | stretch`)

> `j-self-flex-start` y `j-self-flex-end` no existen debido a que las propiedades `justify-self: flex-start` y `justify-self: flex-end` no existen para un contenedor padre `flex`.

- **j-items-`align`**: <br>
  ```css
  justify-items: align;
  ```
- **a-items-`align`**: <br>
  ```css
  align-items: align;
  ```
- **j-self-`align`**: <br>
  ```css
  justify-self: align;
  ```
- **a-self-`align`**: <br>
  ```css
  align-self: align;
  ```

para `align-items` también está el valor `baseline`:

- **a-items-`align`**: <br>
  ```css
  align-items: baseline;
  ```

---

### **justify-content | align-content**

Siendo `align` algunos de estos valores: (`start | flex-start | end | flex-end | center | stretch | space-around | space-between | space-evenly`)

- **j-content-`align`**: <br>
  ```css
  justify-content: align;
  ```
- **a-content-`align`**: <br>
  ```css
  align-content: align;
  ```

---

---

## **Tamaño**

### **width**

Usados idóneamente para los flex-items

| 0, 2, 3                              | 4                             | 5                             | 6                                    | 12                                     |
| ------------------------------------ | ----------------------------- | ----------------------------- | ------------------------------------ | -------------------------------------- |
| **w-0**: <br> `width: 0`             | **w-1/4**:<br> `width: 25%;` | **w-1/5**:<br> `width: 20%;` | **w-1/6**:<br> `width: 16.666667%;` | **w-1/12**:<br> `width: 8.333333%;`   |
| **w-1/2**:<br> `width: 50%;`        | **w-2/4**:<br> `width: 50%;` | **w-2/5**:<br> `width: 40%;` | **w-2/6**:<br> `width: 33.333333%;` | **w-2/12**:<br> `width: 16.666667%;`  |
| **w-1/3**:<br> `width: 33.333333%;` | **w-3/4**:<br> `width: 75%;` | **w-3/5**:<br> `width: 60%;` | **w-3/6**:<br> `width: 50%;`        | **w-3/12**:<br> `width: 25%;`         |
| **w-2/3**:<br> `width: 66.666667%;` |                               | **w-4/5**:<br> `width: 80%;` | **w-4/6**:<br> `width: 66.666667%;` | **w-4/12**:<br> `width: 33.333333%;`  |
|                                      |                               |                               | **w-5/6**:<br> `width: 83.333333%;` | **w-5/12**:<br> `width: 41.666667%;`  |
|                                      |                               |                               |                                      | **w-6/12**:<br> `width: 50%;`         |
|                                      |                               |                               |                                      | **w-7/12**:<br> `width: 58.333333%;`  |
|                                      |                               |                               |                                      | **w-8/12**:<br> `width: 66.666667%;`  |
|                                      |                               |                               |                                      | **w-9/12**:<br> `width: 75%;`         |
|                                      |                               |                               |                                      | **w-10/12**:<br> `width: 83.333333%;` |
|                                      |                               |                               |                                      | **w-11/12**:<br> `width: 91.666667%;` |

### Otros tipos de tamaño:

| **width**                          | **height**                          |
| ---------------------------------- | ----------------------------------- |
| **.w-0**:<br> `width: 0;`    | **h-0**: <br> `height: 0`           |
| **.w-auto**:<br> `width: auto;`    | **.h-auto**:<br> `height: auto;`    |
| **.w-full**:<br> `width: 100%;` | **.h-full**:<br> `height: 100%;`    |
| **.w-screen**:<br> `width: 100vw;` | **.h-screen**:<br> `height: 100vw;` |

---

## **Configuraciones**

- **Breakpoints**

```scss
$breakpoints: (
  '': 0,
  m: 420px,
  t: 768px,
  l: 1024px,
  d: 1280px,
) !default;
```

- **Variables**

```scss
$max-cols: 12;
```

```scss
$min-responsive-size: 250px;
```
