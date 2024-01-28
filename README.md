# HTML Semántica

`div` y `span`  sirven para dividir el contenido, son etiquetas *no* semánticas, el `span` es una etiqueta para agrupar el contenido en línea y el div para agrupar el contenido en bloque.

- **aside**: a un lado, aparte de
- **article**: un elemento con información propia contenida, que si se extrae a otro lugar sigue teniendo sentido
- **header**: no es verdad que solo debe haber un `header` por página, puede haber dentro de `section` o `article` o div. Siempre envolviendo un `h1`…`h6`
- **section**: abarca secciones independientes genéricas de un documento, pueden haber secciones dentro de una sección.
- **main**: solo puede haber una en todo el documento, engloba el contenido que es el principal de la página, por ejemplo, fuera del `main` podemos dejar el titulo principal de la página, y el menú de navegación `nav` y al final el `footer` principal. Lo que esta en el main es el contenido que va a cambiar en cada url.
- **a**: anchor o ancla, sirve para navegar dentro de la página atreves de enlaces o para navegar fuera de la página. por estrategia, es mejor abrir la pagina externa contenida en un a en una pestaña nueva usando `target="_blank"`y por motivos de seguridad colocamos lo siguiente: `rel="noreferrer"` esto para no enviar datos de nuestra página a sitios externos, el sitio de destino no podrá ver información como la URL de origen desde donde proviene el visitante
- **ol**: listas ordenadas
  - type=”a”: los contadores van a ser letras
  - reversed: despliega la lista de forma descendiente
  - start: índice de inicio

- **fieldset**: crea una caja con bordes dibujados, dentro contiene un formulario
- **legend**: va dentro del fieldset y es como un titulo del formulario

`<fieldset> `

 `<legend>Información de contacto</legend> `

 `<label for="">Tal cosa:</label> `

`</fieldset>`

**datalist**: es como un select pero para autocompletar un input de tipo text

`<datalist id="lenguages">   <option value="Java"></option>   <option value="JavaScript"></option>   <option value="SQL"></option> 	<option value="PHP"></option> </datalist> <div> 	<label for="lenguages"> 		<input list="lenguages" name="lenguages"> 	</label> </div>`



### rol

Por defecto cada elemento html tiene un rol que es descrito por el nombre de su etiqueta, pero casos malos, por ejemplo cuando usamos un `div` o `span` podemos especificar el rol con el atributo `role=”nameRol”`

todo lo que hay que saber sobre los role: https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Roles

### Carga de imágenes en una página

Cargar la img solo cuando aparezca en la pantalla. *No utilizar loading=”lazy” en imágenes que están muy arriba*

`<img loading="lazy" src="icon.png" title="Obito" alt="Sharingan">`

*<u>Cada vez que en nuestro html creamos un id, en el window de js se registras.</u>*





# CSS

### hsl:

El sistema de colores HSL (Hue, Saturation, Lightness) en CSS permite definir colores utilizando valores de matiz, saturación y luminosidad.

- **Hue (Matiz)**: Representa el tono base del color y se expresa en grados en una rueda de colores. Los valores van de 0 a 360, donde 0 y 360 representan el rojo, 120 representa el verde y 240 representa el azul.
- **Saturation (Saturación)**: Controla la intensidad o pureza del color. Los valores van de 0% a 100%, donde 0% es completamente desaturado (gris) y 100% es la saturación máxima.
- **Lightness (Luminosidad)**: Controla el brillo del color. Los valores van de 0% a 100%, donde 0% es completamente oscuro (negro) y 100% es completamente claro (blanco).

### oklch:

El sistema de colores OKLCH en CSS es una extensión del sistema de colores HSL (Hue, Saturation, Lightness) que agrega un componente adicional llamado "chroma" (croma). El componente "chroma" representa la intensidad o saturación del color en una escala más perceptual.

La notación OKLCH se utiliza para definir colores en CSS utilizando los valores de matiz (Oklab hue), croma (Oklab chroma) y luminosidad (Oklab lightness). Estos valores se expresan en porcentajes o números decimales.

