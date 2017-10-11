# Sintaxis de CSS

En la actualidad, CSS y HTML son dos lenguajes que van de la mano en prácticamente todos los proyectos de diseño y desarrollo web, y es que en verdad son pocos los que se aventuran a no utilizarlos juntos. A pesar de esta intrínseca relación, ambos lenguajes se ocupan para desempeñar funciones muy distintas y por lo que su sintaxis es completamente diferente.

Para comprender mejor la sintaxis de CSS, tenemos que estudiarla como un conjunto de reglas que se componen de selectores, propiedades y valores. Una típica regla de CSS luciría de la siguiente manera:


~~~~
 p { font-size: 10px; }
  ~~~~

Para poder analizar dicha regla la dividiremos en cuatro partes, primero tenemos el selector que en este caso esta representado por “p”, esta parte definirá a que sección del HTML aplicaremos el estilo, después viene la parte llamada propiedad, que esta representada por “font-size” y se encargará de definir que aspectos de la sección queremos configurar. En este caso particular estamos estableciendo el tamaño de la fuente a 10 píxeles, estos píxeles representan la tercera parte que compone la regla, a la cual le damos el nombre de valor de la propiedad; finalmente la cuarta parte es el conjunto “propiedad-valor” al cual llamaremos declaración.

 ## Selectores CSS

Los selectores juegan un papel fundamental en la sintaxis de CSS, ya que es *gracias a ellos que podemos delimitar de manera exacta que elementos deben o no recibir el estilo que estamos a punto de definir*. Existen varias clases de selectores, entre los principales tenemos aquellos que toman literalmente las etiquetas HTML para envolver a todo los elementos de ese tipo, también existen los selectores por ID o por clase que únicamente envuelven a los elementos que coincidan con estos valores en sus atributos, y también tenemos los selectores hechos mediante expresiones regulares los cuales nos permiten incluir o excluir elementos de manera más específica.

Para utilizar selectores HTML basta con especificar el elemento HTML en las declaraciones, es decir algo como esto:

~~~~
p { color: blue; }
~~~~
Aplicará un estilo a todos los elementos que estén compuestos por la etiqueta “p” en el documento HTML. Con la regla que acabamos de escribir todos los párrafos de la página tendrán la letra de color azul.

Por su parte, los selectores por ID adjuntan los estilos definidos únicamente al elemento HTML con el ID correspondiente. Así que, si en nuestro código HTML tenemos algo como esto:


#### ¡Azul!


Y sólo queremos aplicar el estilo del color azul a este elemento, entonces podemos hacer algo así:

~~~
parr_azul { color: blue; }
~~~
De esta manera únicamente ese párrafo se verá estilizado y todos los demás permanecerán igual. Como se puede apreciar puse una almohadilla “#” antes del nombre del ID, este signo es utilizado reconocer a los identificadores, mientras que para las clases antepondremos al nombre un punto “.”, lo que nos dará una regla como esta:

~~~
.parr_azules { color: blue; }
~~~
Dichos selectores de clases añadirán el estilo a todos los elementos que contengan dicha clase, así podemos aplicar el estilo a un grupo más amplio de elementos, con la posibilidad de segmentar.

Hay que recordar que un elemento puede tener varias clases por lo que los estilos definidos para todas ellas se aplicarán al mismo elemento. Por ejemplo, si tenemos un elemento de tipo párrafo que ya pertenece a la clase “parr_azules” y le agregamos en el HTML una clase llamada “parr_grandes” para delimitar aquellos párrafos que deberían tener un tamaño de letra más grande, entonces tenemos que definir en nuestra hoja de estilo algo así:
~~~
p             { font-size: 10px; }
.parr_azules  { color: blue; }
.parr_grandes { font-size: 20px; }
~~~
Habrá algunos párrafos que coincidan con la primera y la última regla de nuestra hoja de estilo y como ambas están definiendo la propiedad “font-size”, en teoría, dichos párrafos recibirán dos tamaños de letra distinta, pero el que predominará será aquel que cuente con mayor especificidad, que en este caso será el que tenga la clase como el selector, ya que una clase es más específica que un elemento.

Caso distinto sucederá cuando dos o más clases definan la misma propiedad, como las dos reglas tendrían la misma especificidad, para esta situación se va a aplicar el valor que se defina en la clase que aparezca al último en la hoja de estilo.

También se puede ser más específico estableciendo qué elementos de una clase serán los que pueden recibir el estilo, por ejemplo si tuviéramos una clase llamada únicamente “azul”, la cual aplicamos tanto a cabeceras, párrafos y elementos span en nuestro código HTML, pero queremos aplicar el estilo únicamente a las cabeceras de tipo “h2” entonces podemos hacer algo como esto:

~~~
h2.azul { color: blue; }
~~~

## Pseudo clases y pseudo elementos

El uso de pseudo clases y pseudo elementos puede resultar ser un poco más difícil de comprender por lo que lo veremos más a detalle ya que estemos más adentrados en el manual, por ahora únicamente vamos a definir que son utilizados para dar una mayor especificidad y generalmente sirven para indicar posición o algún movimiento.

Se identifican por la adición de una condición extra y el signo de dos puntos que se encuentra entre el elemento y la acción. Por ejemplo, si quisiéramos obtener la primera letra de algún elemento utilizamos una sentencia como “elemento:first-letter”, o si queremos aplicar un estilo cada vez que se coloque el ratón sobre un elemento haremos algo como esto:

~~~
a:hover { text-decoration: none; }
~~~

Este regla de estilo quitará la línea que aparece debajo de los enlaces de una página, cada vez que coloquemos el cursor sobre alguno de ellos.

Agrupación de selectores CSS
Existirán ocasiones en las que queramos aplicar un mismo estilo a diferentes elementos pertenecientes ya sea a diferentes grupos o clases, para estás situaciones podemos usar reglas que agrupen selectores en una sola sentencia. Es decir, en lugar de hacer algo como esto:
~~~
p { color: blue; }
#cabecera_azul { color: blue; }
~~~
Simplemente aplicamos todo en una sola línea de la siguiente manera:
~~~
p, #cabecera_azul { color: blue; }
~~~
Por otro lado si lo que queremos es envolver elementos anidados para aplicarles algún estilo, basta con añadir un espacio entre los selectores. Por ejemplo si queremos aplicar la letra de color azul únicamente a los párrafos que están dentro del “div” principal de la página, basta con declarar la regla de la siguiente manera:

~~~
#principal p { color:blue; }
~~~

## Otros selectores

Como ya dijimos existen otra clase de selectores que pueden llegar a ser muy específicos y nos permitirán delimitar a gran escala, pero para lograr utilizarlos debemos conocer el funcionamiento de las expresiones regulares, por lo que su uso no es tan común. Si quieres conocer a fondo como funcionan dichos selectores le puedes echar un vistazo a este artículo, que si bien habla de jQuery, aplica de la misma manera para los selectores CSS.

## Propiedades y valores
Si bien los selectores nos permiten delimitar el grupo de elementos que vamos a modificar, el estilo en sí es aplicado por las propiedades y los valores.

Las propiedades representan las partes de un elemento que vamos a alterar, estas van desde colores, tamaños de fuente, hasta bordes y decoraciones. Por su parte los valores variarán según la propiedad elegida, pero en general existen dos tipos de unidad que pueden ser utilizados por casi todas las propiedades, nos referimos a los números y porcentajes.
