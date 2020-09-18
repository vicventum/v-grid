# **v-grid**
### Sistema de grillas super ligero para crear layouts basado en Grid CSS y Flexbox, hecho en Sass.
### **Autor:** Víctor Álvarez

>Ejemplo de uso en index.html

---
## **Clases**

### **Display**

* **v-grid**:<br> 
    ```css
    display: grid;
    ```
* ****v-inline-grid****:<br> 
    ```css
    display: inline-grid;
    ```

* **v-flex**:<br> 
    ```css
    display: flex;
    ```
* ****v-inline-flex****:<br> 
    ```css
    display: inline-flex;
    ```

---
### **Responsive**
Crea layout responsive con grid o flexbox
> `$min-size-responsive` es una variable cuyo valor indica el tamaño mínimo que tendrán los elementos afectados por alguna de las clases **reponsives**

* **responsive-grid**:<br> 
```scss
display: grid;
grid-template-columns: repeat(auto-fit, minmax($min-size-responsive, 1fr));
```

* **responsive-flex**:<br> 
```scss
display: flex;
flex-wrap: wrap;
& > * {
    flex: 1 1 $min-size-responsive;
}
```

  
---

### **Gap's**
Siendo `n` un numero del 0 al 20 representando cada unidad `1rem`:
* **gap-`n`**:<br> 
    ```css
    gap: nrem
    ```
Ejemplo:
* **gap-1**:<br> 
    ```css
    gap: 1rem
    ```

También se puede usar mediadas intermedias para valores `n`,5:

* **gap-1,5**:<br> 
    ```css
    gap: 1.5rem
    ```
  
---

### **grid-template-columns** | **grid-template-rows**
Siendo `n` un numero del 1 al 12 o `none`
* **grid-cols-`n`**: <br> 	
    ```css
    grid-template-columns: repeat(n, minmax(0,  1fr));
  ```

* **grid-rows-`n`**: <br> 	
    ```css
    grid-template-rows: repeat(n, minmax(0, 1fr));
    ```

### **grid-column** | **grid-row** (catidad en `span`)
Siendo `n` un numero del 1 al 12
* **col-span-`n`**: <br> 	
    ```css
    grid-column: span n / span n;
    ```

* **row-span-`n`**: <br> 	
    ```css
    grid-row: span n / span n;
    ```

o auto: 
* **col-auto**: <br> 	
    ```css
    grid-column: auto;
    ```
* **row-auto**: <br> 	
    ```css
    grid-row: auto;
    ```


### **grid-column-start** | **grid-row-start** || **grid-column-end** | **grid-row-end**
Siendo `n` un numero del 1 al 13
* **col-start-`n`**: <br> 		
    ```css
    grid-column-start: n;
    ```

* **row-start-`n`**: <br> 		
    ```css
    grid-column-start: n;
    ```

* **col-end-`n`**: <br> 		
    ```css
    grid-column-end: n;
    ```

* **row-end-`n`**: <br> 		
    ```css
    grid-column-end: n;
    ```

o auto: 
* **col-start-auto**: <br> 	
    ```css
    grid-column-start: auto;
    ```
* **row-start-auto**: <br> 	
    ```css
    grid-row-start: auto;
    ```
* **col-end-auto**: <br> 	
    ```css
    grid-column-end: auto;
    ```
* **row-end-auto**: <br> 	
    ```css
    grid-row-end: auto;
    ```

o full:
* **col-full**: <br>
    ```css
    grid-column: 1 / -1;
    ```

### **grid-auto-flow**
* **grid-flow-row**:<br> 
    ```css
    grid-auto-flow: row;
    ```
* **grid-flow-col**:<br> 
    ```css
    grid-auto-flow: column;
    ```
* **grid-flow-row-dense**:<br> 
    ```css
    grid-auto-flow: row dense;
    ```
* **grid-flow-row-dense**:<br> 
    ```css
    grid-auto-flow: column dense;
    ```


---
---

## **v-flex**

### **flex-direction**
* **flex-row**:<br> 
    ```css  
    flex-direction: row;
    ```
* **flex-row-reverse**:<br> 
    ```css  
    flex-direction: row-reverse;
    ```
* **flex-col**:<br> 
    ```css  
    flex-direction: col;
    ```
* **flex-col-reverse**:<br> 
    ```css  
    flex-direction: col-reverse;
    ```
  
### **flex-wrap**
* **flex-wrap**:<br> 
    ```css  
    flex-wrap: wrap;
    ```
* **flex-wrap-reverse**:<br> 
    ```css  
    flex-wrap: wrap-reverse;
    ```
* **flex-nowrap**:<br> 
    ```css  
    flex-wrap: nowrap;
    ```
  
### **flex**
* **flex-1**:<br> 
    ```css  
    flex: 1 1 0%;
    ```
* **flex-auto**:<br> 
    ```css  
    flex: 1 1 auto;
    ```
