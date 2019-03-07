# Seminario Gráfica Computacional I → Clase 2

### Martes 2 de abril → Javascript

Javascript (no confundir con Java) es un lenguaje de programación. Con este lenguaje se pueden escribir programas que serán ejecutados en un navegador web. Estos programas pueden ser incluidos o vinculados a una página web a modo de script, entre etiquetas `<script>…</script>`. 

En un programa de Javascript podemos encontrar código y datos; código es la parte que permite redactar instrucciones. La parte de datos es la que permite almacenar información con la que podríamos condicionar las instrucciones. Así, por ejemplo, podemos escribir: 

```
<script>
  var d = new Date();
  var h = d.getHours();
  var saludo;
  if ((h >= 6) && (h < 12)) { 
    saludo = "buenos días"
  } else if ((h >= 12) && (h < 20)) {
    saludo = "buenas tardes"
  } else { 
    saludo = "buenas noches"
  }
  document.write(saludo);
  // Para otros despliegues del saludo, ver https://www.w3schools.com/js/js_output.asp  
</script>
```

En este ejemplo de Javascript se crea una variable `d`, a la que se le encarga almacenar [la fecha](https://developer.mozilla.org/es/docs/Web/JavaScript/Referencia/Objetos_globales/Date) en la que una página web es visualizada. Luego, a una variable `h` se le encargar almacenar [solo la hora](https://developer.mozilla.org/es/docs/Web/JavaScript/Referencia/Objetos_globales/Date/getHours) en tal fecha. Después se crea una variable con el nombre `saludo`, en la que no se almacenan datos de forma inmediata. Mediante [condiciones](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/if...else) (`if (…){…}`, `else if (…){…}`, `else{…}`) se le encargará a la variable `saludo` almacenar la cadena de caracteres que corresponda a la hora en que se visualiza la página web. Finalmente, se escribe el valor correspondiente del `saludo`.

El mismo programa puede ser escrito en un documento aparte, con extensión `.js`. Si a este programa le llamamos `saludo.js` y lo dejamos en la misma carpeta que contiene una página web, podríamos vincularlo escribiendo: `<script src="saludo.js"></script>`. Dentro del documento no tenemos que incluir las etiquetas `<script>…</script>`. 

Como Javascript es un lenguaje de programación que comenzamos a explorar, es recomendable tener a mano algún ayudamemoria: 

- [JS CheatSheet](https://htmlcheatsheet.com/js/)

- [WebsiteSetup JavaScript Cheat Sheet](https://websitesetup.org/javascript-cheat-sheet/)

- [Cheatography JavaScript Cheat Sheet](https://www.cheatography.com/davechild/cheat-sheets/javascript/pdf_bw/)

Además, tenemos que tener presente que Javascript necesita del [DOM (Document Object Model)](https://www.w3schools.com/js/js_htmldom.asp), Modelo en Objetos para la Representación de Documentos. A través del DOM, los programas escritos en JS pueden acceder y modificar el contenido, estructura y estilo de la representación de la página web. Por ejemplo:

```
<script>
  document.getElementById("unique").style.color="#FF0000";
</script>
```
En este ejemplo accedemos a la representación del documento para obtener el elemento de identidad `unique`. Este elemento será modificado con un cambio de estilo: Su color visto pasará a ser rojo. 

Modificar la representación de una página web es como "photoshopear" una imagen. Si capturaste 3 elementos y con Photoshop agregas un cuarto, en ningún caso modificas la realidad capturada, pero todos podrán ver una imagen con 4 elementos. Lo que modificas es lo representado. No se puede alterar lo presentado.

#### Variables

En programación, una variable está formada por un espacio en el sistema de almacenaje (memoria principal del computador) y un identificador asociado a dicho espacio. Este espacio contendrá una cantidad conocida o desconocida de datos, que pueden ir variando en la medida que el programa se ejecuta (y esta es la razón del nombre). 

En lenguajes de programación de propósito general, tales como [C++](https://es.wikipedia.org/wiki/C%2B%2B) o [Java](https://es.wikipedia.org/wiki/Java_(lenguaje_de_programaci%C3%B3n)), o en derivados como [Processing](https://processing.org/), las variables se crean escribiendo el **tipo de dato, espacio, nombre de la variable, asignación, valor y fin de la instrucción con punto y coma**, como en `int a = 3;`, `float b = 3.14;`, `String c = "Pi";`.

**Pero en la creación de variables en Javascript se omite la declaración del tipo de dato: Para todo evento [se puede utilizar `var`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements#Declarations), lo que implica escribir *var*, espacio, nombre de la variable, asignación, valor y fin de la instrucción con punto y coma**, como en `var a = 3;`, `var b = 3.14;`, `var c = "Pi";`.

Respecto del **nombre de la variable** habría que indicar tres cosas: (1) no corresponde iniciarlas con números, (2) no se puede usar espacios, tildes ni acentos, y (3) corresponde evitar el uso de [palabras reservadas](https://developer.mozilla.org/es/docs/Web/JavaScript/Referencia/Palabras_Reservadas) por el lenguaje de programación en uso.

Para la **asignación** de un valor se utiliza un signo igual **=**, lo que no debes confundir con un doble signo igual **==**, que es un operador utilizado para comprobar la igualdad, pero jamás para asignar un valor.

Además de tener variables a las que se le asigna un valor numeral, entero o decimal (ej: `var a = 1;`), y variables a las que se les asigna una cadena de caracteres o *string* (ej: `var a = "uno";`), podemos tener una variable a la que se le asigna un arreglo o *array* `var a = ["uno", 2, "tres",4, "cinco"];`. Luego, dentro del arreglo, tenemos distintas posiciones partiendo del cero. Podemos obtener el valor en primera posición (uno) cuando escribimos `a[0]`.

También podemos tener una variable a la que se le asigna un "object" como contenido: `var a = {uno:"gato", dos:"perro", tres:"tortuga", cuatro:"iguana"};`. En este caso, podemos pedir los contenidos del objeto *por su nombre*. Podemos obtener el valor "gato" cuando pedimos `a.uno`

Luego podemos comenzar a mezclar:

```
var a = [ { name: "Sergey Prokopyev", craft: "ISS" }, { name: "Alexander Gerst", craft: "ISS" }];
```

En este caso, si quisiera obtener el nombre "Sergey Prokopyek", tendría que ir por `a[0].name` o `a[0]["name"]`, porque se trata de un arreglo (`[…]`), que contiene objetos (`[{…},{…},{…}]`).

#### JSON

La estructura del objeto inspira al JavaScript Object Notation (JSON), un formato de texto sencillo para el intercambio de datos. Uno puede tomar un JSON en línea y "parsearlo" para que sus datos se conviertan en los datos de una variable en un JS. 

Tomemos, por ejemplo, este JSON con un sumario de los últimos movimientos telúricos sobre 4.5 que han sido registrados en las últimas 24 horas la USGS: https://earthquake.usgs.gov/earthquakes/feed/v1.0/summary/4.5_day.geojson

Para almacenar sus datos en una variable de nombre `a` utilizando JS, tenemos que escribir:

```
var request = new XMLHttpRequest();
request.open('GET', ' https://earthquake.usgs.gov/earthquakes/feed/v1.0/summary/4.5_day.geojson', true);
request.onload = function () {
  var a = JSON.parse(this.response);
  console.log(a);
}
request.send();	
```

Luego, será la variable `a` la que contendrá los datos de tal JSON, de acuerdo a las "reglas gramaticales" que correspondan al caso. Para el JSON que nos ofrece la USGS, la consulta por la magnitud del temblor más reciente es `a["features"][0]["properties"]["mag"]` ó `a.features[0].properties.mag`

La estructura y sus detalles se explican bajo el subtítulo de "Output" en: https://earthquake.usgs.gov/earthquakes/feed/v1.0/geojson.php

- - - - - - -

#### Referencias

JavaScript:

- [Fundamentos de JavaScript](https://developer.mozilla.org/es/docs/Learn/Getting_started_with_the_web/JavaScript_basics)

- [JavaScript for Beginner](http://xahlee.info/js/js_basics_index.html)

- [JavaScript para Gatos](https://jsparagatos.com/)

- [JavaScript Tutorial](https://www.w3schools.com/js/)

- [Programación en JavaScript/Variables](https://es.wikibooks.org/wiki/Programaci%C3%B3n_en_JavaScript/Variables)

JSON:

- https://github.com/dariusk/corpora

- https://earthquake.usgs.gov/earthquakes/feed/v1.0/geojson.php

- https://jsonlint.com/

- - - - - - - 

###### [SIGUIENTE CLASE →](https://github.com/profesorfaco/DGP502-2019/tree/gh-pages/clase-03)