```css
h1 {
	/*color: rgb(0 0 0 / 50%);  rojo verde azul opacidad*/
  color: hsl(288, 100%, 40%); /* color en grados, saturación y luminosidad*/
  /*color: oklch(lightness chroma hue);*/
}
```

- border-color: currentColor; esto significa que el color del borde va a ser del mismo color que la fuente.

## font-family

Podemos escoger la fuente del sistema operativo usando la siguiente propiedad y valores:

```css
font-family: system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
```

## Herencia en css

veamos el código

```css
<div class="container">
  este es el container
  <div class="child">
    hola mundo 
  </div>
</div>
.container{
  color: teal;
  font-size: 32px;
  border: 3px solid teal;   
}

.child{
  border: inherit
}
```

### Veamos los valores para heredar o no

- ***inherit***: hereda el valor que tiene el padre
- ***initial***: especifica el valor inicial dictado por css, en este caso el valore esta vacío, no tiene borde. evita heredar el valor
- ***unset***: resetea el valor, quita las propiedades heredadas
- ***revert***: revertir el valor de la herencia, el valor por defecto de revert es inherit

```css
.container{
  color: teal;
  font-size: 32px;
  border: 3px solid teal;   
}
ñ
.child{
  border: inherit;
  color: initial;
  font-size: initial;
}
```

Salida:

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/3ece04bd-7ae2-49fc-b8a8-f0aad2a08f4a/cb927862-3c72-4482-938e-cfe4622ea334/Untitled.png)

<aside> 🚨 Existe dos propiedades parecidas pero diferentes, border y outline. border: el border del contenido. outline: es el contorno del contenido. la diferencia entre estos dos es que el border afecta al contenido y el outline se dibuja encima del contenido

</aside>

## Pseudo clases

Son estados o situaciones especiales en las que se encuentra un elemento HTML

- ***hover***: resalta un elemento cuando pasamos el mouser por encima

- ***active***: resalta un elemento cuando hacemos click sobre él.

- ***focus***: Es útil para mejorar la usabilidad y la accesibilidad de los formularios, ya que permite al usuario saber visualmente en qué campo se encuentra mientras interactúa con él.

- ***first-child, last-child***: seleccionar el primer y ultimo elemento

  ```css
  <ul>
  	<li>FilmTop</li>
    <li>Maria</li>
    <li>CountWhater</li>
  </ul>
  
  li:first-child{
  	color: purple;
  }
  li:last-child{
  	color: orange;
  }
  ```

Salida:

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/3ece04bd-7ae2-49fc-b8a8-f0aad2a08f4a/20b14bcb-42d2-4931-b6fb-c24cf6c60bfa/Untitled.png)

## Operadores y alcance

```html
<article>
  <p>Este es un parrafo</p>
  <p>otro parrafo</p>
  <footer>
    <p>parrafo dentro del footer</p>
  </footer>
  <p>otro parrafo más</p>
</article>
article > p{
  color: red;
}
```

Salida:

<aside> 🚨 `article > p`: esto significa que la fuente de color rojo selo se le aplicara a los p que son hijos directos del article.

</aside>

El símbolo "~" en CSS se utiliza para seleccionar elementos que son adyacentes a otro elemento específico. Esta es conocida como la pseudo-clase de hermano general.

Cuando se utiliza el símbolo "~", se seleccionan todos los elementos que siguen inmediatamente al elemento de referencia, siempre y cuando ambos elementos compartan el mismo padre y el elemento de referencia aparezca antes en el orden del documento.

Aquí tienes un ejemplo de cómo se utiliza el símbolo "~" en CSS:

```css
h1 ~ p {
  color: blue;
}
```

En este ejemplo, todos los elementos `<p>` que siguen inmediatamente a un elemento `<h1>` tendrán un color de texto azul.

Es importante tener en cuenta que el símbolo "~" solo selecciona elementos que son hermanos posteriores, no elementos anteriores. Además, solo selecciona elementos que comparten el mismo padre

ejm

