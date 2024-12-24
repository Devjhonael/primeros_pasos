* elemento bloqueante ocupa todo el espacio de su elemento padre
- li,ul,form,h,section.article,nav,header,div,oletc  son bloqueante

* elemento en linea ocupa todo el espacio de su contendo
- a, span,button,i,strong,em,img,input
- a, span, label, strong, br, input, textarea, abbr, acronym, b, basefont, bdo, big, cite, code, dfn, em, font, i, kbd, q, s, samp, select, small, strike, sub, sup, u, u, var
- son apilables. no tienen ni margin-top ni margin-bottom (por mucho que se lo indiques en el CSS). Si tienen margin-left y margin-right.
- no respetan ni width ni height. Estas medidas dependerán del tamaño en píxels de su contenido

-convierte un elemento en linea a un elemento bloqueando con todos sus atributos display:block;
- unicamente  section{display:inline-block;width:33%;} tiene un ordenamiento mas comodo


* css = disenar con codigo
- el estilo que se coloca al final le gana al del principio pero en si solamente se chanta los valores que se van a cambiar ejm
body{
    background-color: red;
    color: white;
}


body{
    color: green;
}
=> lo que va afectar o se va reescribir es el el atributo color xk es el unico que esta sufriendo cambios entiendes
- no es bueno par crear correos electronicos para eso usar algunos build que se encargaran de arrastras y crear los correos electronico OJO 

para normalizar usamos normalize 
no se usa etiquetass para usar css solo clases
- todas las etiquetas deben tener clases 
- gracias a ello podemos tener clases con las especificaciones correctas y solo aplicamos a las etiquetas
- por buenas practicas no es bueno isar los selectores ni tampocos los id si no solamente clases
- selectores agrupados es compartir atributos con otras clases osea como modulos
aplica ese atributo a todos las etiquetas que tengan las clases 
.p-first,
.p-second{
    color: red;
}
.p{
    background-color: aqua;
}

-aplica este atributo a un elemento que tenga las 2 clases

-.p-first.p-second{
    color: red;
}

- tiene que ser una etiqueta p y tbm tiene k tener una clase title si no no se aplica
p.title{
    color:red;
}

selectores compuesto descendiente osea que div>p que p este dentro de un div no importa si esta e el medio o alfondo basta con que este dentro y se aplica los estilos

div p{
    colore:red
}


selectores de atributos se usan para seleccionar un elemento en funcion de un atributo cualquera

se usa para los formulario maso menos
[atributo="valor"]{

}

[input=text],[input=password]{
    color:red;
}

que tal los atributos no tienen completo su nombre ^ indicamos que comienze con el nombre de te
[type^=te]{
    border:1px solid red;
}

$que termine con jpg hacer estos estilos
[href$=jpg]{
    border:1px solid red;
}

que contenga ed.team usamos un * como es punto usamos ""
[href="ed.team"]{

}

hay 4 operadores

* selector universal selecciona todo
> hijo directo
+ hermano directo
~ hermanos siguientes

*{
    color:red;
}
todo lo que esta dentro de div colocar estos estilos 
div *{
    color:green;
    
}
hijo directo osea dentro del div debe seguirle el p
div >p{
    color:green;   
}
osea sto quiere decir que tiene que ser hermano siguiente osea despues de un div debe hacer un p en la misma estructura
div + p{
    color:green;   
}

que son hermanos siguientes osea despues de div todos los p que sean hermanos de div directo segun su ramificacion
div ~ p{
    color:green;   
}
- mientras mas especifico es una regla ese es el que gana por ejemplo
h1.title{} aqui indicamos que h1 su clase titile osea bien especifico

https://jonassebastianohlsson.com/specificity-graph/
aqui colocamos nuestro css y medimos nuestra especificidad

* cascada= lo que esta al final siempre le gana al inicio
los testilos que viene despues sobre escriben a los estilos anteriores
colocame los 4 bordes y ahora quitame el de derecha para se usa mas o menos

* para saber que estilos estan colocados dentro de un contendor html podemos ir al anvegador y seccionar ese elemento y ahi podemos ver que elementos y que estilos tiene ese elememento o hacer pruebas super facil


*herencia los elemento heredan los estilos de su padre
    <div class="container">
      <h2>Lista de tareas</h2>
      <ul>
        <li>Estudiar CSS</li>
        <li>Estudiar JS</li>
        <li>Estudiar HTML</li>
      </ul>
    </div>
- si al container le pongo colo:red; todo lo que esta dentro sera color red los hijos heredan del padre, se heredan normalemente estilos de texto color, alineacion, centrado, ananio de caja
no se hereda padding, margin estilos de caja

.container *{
    border:inherit;
}

- dice que quiere heredar a la fuerza los estilos del padre caso especiales ejmplo:
a{
    colo:inherit;
}
-toma el color del padre para que los enlaces no seas de color azul horrible

* layers CSS
- crear capas y separarlo en capsa para tener mejor esturcturado nuestro css
- organizo mi codigo css y lo voy agrupando y declarando en los layers
/* * aqui manda la declaracion se ejecuta por casca aqui no abajo */
@layer theme;
@layer base;
@layer color;

@layer theme{
    body{

        color:blue;
    }
}
@layer base{
    body {

        color:orange;
    }
}

*modelo de caja box-model
-todo es una caja en la web 
- solucionar el layout donde va cdaa elemento y como me aseguro  que estan en el lugar donde deben estar 

el layout model 
el algoritmo del navegador para entender la geometria de cada elemento HTML luego de procesar el CSS: el tamano, la posicion, la separacion con otros elementos

/* div{
    display: inline o bloque o inline-bloque o none;
} */
inline: lo convierte en linea
block: ocupada todo el ancho de su padre


display: none; = elimina el contenido, la etiqueta y el espacio que ocupaba y los que estan abajo suben
visibility:hidden; = elimina el contenido , no la etiqueta y si separa el espacio que tenia 

- recuerda las imagenes son inline-block por lo tanto inline que significa en linea y se pone uno al costado de otro entonces asi se pondran las imagenes
ahora como es inline- block puedo darle un width para que se acomode mejor y recuerda las imagenes son como texto inline-block entonces podemos centrarlo con text-align:center;
* siempre es asi