* **flex-initial**:<br> 
    ```css  
    flex: 0 1 initial;
    ```
* **flex-none**:<br> 
    ```css  
    flex: none;
    ```
  
### **flex-grow**
* **flex-grow**:<br> 
    ```css  
    flex-grow: 1;
    ```
* **flex-grow-0**:<br> 
    ```css  
    flex-grow: 0;
    ```
  
### **flex-shrink**
* **flex-shrink**:<br> 
    ```css  
    flex-shrink: 1;
    ```
* **flex-shrink-0**:<br> 
    ```css  
    flex-shrink: 0;
    ```


### **order**
Siendo `n` un numero del 1 al 12
* **order-`n`**: <br>
    ```css
    order: n;
    ```

O valores específicos: 
* **order-first**: <br>
    ```css
    order: -9999;
    ```
* **order-last**: <br>
    ```css
    order: 9999;
    ```
* **order-none**: <br>
    ```css
    order: none;
    ```

---
---

## **Alineamiento**
### **justify-items | align-items | justify-self | align-self**
Siendo `n` un algunos de estos valores: (`start | flex-start | end | flex-end  | center | stretch`)
* **j-items-`n`**: <br> 
    ```css
    justify-items: n;
    ```
* **a-items-`n`**: <br> 
    ```css
    align-items: n;
    ```
* **j-self-`n`**: <br> 
    ```css
    justify-self: n;
    ```
* **a-self-`n`**: <br> 
    ```css
    align-self: n;
    ```

para `align-items` también está el valor `baseline`:
* **a-items-`n`**: <br> 
    ```css
    align-items: baseline;
    ```


### **justify-content | align-content**
Siendo `n` un algunos de estos valores: (`start | flex-start | end | flex-end | center | stretch | space-around | space-between | space-evenly`)
* **j-content-`n`**: <br> 
    ```css
    justify-content: n;
    ```
* **a-content-`n`**: <br> 
    ```css
    align-content: n;
    ```

## **Tamaño**
### **width**
Usados idóneamente para los flex-items 


| 0, 2, 3                              | 4                             | 5                             | 6                                    | 12                                     |
| ------------------------------------ | ----------------------------- | ----------------------------- | ------------------------------------ | -------------------------------------- |
| **w-0**: <br> `width: 0`             | **.w-1/4**:<br> `width: 25%;` | **.w-1/5**:<br> `width: 20%;` | **.w-1/6**:<br> `width: 16.666667%;` | **.w-1/12**:<br> `width: 8.333333%;`   |
| **.w-1/2**:<br> `width: 50%;`        | **.w-2/4**:<br> `width: 50%;` | **.w-2/5**:<br> `width: 40%;` | **.w-2/6**:<br> `width: 33.333333%;` | **.w-2/12**:<br> `width: 16.666667%;`  |
| **.w-1/3**:<br> `width: 33.333333%;` | **.w-3/4**:<br> `width: 75%;` | **.w-3/5**:<br> `width: 60%;` | **.w-3/6**:<br> `width: 50%;`        | **.w-3/12**:<br> `width: 25%;`         |
| **.w-2/3**:<br> `width: 66.666667%;` |                               | **.w-4/5**:<br> `width: 80%;` | **.w-4/6**:<br> `width: 66.666667%;` | **.w-4/12**:<br> `width: 33.333333%;`  |
|                                      |                               |                               | **.w-5/6**:<br> `width: 83.333333%;` | **.w-5/12**:<br> `width: 41.666667%;`  |
|                                      |                               |                               |                                      | **.w-6/12**:<br> `width: 50%;`         |
|                                      |                               |                               |                                      | **.w-7/12**:<br> `width: 58.333333%;`  |
|                                      |                               |                               |                                      | **.w-8/12**:<br> `width: 66.666667%;`  |
|                                      |                               |                               |                                      | **.w-9/12**:<br> `width: 75%;`         |
|                                      |                               |                               |                                      | **.w-10/12**:<br> `width: 83.333333%;` |
|                                      |                               |                               |                                      | **.w-11/12**:<br> `width: 91.666667%;` |










### Otros tipos de tamaño:


| **width**                          | **height**                          |
| ---------------------------------- | ----------------------------------- |
| **.w-auto**:<br> `width: auto;`    | **h-0**: <br> `height: 0`           |
| **.w-full**:<br> `width: 100%;`    | **.h-auto**:<br> `height: auto;`    |
| **.w-screen**:<br> `width: 100vw;` | **.h-full**:<br> `height: 100%;`    |
|                                    | **.h-screen**:<br> `height: 100vw;` |



## **Configuraciones**
* **Breakpoints**
```scss
$breakpoints: (
    '': 0,
    m: 640px,
    t: 768px,
    l: 1024px,
    d: 1280px
) !default;
```
* **Variables**

```scss
$max-cols: 12;
```   
```scss 
$min-size-responsive: 250px;
```