```html
<article>
      <span>Esto es negro</span>
      <p>Parrafo</p>
      <span>Esto es rojo porque esta despues del p</span>
      <p>Esto es un p</p>
      <h2>Dream big</h2>
      <span>Esto es de color rojo</span>
    </article>
    
    <span>Este es el ultimo span</span>
p ~ span{
	color: red;
}
```

Salida:

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/3ece04bd-7ae2-49fc-b8a8-f0aad2a08f4a/90903af0-7bb6-4218-830f-6293bf299b49/Untitled.png)

<aside> 🚨 `p + span`: esto indica que selecciona justo al que viene despues, si hay una etiqueta entre ellos no se aplican los estilos. solo 1, si hay 2 span seguidos solo tomara el primero

</aside>

### Hacer que el texto de un salto de línea si sobrepasa el ancho de la pantalla

```css
word-wrap: break-word;
ó
white-space: pre-wrap; 
```



# La cascada

Si hay dos selectores con las mimas propiedades, el navegador selecciona el selector y sus propiedades que estén mas abajo en la hoja de estilos



## Especificidad

La especificidad en CSS es una forma de determinar qué regla CSS se aplicará a un elemento cuando hay múltiples reglas que se aplican al mismo elemento. Es una forma de resolver conflictos entre reglas y determinar cuál tiene prioridad.

La especificidad se basa en la combinación de selectores utilizados en una regla CSS. Cada selector tiene un valor de especificidad asociado, y cuanto mayor sea el valor de especificidad, mayor será la prioridad de la regla.

La especificidad se calcula utilizando cuatro componentes:

1. Selectores de ID: Cada ID en un selector tiene un valor de especificidad de 100.
2. Selectores de clase, atributo y pseudo-clases: Cada clase, atributo o pseudo-clase en un selector tiene un valor de especificidad de 10.
3. Selectores de tipo y pseudo-elementos: Cada tipo de elemento o pseudo-elemento en un selector tiene un valor de especificidad de 1.
4. Selectores universales y combinadores: Tienen un valor de especificidad de 0.

Cuando se aplican múltiples reglas a un elemento, se compara la especificidad de las reglas y se aplica la regla con la especificidad más alta. Si dos reglas tienen la misma especificidad, se aplica la regla que aparece más tarde en el archivo CSS.

Es importante entender cómo funciona la especificidad en CSS para evitar conflictos y asegurarse de que las reglas se apliquen correctamente a los elementos deseados.



# Display: block

la etiqueta div tiene display: block, es decir que se comporta como bloque y solo hay un bloque por línea.

```css
<section class="parent">
  <div class="item">1</div>
  <div class="item">2</div>
  <div class="item">3</div>
</section>
```

```css
.parent{
  display: block;
}

.item{
  border: 1px solid black;
  opacity: .9;
  width: 100px;
  height: 100px;
  background: teal;
  color: white;
}

.item:first-child{
  background: red;
}

.item:last-child{
  background: purple;
}
```



## Display: inline;

las etiquetas se comportan como texto, es decir se colocan una despues de la otra y en la misma línea.

```css
.item{
  border: 1px solid black;
  opacity: .9;
  width: 100px;
  height: 100px;
  background: teal;
  color: white;
  display: inline;
}
```



## Display: inline-block;

los elementos se colocan en línea pero se comportan como bloques

```css
.item{
  border: 1px solid black;
  opacity: .9;
  width: 100px;
  height: 100px;
  background: teal;
  color: white;
  display: inline-block;
}
```



```css
<section class="container">
  CSS IS AWESOME
</section>
.container{
  width: 150px;
  height: 150px;
  background-color: white;
  padding: 10px;
  box-sizing: border-box;
  font-size: 48px;
}
```

visible



## overflow: visible

el contenido no es recortado, el contenido se dibuja fuera de la cajacontenedora

## overflow: hidden

Muestra solo lo que esta dentro de la caja, recorta lo que esta fuera.

## overflow: scroll

Coloca una barra de desplasamiento vertical y horizontal para poder ver el contenido



## overflow: auto

Es como el scroll, solo que el navegador determina si muestra o no las barras del scroll, si es que hay desbordamiento o no.

<aside> 🚨 Se recomienda usar overflow: auto; en lugar de scroll.

</aside>

