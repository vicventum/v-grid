# **v-grid**
### Sistema de grillas super ligero y para crear layouts basado en Grid CSS y Flexbox, hecho en Sass.
### **Autor:** Víctor Álvarez

>Ejemplo de uso en index.html

---
## **Clases**
---

## **v-grid**
### **Display**

* **v-grid**:<br> `display: grid;`
* ****v-inline-grid****:<br> `display: inline-grid;`

* **v-flex**:<br> `display: flex;`
* ****v-inline-flex****:<br> `display: inline-flex;`

### **Gap's**
Siendo `n` un numero del 0 al 5  representando cada unidad `1rem`:
* **gap-`n`**:<br> `gap: `n`rem`

Ejemplo:
* **gap-1**:<br> `gap: 1rem`

También se puede usar mediadas entremedias para valores `n`,5:

* **gap-1,5**:<br> `gap: 1.5rem`

### **grid-template-columns** | **grid-template-rows**
Siendo `n` un numero del 1 al 12 o `none`
* **grid-cols-`n`**: <br> 	`grid-template-columns: repeat(`*n*`, minmax(0, 1fr));`

* **grid-rows-`n`**: <br> 	`grid-template-rows: repeat(`*n*`, minmax(0, 1fr));`

### **grid-column** | **grid-row** (catidad en `span`)
Siendo `n` un numero del 1 al 12
* **col-span-`n`**: <br> 	`grid-column: span `n ` / span ` n`;`

* **row-span-`n`**: <br> 	`grid-row: span `n ` / span ` n`;`

o auto: 
* **col-auto**: <br> 	`grid-column: auto;`
* **row-auto**: <br> 	`grid-row: auto;`


### **grid-column-start** | **grid-row-start** || **grid-column-end** | **grid-row-end**
Siendo `n` un numero del 1 al 13
* **col-start-`n`**: <br> 		`grid-column-start: `n`;`

* **row-start-`n`**: <br> 		`grid-column-start: `n`;`

* **col-end-`n`**: <br> 		`grid-column-end: `n`;`

* **row-end-`n`**: <br> 		`grid-column-end: `n`;`

o auto: 
* **col-start-auto**: <br> 	`grid-column-start: auto;`
* **row-start-auto**: <br> 	`grid-row-start: auto;`
* **col-end-auto**: <br> 	`grid-column-end: auto;`
* **row-end-auto**: <br> 	`grid-row-end: auto;`

### **grid-auto-flow**
* **grid-flow-row**:<br> `grid-auto-flow: row;`
* **grid-flow-col**:<br> `grid-auto-flow: column;`
* **grid-flow-row-dense**:<br> `grid-auto-flow: row dense;`
* **grid-flow-row-dense**:<br> `grid-auto-flow: column dense;`


---
## **v-flex**

### **flex-direction**
* **flex-row**:<br> `flex-direction: row;`
* **flex-row-reverse**:<br> `flex-direction: row-reverse;`
* **flex-col**:<br> `flex-direction: col;`
* **flex-col-reverse**:<br> `flex-direction: col-reverse;`
  
### **flex-wrap**
* **flex-wrap**:<br> `flex-wrap: wrap;`
* **flex-wrap-reverse**:<br> `flex-wrap: wrap-reverse;`
* **flex-nowrap**:<br> `flex-wrap: nowrap;`
  
### **flex-wrap**
* **flex-1**:<br> `flex: 1 1 0%;`
* **flex-auto**:<br> `flex: 1 1 auto;`
* **flex-initial**:<br> `flex: 0 1 initial;`
* **flex-none**:<br> `flex: none;`
  
### **flex-grow**
* **flex-grow**:<br> `flex-grow: 1;`
* **flex-grow-0**:<br> `flex-grow: 0;`
  
### **flex-shrink**
* **flex-shrink**:<br> `flex-shrink: 1;`
* **flex-shrink-0**:<br> `flex-shrink: 0;`


### **order**
Siendo `n` un numero del 1 al 12
* **order-`n`**: <br> 	`order: `n`;`

O valores específicos: 
* **order-first**: <br> 	`order: -9999`
* **order-last**: <br> 	`order: 9999`
* **order-none**: <br> 	`order: none`

---

## **Alineamiento**
### **justify-items | align-items | justify-self | align-self**
Siendo `n` un algunos de estos valores: (`start | end | center | stretch`)
* **j-items-`n`**: <br> `justify-items: `n`;`
* **a-items-`n`**: <br> `align-items: `n`;`
* **j-self-`n`**: <br> `justify-self: `n`;`
* **a-self-`n`**: <br> `align-self: `n`;`


### **justify-content | align-content**
Siendo `n` un algunos de estos valores: (`start | end | center | stretch | space-around | space-between | space-evenlystart | end | center | stretch`)
* **j-content-`n`**: <br> `justify-content: `n`;`
* **a-content-`n`**: <br> `align-content: `n`;`

## **Tamaño**
### **width**
Usados idóneamente para los flex-items 

<div style="display: flex; margin: 0">
<div>

* **w-0**: <br> `width: 0`
* **.w-1/2**:<br> `width: 50%;`
* **.w-1/3**:<br> `width: 33.333333%;`
* **.w-2/3**:<br> `width: 66.666667%;`
* **.w-1/4**:<br> `width: 25%;`
* **.w-2/4**:<br> `width: 50%;`
</div>
<div>

* **.w-3/4**:<br> `width: 75%;`
* **.w-1/5**:<br> `width: 20%;`
* **.w-2/5**:<br> `width: 40%;`
* **.w-3/5**:<br> `width: 60%;`
* **.w-4/5**:<br> `width: 80%;`
* **.w-1/6**:<br> `width: 16.666667%;`
* **.w-2/6**:<br> `width: 33.333333%;`

</div>
<div>

* **.w-3/6**:<br> `width: 50%;`
* **.w-4/6**:<br> `width: 66.666667%;`
* **.w-5/6**:<br> `width: 83.333333%;`
* **.w-1/12**:<br> `width: 8.333333%;`
* **.w-2/12**:<br> `width: 16.666667%;`
* **.w-3/12**:<br> `width: 25%;`

</div>
<div>

* **.w-4/12**:<br> `width: 33.333333%;`
* **.w-5/12**:<br> `width: 41.666667%;`
* **.w-6/12**:<br> `width: 50%;`
* **.w-7/12**:<br> `width: 58.333333%;`
* **.w-8/12**:<br> `width: 66.666667%;`
* **.w-9/12**:<br> `width: 75%;`
* **.w-10/12**:<br> `width: 83.333333%;`
* **.w-11/12**:<br> `width: 91.666667%;`
  
</div>
</div>

Otros tipos de tamaño:
* **.w-auto**:<br> `width: auto;`
* **.w-full**:<br> `width: 100%;`
* **.w-screen**:<br> `width: 100vw;`

### **height**
* **h-0**: <br> `height: 0`
* **.h-auto**:<br> `height: auto;`
* **.h-full**:<br> `height: 100%;`
* **.h-screen**:<br> `height: 100vw;`

## **Configuraciones**
* **Breakpoints**
  
        $breakpoints: (
            '': 0,
            m: 640px,
            t: 768px,
            l: 1024px,
            d: 1280px
        ) !default;

* **Vars**

        $max-cols: 12;