## texto y overflow

si lo que se desborda es un texto, podemos colocar `overflow: hidden;` y para que se muestre que el texto continúa, colocamos la propiedad `text-overflow: ellipsis;`

> Ellipsis = los puntos suspensivos

### text-overflow: clip

corta el texto donde termina la caja





# Position

Los elementos en css se posicionan por defecto de forma ***static*** 

```css
<section>
  <div class="container">Container</div>
</section>
```

```css
section{
  border: 5px solid red;
  width: 250px;
  height: 250px;
  box-sizing: border-box;
}

.container{
  background: teal;
  width:100px;
  height: 100px;
}

body{
  background: gray;
}
```

## Position: absolute;

Podemos determinar las coordenadas del elemento en el documento, podemos mover la caja azul a cualquier lugar dentro o fuera del borde rojo. De forma absoluta se salta cualquier control que tenemos. Se posiciona respecto a todo el documento.

```css
.container{
  background: teal;
  width:100px;
  height: 100px;
  position: absolute;
  left: 0;
  bottom: 0;
}
```

## Position: relative;

Crea un punto relativo para que cualquiera de nuestros hijos pueda tomarlo como referencia 

```css
section{
  border: 5px solid red;
  width: 250px;
  height: 250px;
  box-sizing: border-box;
  position: relative;
}

.container{
  background: teal;
  width:100px;
  height: 100px;
  position: absolute;
  left: 0;
  bottom: 0;
}
```

### Centrar un div  (*No recomendado*)

```css
.container{
  background: teal;
  width:100px;
  height: 100px;
  position: absolute;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  margin: auto;
}
ó
.container{
  background: teal;
  width:100px;
  height: 100px;
  position: absolute;
  inset: 0;
  margin: auto;
}
```

<aside>
🚨 ***Inset***: La propiedad **inset** corresponde a las propiedades **top** y **bottom**, o **right** y **left**, dependiendo de los valores definidos para el modo de escritura, la dirección y la orientación del texto. Puede tomar valores de longitud, porcentaje o palabras clave, como **auto**, **inherit**, **initial** y **unset**

</aside>

## Position: fixed;

Este valor de la propiedad position ignora el `postion: relative;` se mueve dentro de todo el viewport, es decir, dentro de la pantalla que vemos, se queda fijo en las coordenadas que le indiquemos.

```css
section{
  border: 5px solid red;
  width: 250px;
  height: 250px;
  box-sizing: border-box;
  position: relative;
}

.container{
  background: teal;
  width:100px;
  height: 100px;
  position: fixed;
  top: 0;
  right: 0;
}
```

## Position: sticky;

> Sticky = pegajoso
>

Es como el `position: fixed;` solo que sticky solo se mueve dentro del contenedor padre, se aconseja que el contenedor padre tenga `position: relative;`

```css
.container{
  background: teal;
  width:100px;
  height: 100px;
  position: sticky;
  top: 0;
  right: 0;
}
```



# contexto de apilamiento y z-index

z-index se usa para x elemento se superponga a los demas, entre mayor sea el número, mas prioridad tendrá

El contexto de apilamiento en CSS se refiere a la superposición de capas o elementos a lo largo del eje Z del navegador. Es importante para controlar el orden en el que los elementos se muestran en pantalla y evitar que se superpongan de manera inesperada.

En CSS, cada elemento tiene un contexto de apilamiento que determina su posición en relación con otros elementos. Los elementos con un contexto de apilamiento diferente se apilan en capas separadas y pueden superponerse entre sí dentro de su propia capa.

El contexto de apilamiento se crea cuando se cumplen ciertas condiciones, como tener una posición (absoluta o relativa) con un valor de z-index distinto de "auto", ser un elemento flex con un valor de z-index distinto de "auto" y ser elementos con un valor de opacidad menor a 1.

Al establecer el contexto de apilamiento, se puede controlar el orden en el que los elementos se superponen y se muestran en pantalla. Esto es útil para crear diseños complejos y controlar la interacción visual de los elementos.

Espero que esta explicación te sea útil. Si tienes alguna otra pregunta, no dudes en hacerla.