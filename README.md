* elemento bloqueante ocupa todo el espacio de su elemento padre
- li,ul,form,h,section.article,nav,header,div,ol etc  son bloqueante

* elemento en linea ocupa todo el espacio de su contenido
- a, span,button,i,strong,em,img,input
- a, span, label, strong, br, input, textarea, abbr, acronym, b, basefont, bdo, big, cite, code, dfn, em, font, i, kbd, q, s, samp, select, small, strike, sub, sup, u, u, var
- son apilables. no tienen ni margin-top ni margin-bottom (por mucho que se lo indiques en el CSS). Si tienen margin-left y margin-right.
- no respetan ni width ni height. Estas medidas dependerán del tamaño en píxels de su contenido

-convierte un elemento en linea a un elemento bloqueando con todos sus atributos display:block;

- unicamente  section{display:inline-block;width:33%;} nos permite convertirlo en linea osea al costado de otro elemento pero tener el margin padding ancho y alto como un elemento bloqueante por eso mucho mas comodo

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

- por buenas practicas no es bueno usar los selectores ni tampocos los id si no solamente clases
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
input[atributo="valor"]{

}

input[type=text],input[type=password]{
    color:red;
}


que tal los atributos no tienen completo su nombre ^ indicamos que comienze con el nombre de te
input[type^=te]{
    border:1px solid red;
}

$ que termine con jpg hacer estos estilos
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
- si al container le pongo color:red; todo lo que esta dentro sera color red los hijos heredan del padre, se heredan normalemente estilos de texto color, alineacion, centrado, tananio de caja
no se hereda padding, margin estilos de caja

.container *{
    border:inherit;
}

- dice que quiere heredar a la fuerza los estilos del padre caso especiales ejmplo:
a{
    color:inherit;
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
- solucionar el layout donde va cada elemento y como me aseguro  que estan en el lugar donde deben estar 

el layout model 
el algoritmo del navegador para entender la geometria de cada elemento HTML luego de procesar el CSS: el tamano, la posicion, la separacion con otros elementos

/* div{
    display: inline o bloque o inline-bloque o none;
} */
inline: lo convierte en un elemento en linea
block: ocupada todo el ancho de su padre


display: none; = elimina el contenido, la etiqueta y el espacio que ocupaba y los que estan abajo suben
visibility:hidden; = elimina el contenido , no la etiqueta y si separa el espacio que tenia 

- recuerda las imagenes son inline-block por lo tanto inline que significa en linea y se pone uno al costado de otro entonces asi se pondran las imagenes
ahora como es inline- block puedo darle un width para que se acomode mejor y recuerda las imagenes son como texto inline-block entonces podemos centrarlo con text-align:center;
* recuerda que se puede centrar elementos inline basta dandole al padre text-align:center

-para centrar un div margin-left:auto; margin-right:auto; 
*{
box-sizing:border-box;
}
- se usa esta propiedad a todo el doc para cuando tenga un caja y le ponga padding margin border no sume su ancho ni alto actual si no que coja de su propio espacio al interior 
- .cuadrado{
    outline:10px solid red;
}
el atributo outline hace referencia a lo que esta afuera del elementos su relieve por fuera no por dentro esto se usa mas comunmente en formularios de los input

-box-shadow: h v blur spread color / inset;
h: movimiento horizontal(positivo derecha )
v: movimiento vertical (positivo abajo)
blur: difumidado 
spread: es que tanto crece o se comprime la sombra en sus cuatro lados

/ las pseudoclases son selectores dinamicos o contextuales. esto significa que su comportamiento va a depender de las circunstancias y siempre usamos los :

- h1:hover{
    color:red;
    cursor:pointer;
}
a:active = va haer todo lo que esta adentro por que se ejecutara cuando le hagas clip
a:visited{
    todo lo que quieres cuando un enlace ya fue visitado
}


a:hover = solo si el usuario pasa el cursos sobre el elemento, normalmente en un enlace

:focus = solo interviene si el usuario selecciona el elemento con los controles del teclado.

:active = Selecciona un elemento cuando el usuario lo activa (por ejemplo, con un clic).





















* JS BASICO
// //^ SEMANA 04

// // declara un variable asignando un valor
// // variables numerico, float, string y boleanos
// let edad = 20;
// let peso = 89.7;
// let nombre = "jhonatan";
// let isCasado = false;

// // valores que no se pueden modificar de ninguna manera
// const pi = 3.1416;
// const igv = 0.18; 

// // imprimir 23manera "concatenando con +, con comas ,  y comillas invertidas o backticks
// console.log(nombre + " " + edad); //concatenando
// console.log(nombre,edad); //concatenando
// console.log(`nombre ${nombre} apellido ${edad}`); //backticks

// // // OPERADORES
// // // + suma
// // // - resta
// // // * multiplicacion
// // // / division cociente
// // // % residuo de una operación de división entera

// // // CONDICIONALES
// // if (condition) {
// //   console.log("si cumple la condiciones")
// // }else{
// //   console.log("no cumple la condiciones")
// // }

// // // COMPARADORES ARITMETRICOS
// // // > mayor
// // // < menor
// // // <= menor o igual
// // // >= mayor o igual
// // // !== diferente
// // // == igual valor pero diferente tipo de dato 
// // // === igual valor e igual tipo de dato

// // // COMPARADORES LOGICOS

// // // Y    :   &&
// // // O    :   ||   
// // // not  :   !

// // // SWITCH
// // switch (condicion_ala_que_opertenezca) {
// //   case 1:
// //     break;
// //   case 2:
// //     break;

// //   default:
// //     break;
// // }

// // ARREGLO
// let vacio=[]//declarando un array vacio
// let nombres = ["Jorgito", "Pedrito", "Sandrita", "Danielito"];
// console.log(nombres);// imprimir todo el arreglo
// console.log(`Posición 4 = ${nombres[4]}`);// imprimir un elemento del arreglo dada la posición
// nombres[0] = 720;// modificar o asignar un valor al arreglo
// console.log(nombres);//mostrar el array modificado

// como funciona al tipo_datos.metodo que se desea aplicar
// console.log(`Cantidad de elementos del arreglo ${nombres.length}`);
// numeros.push(212);//agregar elementos al final del array
// console.log(nombres);

// // // CICLO WHILE
// // // un bucle repetitivo hasta que la condiciones cumple
// // while (condition) {
// //   // parte verdadera o que cumpla la condicion
// // }

// // // CICLO DO-WHILE
// // do {
// // // parte verdadera
// // } while (condition);

// // // CICLO FOR
// // let numeros = [5, 7, 8, 6, 5, 12, 10];
// // for (let i = 0; i < numeros.length; i++) {
// //   numeros[i] = numeros[i] * numeros[i];
// // }
// // console.log(numeros);



// //OBJETOS 1
// // Un objeto es un elemento que abstrae caracteristicas
// // o atributos en común o que guardan relación

// // ¿Como se crea?
// let objPersona = {
//   nombre: "Jorge",//clave - valor
//   apellido: "Garnica",
//   edad: 28,
//   peso: 72,
//   casado: false,
//   cazado: true,
// };

// // Forma 1 de acceder a los atributos
// console.log(objPersona.nombre);
// // Forma 2 de acceder a los atributos
// console.log(objPersona["apellido"]);

// // Forma 1 de modificar un atributo
// objPersona.casado = true;
// objPersona.peso = 70;
// objPersona['peso']=120

// console.log(objPersona);

// // Forma 1 de crear nuevos atributos a un objeto
// objPersona.platosFavoritos = ["Cebiche", "Pastel de Papa", "Rocoto Relleno"];
// console.log(objPersona);

// for (let i = 0; i < objPersona.platosFavoritos.length; i++) {
//   console.log(objPersona.platosFavoritos[i]);
// }

// // // --------------------------------------- //

// let productos = [
//   {
//     nombre: "TV Samsung 50",
//     precio: 8000.0,
//     codigo: "10101",
//     coloresDisponibles: ["Azul", "Plomo", "Blanco", "Negro"],
//   },
//   {
//     nombre: "TV Samsung 42",
//     precio: 7000.0,
//     codigo: "10102",
//     coloresDisponibles: ["Azul", "Plomo"],
//   },
//   {
//     nombre: "TV Samsung 39",
//     precio: 6000.0,
//     codigo: "10103",
//     coloresDisponibles: ["Azul"],
//   },
//   {
//     nombre: "TV Samsung 25",
//     precio: 5000.0,
//     codigo: "10104",
//     coloresDisponibles: [],
//   },
// ];

// for (let i = 0; i < productos.length; i++) {
//   console.log(`---Producto ${i + 1}---`);
//   console.log(`Nombre: ${productos[i].nombre}`);
//   console.log(`Precio: ${productos[i].precio}`);
//   console.log(`Codigo: ${productos[i].codigo}`);
//   console.log(`Colores Disponibles:`);
//   for (let j = 0; j < productos[i].coloresDisponibles.length; j++) {
//     console.log(productos[i].coloresDisponibles[j]);
//   }
// }


// //OBJETOS 2
// let objTienda = {
//   nombre: "Capricho",
//   categoria: "postres",
//   descripcion: "Tienda de postres arequipeños",
//   sucursales: [
//     {
//       nombre: "Capricho Mercaderes",
//       telefono: "974254652",
//     },
//     {
//       nombre: "Capricho Lambramani",
//       telefono: "974254111",
//     },
//     {
//       nombre: "Capricho EEUU",
//       telefono: "974220011",
//     },
//   ],
// };

// console.log(`------ CAPRICHO -----`);
// console.log(`Nombre: ${objTienda.nombre}`);
// console.log(`Categoria: ${objTienda.categoria}`);
// console.log(`Descripcion: ${objTienda.descripcion}`);
// console.log(`Sucursales:`);

// for (let i = 0; i < objTienda.sucursales.length; i++) {
//   console.log(`----------------`);
//   console.log(`Sucursal ${i + 1}`);
//   console.log(`Nombre: ${objTienda.sucursales[i].nombre}`);
//   console.log(`Telefono: ${objTienda.sucursales[i].telefono}`);
//   console.log(`----------------`);
// }



// // FUNCIONES (puede recibir cualquier tipo de dato como parametro)
// // 1. Funciones que no retornan valor ni reciben parametros
// // declarando una función
// function Saludar() {
//   console.log("Hello world");
// }
// // llamado a la funcion creada de saludar
// Saludar()

// // 2. Funciones que retornar valor y no reciben parametros
// // /** = con esto podemos documentar nuestra funcion
// function retornaNombre() {
//   let nombre = "Jhonatan";
//   return nombre;
// }
// let respuesta=retornaNombre()
// console.log(respuesta)

// // 3. Funciones que reciben parametros y retornan valor(una forma de reclarar cada funcion que utilizamos)
// /**
//  * Funcion que recibe dos numeros y calcula
//  * el binomio cuadrado perfecto de ambos
//  * @param {number} a primer numero
//  * @param {number} b segundo numero
//  * @return {number} El resultado del binomio
//  */
// function retornarBinomio(a, b) {
//   let rpta = a * a + 2 * a * b + b * b;
//   return rpta;
// }
// console.log(retornarBinomio(2,3))

// // 4. Funciones que no retornan valor y que reciben parametros
// function imprimirPares(numeros) {
//   for (let i = 0; i < numeros.length; i++) {
//     if (numeros[i] % 2 === 0) {
//       console.log(numeros[i]);
//     }
//   }
// }
// // invocando a la función 4
// let arreglo = [4, 20, 1, 0, 5, 63, 98];
// imprimirPares(arreglo);

// // //PARAMETROS POR DEFECTO DE UNA FUNCION 

// // let numero=5;
// // console.log(typeof numero)//define el tipo de dato 

// /**
//  * Funcion que recibe un arreglo de nombres y un nombre a buscar.
//  * Si el algoritmo encuentra el nombre buscado dentro del arreglo,
//  * retorna true, en caso contrario retorna false
//  * @param {array} nombres
//  * @param {string} busqueda
//  * @return {boolean}
//  */
// function buscarNombre(nombres = [], busqueda = "") {
//   for (let i = 0; i < nombres.length; i++) {
//     if (nombres[i] === busqueda) {
//       // la sentencia return en una función, no sólo retorna un valor
//       // sino que también hace que la función deje de ejecutarse en esa
//       // sentencia, no importa si está dentro un for, while, if, etc
//       return true;
//     }
//   }
//   // ¿que significa que el ciclo for acabe?
//   return false;
// }

// // let nombres = ["martin", "jaime", "anita", "paola", "daniel"];
// // let resultadoBusqueda = buscarNombre();
// // console.log(resultadoBusqueda);





// // // FUNCIONES ANONIMAS (las funciones anonimas son funciones cuyo valor se guarda en una variable.)

// //las funciones siempre se crean con CONST xk no se modifica buena practica
// const sumar = function (a, b) {//no tiene nombre es anonima
//   return a + b;
// };

// let rpta = sumar(7, 8);
// console.log(rpta);

// // FUNCIONES DE FLECHA ARROW FUNCTION
// const sumarFlecha = (a, b) => {//IGUALES A LAS ANONIMAS
//   return a + b;
// };
// console.log(sumarFlecha(500, 20));


// // FUNCIONES DENTRO DE OTRAS FUNCIONES
// const areaCirculo = (radio) => {
//   const PI = 3.1416;

//   const cuadrado = (numero) => {
//     return numero * numero;
//   };

//   return PI * cuadrado(radio);
// };

// let rpta2 = areaCirculo(13);
// console.log(rpta2);

// // //PARA CREAR NUESTROS PROPIOS SNIPPETS
// // //preferences/configure snippets/selecciona_lenguaje/GO
// // //el $1 permite dar tab y saltar de 1 a 1

// // 	// "nombre_snippets": {
// // 	// 	"prefix": "palabra_asignada_enter",
// // 	// 	"body": [
// // 	// 		"const $0mifuncion=($1)=>{$2}",
// // 	// 		"$2"
// // 	// 	],
// // 	// 	"description": "descripcion_de_esto"
// // 	// }
	

// // //CALLBACKS LLAMAR UNA FUNCION DENTRO OTRA FUNCION COMO PARAMETRO
// // const buscarPorDni = (dni, callback) => {
// //   // conecto a la BD
// //   // hago la consulta del dni
// //   // RETORNO LA INFORMACION DE LA PERSONA
// //   let nombreEncontrado = "-----";
// //   setTimeout(function () {
// //     console.log("Buscando en la base de datos");
// //     nombreEncontrado = "Jorge Garnica";
// //     callback(nombreEncontrado);
// //   }, 2000);
// // };

// // buscarPorDni("45875212", (nombre) => {
// //   console.log(nombre);
// // });

// // //FUNCIONES DE FLECHAS SIMPLIFICADAS
// // // Regla 1: Si la función sólo tiene una linea de ejecución
// // // se pueden omitir las llaves "{}"
// // const sumarE = (a, b) => console.log(a + b);
// // sumarE(52, 11);

// // // Regla 2: Si la función recibe 1 parametro solamente
// // // se pueden omitir los paréntesis
// // const cuadrado = numero => console.log(numero * numero);
// // cuadrado(12);

// // // Regla 3: Si la función sólo tiene una linea de ejecución y a su vez
// // // retorna un valor
// // // Se puede obviar la palabra reservada 'return ' y en su lugar, encerrar
// // // el retorno en un paréntesis
// // const cubo = n => (n*n*n);
// // console.log(cubo(5));















// //^ SEMANA 05
// //METODOS DE LOS STRING
// let frase = "Agua que no has de BEBER";
// let cantidadLetras = frase.length;
// console.log(`Cantidad de caracteres: ${cantidadLetras}`);

// /**
//  * string.toLowerCase()
//  * retorna una copia de la cadena de texto, convertida a minúsculas
//  */

// let minusculas = frase.toLowerCase();
// console.log(minusculas);
// frase=frase+'Holas'
// console.log(frase)

// /**
//  * string.toUpperCase()
//  * retorna una copia de la cadena de texto, convertida a mayúsculas
//  */

// let mayusculas = frase.toUpperCase();
// console.log(mayusculas);

// /**
//  * string.substr(posición_inicial, cantidad_de_caracteres_desde_posición_inicial)
//  * Retorna una subcadena dada una posición iniical y una cantidad de carateres
//  * a partir de dicha posición inical.
//  */

// let subcadena = frase.substr(0, 2);//Ag
// console.log(`substr: ${subcadena}`);

// /**
//  * string.substring(posición_inicial, posición_final-1)
//  * retorna una subcadena dada una posición inicial y una posición final
//  * ATENTION: la última posición no es considerada dentro de la subcadena de respuesta
//  */

// let subcadenaInicioFin = frase.substring(0, 2);//Ag
// console.log(`substring: ${subcadenaInicioFin}`);

// /**
//  * string.includes("subcadena_buscada")
//  * Retorna true si la "subcadena_buscada" existe en el string
//  * Retorna false si no existe
//  */

// let existeBEBER = frase.includes("BEBER");
// console.log(`¿BEBER está incluída?: ${existeBEBER}`);

// /**
//  * string.indexOf("subcadena")
//  * Retorna la posición inicial de la "subcadena buscada"
//  * si "subcadena" no existe, se retorna -1
//  */

// let posicionPalabraCadena = frase.indexOf("cadena");
// console.log(posicionPalabraCadena);

// let posicionPalabraCadenas = frase.indexOf("cadenas");
// console.log(posicionPalabraCadenas);

// /**
//  * string.trim()
//  * retorna una copia de la cadena
//  * SIN LOS ESPACIOS EN BLANCO a los extremos de dicha cadena
//  * Si la cadena tiene espacios intermedios, no los borra
//  */

// let fraseConEspacios = "    ups!              ";
// console.log(fraseConEspacios);
// console.log(fraseConEspacios.trim());

// //PROPIEDADES DE LOS ARREGLOS
// // arreglo.forEach(()=>{}) muestra lo que esta dentro
// /**
//  * El callback se ejecuta tantas veces como elementos
//  * tenga el arreglo, el callback recibe hasta 3 elementos
//  * (elemento_actual, iteracion?, copia_del_arreglo?)=>{}
//  */
// // ? significa que ese parámetro es opcional

// // peliculas.forEach((elemento) => {
// //   console.log(elemento);
// // });

// let arreglo = ["Jorge", "Luis", "Karla", "Jane"];
// arreglo.forEach((nombre) => {
//   console.log(nombre);
//   //   en cada vuelta pueden dibujar un producto
//   // en forma de card en el DOM para un E-COMMERCE creando una variable contenido
// });

// // ------ recorriendo peliculas
// peliculas.forEach((objPelicula, i) => {
//   console.log(`${i} : ${objPelicula.title}`);
//   // Desventaja: No se pueden retornars elementoses
//   // de la función forEach
// });

// // filter
// /**
//  * Funcion de los arreglos que recibe un callback en el cual
//  * se pueden RETORNAR un arreglo de elementos de acuerdo a ciertas condiciones
//  * Sirve como un filtro de elementos
//  * Ejecuta el callback tantas veces como elementos tenga
//  * (elemento_actual, iteracion?, copia_del_arreglo?)=>{}
//  */
// let numeros = [20, 1, 7, 82, 6, 9, 32, 10, 0, 45];

// let mayoresIgualesQueDiez = numeros.filter((elemento, i, arreglo) => {
//   if (elemento >= 10) {
//     return elemento;
//   }
// });
// console.log(mayoresIgualesQueDiez);

// let peliculasExtranjeras = peliculas.filter((objPelicula) => {
//   if (objPelicula.original_language !== "en") {
//     return objPelicula;
//   }
// });
// console.log(peliculasExtranjeras);


// //PROPIEDADES DE LOS ARREGLOS 2
// /**
//  * Devuelve un arreglo de la misma cantidad de elementos del arreglo }
//  * original con las transformaciones que el usuario le haga a cada elemento
//  * A diferencia del filter, la función map no puede retornar menos elementos
//  */
// console.log("///////map////////");
// let nombres = ["Joaquin", "Maria", "Thamara", "Allison", "Jorge"];
// let nombresMayusculas = nombres.map((name) => {
//   return {
//     original: name,
//     minuscula: name.toLowerCase(),
//     mayuscula: name.toUpperCase(),
//   };
// });
// console.log(nombresMayusculas);

// // ------------------------
// // array.splice(posicion_inicia, elementos_a_eliminar, elementos_a_insertar)
// console.log("///////////SPLICE//////////");
// let productos = [
//   "TV Samsung",
//   "Tablet Android",
//   "Laptop Razer",
//   "Smartphone Xiaomi",
// ];
// // A partir de la posición 1, eliminar 1 elemento
// productos.splice(1, 1);
// console.log(productos);
// // A partir de la posición 0, eliminar 1 elemento e insertar el elemento "PC gamer"
// productos.splice(0, 1, "PC gamer");
// console.log(productos);
// // A partir de la posición 2, no eliminar elementos e insertar 2 nuevos elementos
// productos.splice(2, 0, "Mouse HyperX", "Audífonos Razer");
// console.log(productos);

// // --------- indexOf -------
// console.log("/////indexOf////");
// let posicionMouse = productos.indexOf("Mouse HyperX");
// console.log("Posición del mouse:");
// console.log(posicionMouse);

// // -------- pop -----------
// // Sirve para extraer el último de un arreglo
// // la función además, retorna dicho elemento
// console.log("//////////////pop////////////");
// let elementoEliminado = productos.pop();
// console.log(`Eliminaste: ${elementoEliminado}`);
// console.log(productos);


// //PROPIEDADES CON FECHAS
// // Date() clase cuyos objetos trabajan con fechas
// let hoy = new Date();
// console.log(hoy);

// /**
//  * getFullYear()  retorna el año de una variable de tipo fecha
//  */
// let anioActual = hoy.getFullYear();
// console.log("Año actual:");
// console.log(anioActual);

// /**
//  * getMonth() retorna el mes de una viable de tipo fecha
//  * OJO: enero empieza con el valor 0, Diciembre 11
//  */
// let mesActual = hoy.getMonth();
// console.log("Mes actual:");
// console.log(mesActual);

// /**
//  * getDate() retorna el día del calendario de una variable DATE
//  */
// let diaCalendarioActual = hoy.getDate();
// console.log("Dia calendario actual:");
// console.log(diaCalendarioActual);

// let stringFecha = `${diaCalendarioActual}-${mesActual + 1}-${anioActual}`;
// console.log("Fecha en String");
// console.log(stringFecha);

// /**
//  * Función que retorna el número del día de la semana empezando desde el 0
//  * como domingo
//  */
// let diaSemana = hoy.getDay();
// console.log("Dia de la semana");
// console.log(diaSemana);

// let horaActual = hoy.getHours();
// let minutoActual = hoy.getMinutes();
// let segundoActual = hoy.getSeconds();
// let milisegundoActual = hoy.getMilliseconds();

// console.log(`hora Actual: ${horaActual}`);
// console.log(`minuto Actual: ${minutoActual}`);
// console.log(`segundo Actual: ${segundoActual}`);
// console.log(`milisegundo Actual: ${milisegundoActual}`);

// // Iniciar una variable de tipo fecha
// // ubicado en navidad por ejemplo
// // new Date(anio?,mes?,dia?,horas?,minutos?,segundos?);
// let navidad2020 = new Date(2020, 11, 25);
// console.log(navidad2020);


// // la diferencia de las fechas en millisegundos
// let navidadMenosHoy = navidad2020 - hoy;

// let semanasParaNavidad = ((((navidadMenosHoy/1000)/60)/60)/24)/7;

// console.log(`Semanas para navidad: ${semanasParaNavidad}`);


// //PROPIEDADES CON MATH
// // La clase Math
// // es una clase ESTÁTICA
// // CLASE ESTÁTICA: Clase de la cual no se crean variables
// // que nos provee de funciones matematicas

// // Ejm: Math.sqrt(numero)
// let raizDe25 = Math.sqrt(25);
// console.log(raizDe25);

// //  Math.floor(numero_decimal)
// // Redondea un numero al proximo entero inferior
// // Ejm Math.floor(5.99999999) = 5
// console.log(Math.floor(12.999999));

// // Math.ceil(numero_decimal)
// // Redondea un numero al proximo entero superior
// // Ejm: Math.ceil(0.2);
// console.log(Math.ceil(0.2));

// // Math.round(numero_decimal)
// // Redondea un número respetando las formas normales de redondeo
// // Ejm: Math.round(3.2) = 3
// // Ejm: Math.round(3.6) = 4

// console.log(Math.round(2.5));

// // Math.random() => genera un numero aleatorio
// // entre 0 y 1

// let aleatorio = Math.random();
// console.log(aleatorio);

// // Math.random() * (max-min) + min
// // genera un número aleatorio entre 'min' y 'max'

// let aleatorioQuinceYCien = Math.random() * (100 - 15) + 15;
// console.log(aleatorioQuinceYCien);

// // numero.toFixed(numero_de_decimales)
// console.log(aleatorioQuinceYCien.toFixed(2));

// let precio = 99.57;
// console.log(precio.toFixed(1));

// // Considerar la acción de un cajero automático para retirar dinero
// // de forma que los billetes estén bien distribuidos
// // 500 SOLES = 2 billetes de 200 y 1 de 100
// // 190 soles = 1=>100 1=>50 2=>20
// // intenten sacar módulos %100 %10 
// // considerando que la máxima cantidad es: 9000

// //CLASES 
// // 1 modelo de necegocio es narrar todo lo que quieres que haga tu aplicacion
// // 2 obtener requerimientos

// /**
//  * Los nombres de las clases deben iniciar con una Mayúscula
//  */
// class Restaurant {
//   aforo;
//   nroMesas;
//   direccion;
//   categoria;
//   telefonos;
//   nombre;
//   delivery;
//   /**
//    * Para la 'tipificacion':
//    * Será tipo "A" si el aforo es mayor a 500 personas
//    * Será tipo "B" si es aforo es mayor a 300 personas
//    * Será tipo "C" si el aforo es menor igual a 300 personas
//    */
//   tipificacion;

//   /**
//    * Funcion que se ejecuta automaticamente al momento de crear un objeto
//    * da valores iniciales a un objeto
//    */
//   constructor(
//     _aforo = 0,
//     _nroMesas = 0,
//     _direccion = "Sin Dirección",
//     _categoria = "Sin Categoria",
//     _telefonos = [],
//     _nombre = "Sin Nombre",
//     _delivery = false
//   ) {
//     // this : acceder al scope interno de la clase.
//     // this: se usa para acceder a los atributos y métodos de la clase.
//     this.aforo = _aforo;
//     this.nroMesas = _nroMesas;
//     this.direccion = _direccion;
//     this.categoria = _categoria;
//     this.telefonos = _telefonos;
//     this.nombre = _nombre;
//     this.delivery = _delivery;

//     //podemos hacer evaluaciones o comparaciones 
//     if (this.aforo > 500) {
//       this.tipificacion = "A";
//     } else if (this.aforo > 300) {
//       this.tipificacion = "B";
//     } else {
//       this.tipificacion = "C";
//     }
//   }
//   //asi se crean los metodos dentro de una clase
//   imprimirTelefonos() {
//     console.log(`Teléfonos del restaurant: ${this.nombre}`);
//     for (let i = 0; i < this.telefonos.length; i++) {
//       console.log(`📞 ${this.telefonos[i]}`);
//     }
//   }

//   imprimirTelefonos2() {
//     for (const tel of this.telefonos) {
//       console.log(`Telefono: ${tel}`);
//     }
//   }

//   toString() {
//     return this.nombre;
//   }

// }

// // Instanciando una clase : Creando un objeto a partir de una clase
// let objTanta = new Restaurant(
//   800,
//   200,
//   "Vallecito",
//   "Comida Criolla",
//   ["974204853", "974854512"],
//   "Tanta",
//   true
// );

// let objAstrid = new Restaurant();

// // Modificando los atributos de un objeto
// // objAstrid.aforo = 1000;

// console.log(objTanta);
// console.log(objAstrid);

// objTanta.imprimirTelefonos();
// objTanta.imprimirTelefonos2();


// //OBJETO WINDOW
// // window => objeto que representa al navegador
// // y todas sus propiedades internas
// // es un objeto global

// // Obtener la altura y el ancho del viewport de la pantalla si lo achico otra medida tendra y asi.
// let alto = window.innerHeight;
// let ancho = window.innerWidth;

// console.log(`Alto: ${alto}`);
// console.log(`Ancho: ${ancho}`);

// // window.location contiene un obj con información
// // de la dirección que se está visitando a través del navegador
// // el puerto, href, dominio,hash, etc
// let navegacion = window.location;
// console.log(navegacion);

// let url = navegacion.href;
// console.log(url);

// console.log(navegacion);

// // window.document => objeto que tiene toda la información
// // DEL DOM!!!!!!!!!!!!! todas sus etiquetas etc la estructura completa
// console.log(window.document);






// //WINDOW.DOCUMENT
// // document => objeto que sirve para manipular el DOM
// // propiedades más importantes
// /**
//  * document.getElementById("id_del_elemento"); => obtiene en una variable
//  * la referencia a un elemento del DOM
//  *
//  *  */

// {/* <header id="header"> */}//lo capturamos con el id a cualquier etiqueta
// let header = document.getElementById("header");
// // header es un objeto de la clase "ELEMENT"
// console.log(`header: ${header}`);

// /**
//  * document.getElementsByClassName("nombre_de_la_clase");
//  * retorna un HTMLCollection(similar a un arreglo) de elementos
//  * que tengan la clase pasada como parámetro
//  */
// let secciones = document.getElementsByClassName("miseccion");
// console.log(secciones);
// console.log("Cantidad de Secciones");
// console.log(secciones.length);

// // Transformar la el HTMLCollection a un Array

// let seccionesArreglo = Array.from(secciones);
// console.log(seccionesArreglo);
// seccionesArreglo.forEach((seccion) => {
//   console.log(seccion);
// });

// /**
//  * document.querySelector("selector_de_un_elemento")
//  * Retorna un elemento del DOM dado un selector al estilo CSS
//  * Por ejemplo .rojo => un elemento con la clase "rojo"
//  * Por ejemplo #seccion1 => un elemento con el id "seccion1"
//  * OJO: querySelector sólo devuelve 1 elemento
//  */

// let footerApp = document.querySelector("#footerApp");
// console.log(footerApp);

// /**
//  * document.querySelectorAll("selector_de_uno_o_mas_elementos");
//  * Retorna una colección de elementos del DOM dado un selector como en  CSS
//  */
// let divsFooter = document.querySelectorAll(".footerApp__seccion");
// console.log(divsFooter);

// divsFooter.forEach((div) => {
//   console.log(div);
// });


// let navegacion = document.querySelector("#navegacion");
// console.log(navegacion);













// let body = document.querySelector("body");

// // Colocando estilos desde JavaScript
// body.style.backgroundColor = "#444444";

// // elemento.classList()
// /**
//  * Atributo que permite trabajar con las clases de un elemento
//  * como añadir clase, listar las clases que elelemento tiene
//  * quitar una clase y hasta agregar/quitar clase como un interruptor
//  */
// let header = document.querySelector("header");
// console.log("Lista de clases del elemento");
// console.log(header.classList);

// /**
//  * elemento.classList.add("nombre(s)_de_clase(s) separados por comas")
//  * Añade una clase a un elemento del DOM
//  * TODO: remove, contains
//  */

// header.classList.add("header");

// // elemento.clientWidth => Devuelve el ancho del elemento
// // elemento.clientHeight => Devuelve la altura de un elemento
// let seccion1 = document.querySelector(".seccion1");
// console.log(`Ancho de .seccion1: ${seccion1.clientWidth}`);
// console.log(`Alto de .seccion1: ${seccion1.clientHeight}`);

// //elemento.offsetTop => Devuelve la cantidad pixeles que el elemento
// // dista con la parte superior del viewport

// //elemento.offsetLeft => Devuelve la cantidad pixeles que el elemento
// // dista con la parte izquierda del viewport

// console.log(`Pixeles desde top .seccion1: ${seccion1.offsetTop}`);
// console.log(`Pixeles desde left .seccion1: ${seccion1.offsetLeft}`);

// //elemento.scrollTop => Devuelve la cantidad de pixeles que el elemento
// // lleva como scroll interno
// console.log(`Seccion1 scrollTop: ${seccion1.scrollTop}`);

// let html = document.querySelector("html");

// console.log(`html scrollTop: ${html.scrollTop}`);

// let imagen = document.querySelector("img");

// // let altoPantalla = window.innerHeight;

// body.onscroll = (e) => {
//   let scrollAbajo = html.scrollTop;

//   if (scrollAbajo > 200) {
//     imagen.style.height = "200px";
//   } else {
//     imagen.style.height = scrollAbajo + "px";
//   }
// };


// //juego de prender y apagar
// let btnLight = document.getElementById("btnLight");
// let btnDarks = document.getElementById("btnDarks");
// let btnToggle = document.getElementById("btnToggle");
// let seccion1 = document.querySelector(".seccion1");
// // Evento Click

// btnLight.onclick = () => {
//   if (seccion1.classList.contains("sombra-darks") === true) {
//     seccion1.classList.remove("sombra-darks");
//   }
//   seccion1.classList.add("sombra-light");
// };

// btnDarks.onclick = () => {
//   if (seccion1.classList.contains("sombra-light") === true) {
//     seccion1.classList.remove("sombra-light");
//   }
//   seccion1.classList.add("sombra-darks");
// };

// btnToggle.onclick = () => {
//   if (seccion1.classList.contains("sombra-light") === true) {
//     seccion1.classList.remove("sombra-light");
//     seccion1.classList.add("sombra-darks");
//   } else if (seccion1.classList.contains("sombra-darks") === true) {
//     seccion1.classList.remove("sombra-darks");
//     seccion1.classList.add("sombra-light");
//   } else {
//     seccion1.classList.add("sombra-light");
//   }
// };

// ^ SEMANA 06

// BUEN EJEMPLO DE COMO PODEMOS TRAER DATOS EN UN SELECT 
// <!DOCTYPE html>
// <html lang="en">
//   <head>
//     <meta charset="UTF-8" />
//     <meta name="viewport" content="width=device-width, initial-scale=1.0" />
//     <script src="./data-peliculas.js"></script>
//     <title>Document</title>
//   </head>
//   <body>
//     <header>
//       <h1>Titulo 1</h1>
//     </header>
//     <main>
//       <button id="btnTitulo1">Cambiar a titulo 2</button>
//       <button id="btnTitulo2">Cambiar a titulo 3</button>
//       <form>
//         <div>
//           <label for="selectPeliculas">Lista de Peliculas</label>
//           <select name="" id="selectPeliculas"> </select>
//         </div>
//         <button type="button" id="btnSelect">Llenar Select</button>
//       </form>
//     </main>

//     <script src="./01-element3.js"></script>
//   </body>
// </html>

// let btnTitulo1 = document.querySelector("#btnTitulo1");
// let btnTitulo2 = document.querySelector("#btnTitulo2");
// let h1 = document.querySelector("h1");
// let selectPeliculas = document.getElementById("selectPeliculas");
// let btnSelect = document.getElementById("btnSelect");

// btnTitulo1.onclick = () => {
//   /**
//    * elemento.innerText => settea el contenido de una etiqueta
//    * OJO, se debe considerar sólo el contenido a nivel
//    * de texto y NO HTML
//    */
//   h1.innerText = "Nuevo <strong>título</strong> 1";
// };

// btnTitulo2.onclick = () => {
//   /**
//    * elemento.innerHTML => settea el contenido de una etiqueta
//    * a nivel de texto y también reconoce etiquetas HTML
//    */
//   h1.innerHTML = "Nuevo <strong>título</strong> 2";
// };

// // metodo que se encarga de obtener todos los datos y colocarlo en un selec como podenos observar
// const llenarSelect = () => {
//   let contenido = "";
//   peliculas.forEach((objPelicula, i) => {
//     contenido =
//       contenido +
//       `<option value="${objPelicula.id}">${objPelicula.title}</option>`;
//   });
//   selectPeliculas.innerHTML = contenido;
// };
// //metodo que se ejecutara cuando le haga click llamara ala funcion y se ejecutara
// btnSelect.onclick = () => {
//   llenarSelect();
// };


// EJEMPLO DE COMO MOSTRAR NUMEROS ALEATORIOS
// <!DOCTYPE html>
// <html lang="en">
//   <head>
//     <meta charset="UTF-8" />
//     <meta name="viewport" content="width=device-width, initial-scale=1.0" />
//     <title>Document</title>
//     <style>
//       .lista-item {
//         color: red;
//         cursor: pointer;
//       }
//       .lista-item:hover {
//         transform: scale(1.1);
//         color: blue;
//       }
//     </style>
//   </head>
//   <body>
//     <section>
//       <h4>Números de lotería</h4>
//       <button id="btnGenerar">Generar nuevo número</button>
//       <ul id="lista"></ul>
//     </section>

//     <script src="./02-element4.js"></script>
//   </body>
// </html>

// let lista = document.getElementById("lista");
// let btnGenerar = document.getElementById("btnGenerar");


// la diferencia aqui es que hago un click y muestro un valor pero en el anterior hago un click y traigo todos los datos x eso no creamos elementos si un contenido con un forEach
// btnGenerar.onclick = () => {
//   /**
//    * document.createElement("etiqueta_del_elemento")
//    * retorna un elemento HTML que aún no está en el DOM
//    * imaginemos que dicho elemento está en el limbo
//    */
//   let liTemporal = document.createElement("li");
//   let numeroAleatorio = (Math.random() * (45 - 1) + 1).toFixed(0);
//   liTemporal.innerText = numeroAleatorio;
//   /**
//    * elemento.setAttribute("nombre_del_atributo","valor_del_atributo")
//    * Coloca un atributo al elemento con un respectivo valor
//    * (hablamos de atribbutos HTML ejm: id, class, border, name, value)
//    */
//   liTemporal.setAttribute("class", "lista-item");
//   liTemporal.onclick = () => {
//     console.log(`Uy! alguien está haciendo click en ${numeroAleatorio}`);
//   };

//   // liTemporal.addEventListener("click",()=>{
//   //   console.log("bla bla bla")
//   // })

//   /**
//    * elemento.appenChild(elemento), agrega como hijo final al elemento
//    * recibido por parámetros
//    *
//    * elemento.before(elemento), análogamente, inserta un hijo al inicio
//    * de los elementos hijos
//    */
//   lista.appendChild(liTemporal);

//   /**
//    * Reto:
//    * - permitir como máximo 7 números de lotería
//    * - validar que si un número se repite, salga otro
//    * HINT: Usar un arreglo para guardar los números y sacar la cantidad de números
//    */
// };
// /**
//  * document.onkeyup=(e)=>{if(e.key==="x"){hacer algo aqui}}
//  * html
//  */


// EJEMPLO DE MOSTRAR LOS DATOS EN UNA TABLA Y PRESIONAR EL BOTON DE ELIMINAR Y QUE SE ACTUALIZA Y NO MUESTRE SOLO LO RESTANTE

// <!DOCTYPE html>
// <html lang="es">
//   <head>
//     <meta charset="UTF-8" />
//     <meta name="viewport" content="width=device-width, initial-scale=1.0" />
//     <script src="./data-coronavirus.js"></script>
//     <title>Document</title>
//   </head>
//   <body>
//     <table border="1">
//       <thead>
//         <tr>
//           <th>Nro</th>
//           <th>País</th>
//           <th>Infectados 😣</th>
//           <th>Fallecidos 😥</th>
//           <th>Recuperados 😀</th>
//           <th>Acciones</th>
//         </tr>
//       </thead>
//       <tbody id="tbody"></tbody>
//     </table>

//     <script src="./03-element5.js"></script>
//   </body>
// </html>


// /**
//  * EJERCICIO
//  * Recorrer el arreglo "covid" para poblar la tabla
//  * y agregar filas y columnas con la información que sugieren
//  * las cabeceras de la tabla
//  * No se debe obedecer a ningún click, el proceso debe ser ni bien cargue
//  * la página
//  */

// let tbody = document.getElementById("tbody");

// const llenarTabla = () => {
//   /**
//    * 1. iterar el arreglo covid
//    * 2. en cada vuelta crear una fila y 5 columnas
//    * 3. agregar las columnas a la fila
//    * 4. al final de cada vuelta, agregar la fila al tbody
//    */
//   covid.forEach((objPais, i) => {
//     let fila = document.createElement("tr");

//     let tdNro = document.createElement("td");
//     tdNro.innerText = i + 1;

//     let tdPais = document.createElement("td");
//     tdPais.innerText = objPais.country;

//     let tdInfectados = document.createElement("td");
//     tdInfectados.innerText = objPais.cases;

//     let tdFallecidos = document.createElement("td");
//     tdFallecidos.innerText = objPais.deaths;

//     let tdRecuperados = document.createElement("td");
//     tdRecuperados.innerText = objPais.recovered;

//     let tdAcciones = document.createElement("td");
//     let btnEliminar = document.createElement("button");
//     btnEliminar.innerHTML = "Eliminar";
//     btnEliminar.onclick = () => {
//       let rpta = confirm(`¿Estás seguro de eliminar ${objPais.country}?`);
//       if (rpta) {
//         // PERMITE OCULTAR ESA FILA
//         fila.setAttribute("hidden", "hidden");
//       }
//     };

//     tdAcciones.appendChild(btnEliminar);

//     fila.appendChild(tdNro);
//     fila.appendChild(tdPais);
//     fila.appendChild(tdInfectados);
//     fila.appendChild(tdFallecidos);
//     fila.appendChild(tdRecuperados);
//     fila.appendChild(tdAcciones);

//     tbody.appendChild(fila);
//   });
// };
// llenarTabla();



// //EJERCICIO DE CAMBIAR EL MODO LIGHT A MODO DARK
// <!DOCTYPE html>
// <html lang="en">
//   <head>
//     <meta charset="UTF-8" />
//     <meta name="viewport" content="width=device-width, initial-scale=1.0" />
//     <link rel="stylesheet" href="./01-eventos-light.css" />
//     <link rel="stylesheet" href="" id="linkDark" />

//     <style>
//       .cuadrado {
//         width: 200px;
//         height: 200px;
//         background-color: crimson;
//         margin: 20px auto 0 auto;
//         position: relative;
//       }
//       .bolita {
//         width: 5px;
//         height: 5px;
//         background-color: yellow;
//         border-radius: 50%;
//         position: absolute;
//         display: none;
//         pointer-events: none;
//       }
//       .sombra {
//         box-shadow: 0px 0px 10px #888;
//       }
//     </style>
//     <title>Document</title>
//   </head>
//   <body>
//     <header class="header">
//       <div class="header__contenedor">
//         <div class="header__logo">
//           <img src="./logo.svg" alt="logo" />
//         </div>
//         <nav class="header__navegacion">
//           <ul class="header__lista">
//             <li class="header_item">
//               <a href="#" class="header_link">Inicio</a>
//             </li>
//             <li class="header__item">
//               <a href="#" class="header__link">Cursos</a>
//             </li>
//             <li class="header__item">
//               <a href="#" class="header__link">Proyectos</a>
//             </li>
//             <li class="header__item">
//               <a href="#" class="header__link">Contacto</a>
//             </li>
//           </ul>
//         </nav>
//       </div>
//     </header>

//     <button id="btnDark">
//       Estilo Dark
//     </button>
//     <button id="btnLight">
//       Estilo Light
//     </button>

//     <button id="btnToggle" class="btn-toggle">
//       Cambiar Estilo
//     </button>

//     <div id="cuadrado" class="cuadrado"></div>
//     <div id="cuadrado2" class="cuadrado"></div>
//     <div id="cuadrado3" class="cuadrado"></div>

//     <script src="./01-eventos.js"></script>
//   </body>
// </html>

// let btnLight = document.getElementById("btnLight");
// let btnDark = document.getElementById("btnDark");
// let btnToggle = document.getElementById("btnToggle");
// let linkDark = document.getElementById("linkDark");
// let cuadrado = document.getElementById("cuadrado");
// let cuadrado2 = document.getElementById("cuadrado2");
// let cuadrado3 = document.getElementById("cuadrado3");

// btnLight.onclick = () => {
//   console.log("click en light");
//   /**
//    * elemento.getAttribute("nombre_del_atributo")
//    * Retorna el valor de un atributo de un elemento
//    */
//   // let href = linkDark.getAttribute("href");
//   linkDark.setAttribute("href", "");
// };
// btnDark.addEventListener("click", () => {
//   linkDark.setAttribute("href", "./01-eventos-dark.css");
// });
// btnToggle.onclick = (e) => {
//   console.log(e);

//   let href = linkDark.getAttribute("href");
//   if (href.length > 0) {
//     // está en dark
//     linkDark.setAttribute("href", "");
//   } else {
//     linkDark.setAttribute("href", "./01-eventos-dark.css");
//   }
// };

// cuadrado.onclick = (e) => {
//   console.log(e);
//   console.log(`Tipo de evento => ${e.type}`);
//   console.log("Elemento objetivo del evento:");
//   console.log(e.target);
//   console.log(`Valores de X e Y con respecto al VIEWPORT`);
//   console.log(`X => ${e.clientX} - Y => ${e.clientY}`);
//   console.log(`Valores de X e Y con respecto al MISMO ELEMENTO`);
//   console.log(`X => ${e.offsetX} - Y => ${e.offsetY}`);
// };

// /**
//  * elemento.onmousemove
//  * evento que se desencadena cuando el mouse se mueve por encima del elemento
//  */

// cuadrado2.onmousemove = (e) => {
//   let x = e.offsetX;
//   let y = e.offsetY;
//   if (e.ctrlKey) {
//     let bolita = document.createElement("div");
//     bolita.style.left = x + "px";
//     bolita.style.top = y + "px";
//     bolita.style.display = "block";
//     bolita.classList.add("bolita");
//     cuadrado2.appendChild(bolita);
//   }
// };

// /**
//  * elemento.onmouseover
//  * evento que se ejecuta cuando el mouse pasa por encima del elemento
//  * A diferencia de mousemove, el evento sólo se dispara UNA VEZ, cuando el mouse
//  * ingresa al elemento.
//  * SIMILAR A HOVER (CSS)
//  */

// cuadrado3.onmouseover = (e) => {
//   console.log(e);
//   cuadrado3.classList.add("sombra");
// };

// cuadrado3.onmouseleave = (e) => {
//   console.log(e);
//   cuadrado3.classList.remove("sombra");
// };

// //EVENTOS DE FORMULARIO 
// EJEMPLO DE COMO CREAR UN CORREO QUE NO ESTE EN LA BASE DE DATOS Y QUE CUANDO SI ESTE MANDE UN MENSAJE EN SMALL DE QUE ESE CORREO YA EXISTE VERIFICANDO QUE YA ESTE ESO
// <!DOCTYPE html>
// <html lang="en">
//   <head>
//     <meta charset="UTF-8" />
//     <meta name="viewport" content="width=device-width, initial-scale=1.0" />
//     <script src="./data-usuarios.js"></script>
//     <script src="./02-eventos-formularios.js"></script>
//     <title>Document</title>
//     <style>
//       body {
//         background-color: #eee;
//       }
//       form {
//         background-color: #fff;
//         padding: 30px;
//         border-radius: 10px;
//         box-shadow: 0px 0px 20px #888;
//         width: 500px;
//         margin: 20px auto 0px auto;
//       }
//       form input {
//         width: 100%;
//       }
//       .text-success {
//         color: #30a720;
//       }
//       .text-danger {
//         color: crimson;
//       }
//       .input-success {
//         border: 1px solid #30a720;
//         outline: 1px solid #30a720;
//       }
//       .input-danger {
//         border: 1px solid crimson;
//         outline: 1px solid crimson;
//       }
//     </style>
//   </head>
//   <body>
//     <form id="formulario">
//       <p>
//         <label>Usuario</label>
//         <input type="email" id="inputEmail" placeholder="Ingrese su correo" />
//         <small id="helperEmail"></small>
//       </p>
//       <p>
//         <label>Contraseña</label>
//         <input type="password" id="inputPassword" />
//       </p>
//       <button type="submit">Iniciar Sesión</button>
//       <a href="https://www.google.com" id="enlace">¿Olvidaste tu contraseña?</a>
//     </form>
//   </body>
// </html>


// /**
//  * elemento.onload
//  * función que se dispara cuando se han cargado todos los elementos hijos
//  * de un elemento
//  */
// window.onload = () => {
//   let formulario = document.getElementById("formulario");
//   let inputPassword = document.getElementById("inputPassword");
//   let inputEmail = document.getElementById("inputEmail");
//   let enlace = document.getElementById("enlace");
//   let helperEmail = document.getElementById("helperEmail");

//   const validarEmail = (email) => {
//     let regexEmail = /^(([^<>()\[\]\\.,;:\s@"]+(\.[^<>()\[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/;

//     if (regexEmail.test(email) === false) {
//       helperEmail.innerText = "Error, ingrese un correo válido";
//       helperEmail.setAttribute("class", "text-danger");
//     } else {
//       let resultados = usuarios.filter((objUsuario) => {
//         if (objUsuario.correo === email) {
//           return objUsuario.correo;
//         }
//       });

//       if (resultados.length > 0) {
//         helperEmail.innerText = "ERRORSH! el email ya está siendo usado";
//         helperEmail.classList.remove("text-success");
//         helperEmail.classList.add("text-danger");
//         inputEmail.setAttribute("class", "input-danger");
//       } else {
//         helperEmail.innerText = "BIEN! el email está disponible";
//         helperEmail.classList.remove("text-danger");
//         helperEmail.classList.add("text-success");
//         inputEmail.setAttribute("class", "input-success");
//       }
//     }
//   };

//   // const validarEmail = (email) => {
//   //   let resultados = usuarios.filter(
//   //     (objUsuario) => objUsuario.correo === email
//   //   );

//   //   helperEmail.innerText =
//   //     resultados.length > 0
//   //       ? "ERRORSH! el email ya está siendo usado"
//   //       : "BIEN! el email está disponible";
//   // };

//   /**
//    * Funcion que se ejecuta cuando una tecla es presionada y soltada
//    * sobre un elemento objetivo
//    * @param {*} e
//    */
//   inputEmail.onkeyup = (e) => {
//     // console.log(e);
//     // console.log(e.key);
//     // console.log("presionando una tecla");

//     validarEmail(inputEmail.value.trim());
//   };

//   /**
//    * formulario.onsubmit, evento que se ejecuta cuando se hace
//    * submit en un formulario
//    */
//   formulario.onsubmit = (e) => {
//     /**
//      * preventDefault => previene todas las acciones automaticas
//      * disparadas por cualquier evento
//      * ejm: el CLICK en un enlace <a> redirecciona a una pagina
//      * ejm: el SUBMIT de un formulario envía datos al server
//      * y actualiza la página
//      * ejm: el CLICK DERECHO en cualquier zona, abre un menu
//      * contextual en la página
//      * CONCLUSIÓN: cualquiera de estos eventos pueden ser evitados
//      */
//     e.preventDefault();
//     console.log("submit del formulario");

//     let objetoUsuario = {
//       usuario: inputEmail.value,
//       password: inputPassword.value,
//     };
//     console.log("Enviando......");
//     console.log(objetoUsuario);
//   };
//   enlace.onclick = (e) => {
//     e.preventDefault();
//   };
// };


// EJEMPLO DE YO SELECCIONO UN PAIZ Y ESTE RECIEN ME MUESTRA LAS PROVINCIAS RELACIONADAS MIENTRAS ESTA INACTIVADO

// <!DOCTYPE html>
// <html lang="en">
//   <head>
//     <meta charset="UTF-8" />
//     <meta name="viewport" content="width=device-width, initial-scale=1.0" />
//     <script src="./data-lugares.js"></script>
//     <title>Document</title>
//     <style>
//       body {
//         background-color: #eee;
//       }
//       form {
//         background-color: #fff;
//         padding: 30px;
//         border-radius: 10px;
//         box-shadow: 0px 0px 20px #888;
//         width: 500px;
//         margin: 20px auto 0px auto;
//       }
//       form input {
//         width: 100%;
//       }
//     </style>
//   </head>
//   <body>
//     <form>
//       <p>
//         <label>Pais:</label>
//         <select name="" id="selectPais"></select>
//       </p>
//       <p>
//         <label>Departamento</label>
//         <select name="" id="selectDepartamento" disabled="disabled"></select>
//       </p>
//     </form>

//     <script src="./01-eventos-formulario2.js"></script>
//   </body>
// </html>

// let selectPais = document.getElementById("selectPais");
// let selectDepartamento = document.getElementById("selectDepartamento");

// const poblarPaises = () => {
//   let options = "<option value=0>--- Seleccione un País ---</option>";

//   paises.forEach((objPais) => {
//     options += `<option value="${objPais.id}">${objPais.nombre}</option>`;
//   });

//   selectPais.innerHTML = options;
// };

// poblarPaises();

// const llenarDepartamentosByIdPais = (idPaisSeleccionado) => {
//   let depasTemporales = departamentos.filter(
//     (objDepartamento) => objDepartamento.paisId === idPaisSeleccionado
//   );

//   if (depasTemporales.length === 0) {
//     selectDepartamento.innerHTML = "";
//     selectDepartamento.setAttribute("disabled", "disabled");
//     return;
//   }

//   let options = "<option value=0>---Seleccione---</option>";
//   depasTemporales.forEach((objDepa) => {
//     options += `<option value="${objDepa.id}">${objDepa.nombre}</option>`;
//   });
//   selectDepartamento.innerHTML = options;
//   selectDepartamento.removeAttribute("disabled");
// };

// /**
//  * elemento.onchange evento que se ejecuta cada vez que el valor de un elemento
//  * cambia (en el caso del select, cada vez que un nuevo option es seleccionado)
//  * @param {*} e
//  */
// selectPais.onchange = (e) => {
//   console.log(e);
//   let idPaisSeleccionado = +selectPais.value;
//   llenarDepartamentosByIdPais(idPaisSeleccionado);
// };


// EJEMPLO DE COMO CREAR UN FORMULARIO Y ENVIAR LOS DATOS SELECCIONADOS Y DATOS AL SERVIDOR

// <!DOCTYPE html>
// <html lang="en">
//   <head>
//     <meta charset="UTF-8" />
//     <meta name="viewport" content="width=device-width, initial-scale=1.0" />
//     <title>Document</title>
//     <style>
//       body {
//         background-color: #eee;
//       }
//       form {
//         background-color: #fff;
//         padding: 30px;
//         border-radius: 10px;
//         box-shadow: 0px 0px 20px #888;
//         width: 500px;
//         margin: 20px auto 0px auto;
//       }
//       form input {
//         width: 100%;
//       }
//     </style>
//   </head>
//   <body>
//     <form id="formulario">
//       <p>
//         <label for="inputNombre">Nombres:</label>
//         <input type="text" name="nombre" id="inputNombre" />
//       </p>
//       <p>
//         <label for="inputApellido">Apellidos:</label>
//         <input type="text" name="apellido" id="inputApellido" />
//       </p>
//       <p>
//         <label for="inputFecha">Fecha Nacimiento:</label>
//         <input type="date" name="fecha" id="inputFecha" />
//       </p>
//       <p>
//         <label><strong> Seleccione turno:</strong></label>
//         <br />
//         <label for="">Mañana</label>
//         <input type="radio" value="manana" name="turno" id="inputTurnoM" checked />
//         <label for="">Tarde</label>
//         <input type="radio" value="tarde" name="turno" id="inputTurnoT" />
//         <label for="">Noche</label>
//         <input type="radio" value="noche" name="turno" id="inputTurnoN" />
//       </p>
//       <button type="submit">Enviar Formulario</button>
//     </form>

//     <script src="./01-eventos-formularios3.js"></script>
//   </body>
// </html>


// let inputNombre = document.getElementById("inputNombre");
// let inputApellido = document.getElementById("inputApellido");
// let inputFecha = document.getElementById("inputFecha");
// let formulario = document.getElementById("formulario");

// let inputTurnoM = document.getElementById("inputTurnoM");
// let inputTurnoT = document.getElementById("inputTurnoT");
// let inputTurnoN = document.getElementById("inputTurnoN");

// let objFormulario = {
//   nombre: "",
//   apellido: "",
//   fecha: "",
//   turno: "manana",
// };

// const actualizarObjFormulario = (event) => {
//   objFormulario[event.target.name] = event.target.value;
// };

// inputNombre.onkeyup = actualizarObjFormulario;
// inputApellido.onkeyup = actualizarObjFormulario;
// inputFecha.onchange = actualizarObjFormulario;
// /**
//  * al ejecutar el evento onchange de multiples radioButtons con el mismo "name"
//  * sólo se ejecuta en el radio que acaba de ser seleccionado, NO EN LOS DEMÁS
//  */
// inputTurnoM.onchange = actualizarObjFormulario;
// inputTurnoT.onchange = actualizarObjFormulario;
// inputTurnoN.onchange = actualizarObjFormulario;

// formulario.onsubmit = (e) => {
//   e.preventDefault();
//   console.log("Enviando datos al servidorsh");
//   console.log(objFormulario);
// };



// LOCAL_STORAGE
// CREAR UN FORMULARIO Y GUARDAR LOS DATOS EN EL LOCAL STORAGE Y TBM QUE CADA VEZ QUE YO AGREGE ALGO APARESCA ABAJO EN UNA TABLA TODO LO QUE VAYA AGREGANDO

// <!DOCTYPE html>
// <html lang="en">
//   <head>
//     <meta charset="UTF-8" />
//     <meta name="viewport" content="width=device-width, initial-scale=1.0" />
//     <title>Document</title>
//     <style>
//       body {
//         background-color: #eee;
//         min-height: 100vh;
//       }
//       form,
//       .contenedor {
//         background-color: #fff;
//         padding: 30px;
//         border-radius: 10px;
//         box-shadow: 0px 0px 20px #888;
//         width: 500px;
//         margin: 20px auto 0px auto;
//       }
//       form input {
//         width: 100%;
//       }
//       .contenedor > table {
//         width: 100%;
//       }

//       .menu {
//         list-style: none;
//         position: absolute;
//         border-radius: 12px;
//         overflow: hidden;
//         left: 0;
//         top: 0;
//         box-shadow: 0px 0px 12px #888;
//         padding: 0;
//       }
//       .menu__item {
//         background-color: #444;
//         color: white;
//         padding: 10px;
//         cursor: pointer;
//       }
//       .menu__item:hover {
//         background-color: #666;
//       }
//     </style>
//   </head>
//   <body>
//     <h2>Preferencias</h2>
//     <input type="color" id="inputColor" />

//     <form id="formulario">
//       <p>
//         <label for="">Código de Producto</label>
//         <input type="number" name="codigo" id="inputCodigo" />
//       </p>
//       <p>
//         <label for="">Nombre de Producto</label>
//         <input type="text" name="nombre" id="inputNombre" />
//       </p>
//       <button type="submit">Agregar Producto</button>
//     </form>
//     <hr />
//     <section class="contenedor">
//       <table border="1">
//         <thead>
//           <tr>
//             <th><strong>#</strong></th>
//             <th>Codigo</th>
//             <th>Nombre</th>
//           </tr>
//         </thead>
//         <tbody id="tbody"></tbody>
//       </table>
//     </section>

//     <ul class="menu" id="menu" hidden>
//       <li class="menu__item">
//         Crear Carpeta
//       </li>
//       <li class="menu__item">
//         Crear Archivo
//       </li>
//       <li class="menu__item">
//         Imprimir Página
//       </li>
//     </ul>

//     <script src="./02-localstorage.js"></script>
//   </body>
// </html>

// let formulario = document.getElementById("formulario");
// let inputCodigo = document.getElementById("inputCodigo");
// let inputNombre = document.getElementById("inputNombre");
// let tbody = document.getElementById("tbody");
// let inputColor = document.getElementById("inputColor");
// let menu = document.getElementById("menu");

// inputColor.onchange = () => {
//   let body = document.querySelector("body");
//   body.style.backgroundColor = inputColor.value;
//   localStorage.setItem("color", inputColor.value);
// };

// let productos = [];

// const llenarTabla = () => {
//   tbody.innerHTML = "";

//   // console.time("tabla");-=--=_+
//   productos.forEach((objProd, i) => {
//     let tr = document.createElement("tr");
//     let tdNro = document.createElement("td");
//     tdNro.innerText = i + 1;
//     let tdCodigo = document.createElement("td");
//     tdCodigo.innerText = objProd.codigo;
//     let tdNombre = document.createElement("td");
//     tdNombre.innerText = objProd.nombre;
//     tr.appendChild(tdNro);
//     tr.appendChild(tdCodigo);
//     tr.appendChild(tdNombre);
//     tbody.appendChild(tr);
//   });
//   // console.timeEnd("tabla");
// };

// formulario.onsubmit = (e) => {
//   // e.preventDefault();
//   let objProducto = {
//     codigo: inputCodigo.value,
//     nombre: inputNombre.value,
//   };
//   if (objProducto.codigo.length > 0 && objProducto.nombre.length > 0) {
//     productos.push(objProducto);
//   }


//   /**
//    * window.localStorage.setItem("identificador_del_item","valor")
//    * En la memoria localStorage del navegador(chrome), se crea
//    * una variable llamada "identificador_del_item" con el valor "valor"
//    * OJO: sólo se pueden guardar valores Strings
//    */
//   /**
//    * JSON es una clase estática (análoga a Math) que tiene una serie de
//    * funciones para trabajar con objetos JSON
//    * ejm:
//    * JSON.stringify(objeto|arreglo), retorna el parametro pasado
//    * como argumento en STRING
//    */
//   let productosString = JSON.stringify(productos);
//   window.localStorage.setItem("listaproductos", productosString);

//   llenarTabla();
// };

// /**
//  * Funcion que verifica si hay datos en el LOCALSTORAGE
//  * y llena la tabla con dichos datos inciales
//  */
// const verificarStorage = () => {
//   let productosStorage = window.localStorage.getItem("listaproductos");
//   let colorStorage = localStorage.getItem("color");
//   /**
//    * preguntamos si habían datos con esa clave(listaproductos) en el storage
//    */
//   if (productosStorage) {
//     let productosJSON = JSON.parse(productosStorage);
//     productos = productosJSON;
//     llenarTabla();
//   }
//   if (colorStorage) {
//     document.querySelector("body").style.backgroundColor = colorStorage;
//     inputColor.value = colorStorage;
//   }
// };
// verificarStorage();

// // window.onbeforeunload = (e) => {
// //   e.preventDefault();
// //   // borrar el localstorage antes de cerrar la página
// //   // window.localStorage.removeItem("listaproductos");
// //   return "asdasd";
// // };

// document.querySelector("body").oncontextmenu = (e) => {
//   e.preventDefault();
//   // aqui podrían dibujar un menu contextual propio de la aplicación
//   menu.style.left = `${e.clientX}px`;
//   menu.style.top = `${e.clientY}px`;
//   menu.removeAttribute("hidden");
// };

// document.querySelector("body").onclick = (e) => {
//   menu.setAttribute("hidden", "hidden");
// };


// // PRACTICAS BOOTSTRAP
// // LIBRERIAS PRACTICAR 

// //DESTRUCTURACION
// /**
//  * Destructurar arreglos
//  */

// let nombres = ["Anita", "Lucio", "María", "Omar", "Fernanda"];
// let [a, b, c, d, e] = nombres;
// console.log(e); //Fernanda
// console.log(b); //Lucio

// let [ani, , , , fer] = nombres;
// console.log(fer); //Fernanda
// console.log(ani); //Anita


// // operador rest => ...
// //hacer una copia de un arreglo y almacenarlo aparte
// // con el = estamos hacemo copia hasta de la direccion de memoria y datos mala practica
// let [...nombresTemporal] = nombres;
// console.log(nombresTemporal);

// let [ele1, ele2, ...resto] = nombres;
// console.log(ele1);
// console.log(ele2);
// console.log(resto);
// //console.log(...resto);

// let nombresCopia = ["Juan", ...nombres];
// console.log(nombresCopia);
// console.log(nombres);


// //le estoy pasando un array y solo quiero destructurar 2 valores de ese arreglo
// const dosPrimeros = ([a, b]) => {
//   console.log(a);
//   console.log(b);
// };

// dosPrimeros(nombres);

// //DESTRUCTURACION DE OBJETOVS
// // Destructuración de Objetos

// let restaurant = {
//   nombre: "El pollo real",
//   tipo: "Pollería",
//   aforo: 500,
//   geo: {
//     lat: -70,
//     lng: -16,
//   },
// };

// // Creando una variable "nombre" que es copia de restaurant.nombre
// // tambien podemos cambiar el nombre de aforo a capacidad

// let { nombre, aforo: capacidad } = restaurant;
// console.log(nombre);
// console.log(capacidad);

// let {
//   geo: { lat: latitud, lng: longitud },
// } = restaurant;
// // console.log(geo);//error
// console.log(latitud, longitud);

// const nombreYAforo = ({ nombre, aforo }) => {
//   console.log(nombre, aforo);
// };
// nombreYAforo(restaurant);

// // forma correcta de copiar un objeto por completo
// let copiaRest = { ...restaurant };
// console.log(copiaRest);

// const modificarAforo = (objRestaurant, nuevoAforo) => {
//   return {
//     ...objRestaurant,
//     aforo: nuevoAforo,
//   };
// };

// let restaurantGrande = modificarAforo(restaurant, 5000);
// console.log(restaurantGrande);




// /**
//  * Ejemplo de destructuracion al estilo REACT!
//  */
// // const useState = (estadoInicial) => {
// //   let inicial = estadoInicial;
// //   const modificarEstado = (nuevoEstado) => {
// //     inicial = nuevoEstado;
// //   };

// //   return [inicial, modificarEstado];
// // };

// // const [state, setState] = useState("Jorge");
// // setState("nuevo estado");

// //asincronia
// /**
//  * setTimeout
//  */
// let resultado = [];
// const traerDatos = () => {
//   console.log("Conectándose a la base de gatos");
//   console.log("Los datos llegaron del servidor =)");
//   resultado = [5000, 8500, 10000];
// };

// console.log("LOG 1");

// //funcion asincrona
// setTimeout(traerDatos, 2000);

// console.log("LOG 2");
// console.log(resultado);
// console.log("LOG 3");

// /**
//  * promesas
//  */

// /**
//  * async await
//  */

// /**
//  * fetch (ajax)
//  */


// // PROMESAS

// /**
//  * Las promesas nos ayudan a esperar el resultado
//  * de un proceso asincrono
//  */

// let miPromesa = new Promise((resolve, reject) => {
//   setTimeout(() => {
//     // ambas funcionan como un return
//     // resolve
//     // reject
//     // resolve(["02815740", "01845421", "01854216"]);
//     // reject("El usuario no se ha encontrado en la base de gatos");
//     resolve({
//       codigo: 200,
//       mensaje: "No se encontró el producto",
//       contenido: "Lentes Rayban",
//     });
//   }, 2000);
// });

// miPromesa
//   .then((rpta) => {
//     if (rpta.codigo === 200) {
//       console.log("=)");
//       console.log(rpta.contenido);
//     } else {
//       console.log("=(");
//       console.log(rpta.mensaje);
//     }
//   })
//   .catch((error) => {
//     console.log("Ups! =(");
//     console.log(error);
//   });


// //EJERCICIOS DE PROMESAS
// let paises = [
//   { id: 1, nombre: "Perú" },
//   { id: 2, nombre: "Bolivia" },
//   { id: 3, nombre: "Chile" },
//   { id: 4, nombre: "Argentina" },
// ];

// let departamentos = [
//   { id: 1, nombre: "Lima", paisId: 1 },
//   { id: 2, nombre: "Arequipa", paisId: 1 },
//   { id: 3, nombre: "Puno", paisId: 1 },
//   { id: 4, nombre: "La Paz", paisId: 2 },
//   { id: 5, nombre: "Cochabamba", paisId: 2 },
//   { id: 6, nombre: "Santa Cruz", paisId: 2 },
// ];

// const getPaisById = (id) => {
//   let buscando = new Promise((resolve, reject) => {
//     setTimeout(() => {
//       let pais = paises.find((objPais) => {
//         if (objPais.id === id) {
//           return objPais;
//         }
//       });
//       if (pais) {
//         resolve(pais);
//       } else {
//         reject("No se encontro el país buscado joven");
//       }
//     }, 2000);
//   });
//   return buscando;
// };

// const getDepartamentosByPaisId = (id) => {
//   const buscando = new Promise((resolve, reject) => {
//     setTimeout(() => {
//       const dptos = departamentos.filter((objDpto) => {
//         if (objDpto.paisId === id) {
//           return objDpto;
//         }
//       });
//       resolve(dptos);
//     }, 3000);
//   });
//   return buscando;
// };

// getPaisById(1)
//   .then((paisEncontrado) => {
//     console.log(paisEncontrado);
//     return getDepartamentosByPaisId(1);
//   })
//   .then((dptos) => {
//     console.log(dptos);
//   })
//   .catch((mensajeError) => {
//     console.log("=(");
//     console.log(mensajeError);
//   });

// // getDepartamentosByPaisId(2)
// //   .then((dptos) => {
// //     console.log("llegaron los departamentos");
// //     console.log(dptos);
// //   })
// //   .catch(() => {});



// //PROMESAS USANDO ASYNC - AWAIT

// let paises = [
//   { id: 1, nombre: "Perú" },
//   { id: 2, nombre: "Bolivia" },
//   { id: 3, nombre: "Chile" },
//   { id: 4, nombre: "Argentina" },
// ];

// let departamentos = [
//   { id: 1, nombre: "Lima", paisId: 1 },
//   { id: 2, nombre: "Arequipa", paisId: 1 },
//   { id: 3, nombre: "Puno", paisId: 1 },
//   { id: 4, nombre: "La Paz", paisId: 2 },
//   { id: 5, nombre: "Cochabamba", paisId: 2 },
//   { id: 6, nombre: "Santa Cruz", paisId: 2 },
// ];

// const getPaisById = (id) => {
//   let buscando = new Promise((resolve, reject) => {
//     setTimeout(() => {
//       let pais = paises.find((objPais) => {
//         if (objPais.id === id) {
//           return objPais;
//         }
//       });
//       if (pais) {
//         resolve(pais);
//       } else {
//         reject("No se encontro el país buscado joven");
//       }
//     }, 2000);
//   });
//   return buscando;
// };

// const getDepartamentosByPaisId = (id) => {
//   const buscando = new Promise((resolve, reject) => {
//     setTimeout(() => {
//       const dptos = departamentos.filter((objDpto) => {
//         if (objDpto.paisId === id) {
//           return objDpto;
//         }
//       });
//       resolve(dptos);
//     }, 3000);
//   });
//   return buscando;
// };

// /**
//  * funcion que retorna tanto el pais como la lista de departamentos
//  * dado el id de un pais
//  */
// const getAllByPaisId = async (id) => {
// 	let paisEncontrado = await getPaisById(id);
// 	let departamentosFiltrados = await getDepartamentosByPaisId(id);
//   return {
//     paisEncontrado: paisEncontrado,
//     departamentosFiltrados: departamentosFiltrados,
//   };
// };

// getAllByPaisId(1).then((rptaFinal) => {
//   console.log(rptaFinal);
// });








// const funcionAsincrona = async () => {
//   return 100;
// };

// funcionAsincrona().then((valor) => {
//   console.log(valor);
// });

// //EJEMPLO DE FETCH CONSUMIENDO APIS RECIEN
// <!DOCTYPE html>
// <html lang="en">
//   <head>
//     <meta charset="UTF-8" />
//     <meta name="viewport" content="width=device-width, initial-scale=1.0" />
//     <!-- <script src="./06-async-await.js"></script> -->
//     <link
//       rel="stylesheet"
//       href="https://stackpath.bootstrapcdn.com/bootstrap/4.5.1/css/bootstrap.min.css"
//       integrity="sha384-VCmXjywReHh4PwowAiWNagnWcLhlEJLA5buUprzK8rxFgeH0kww/aWY76TfkUoSX"
//       crossorigin="anonymous"
//     />
//     <link
//       rel="stylesheet"
//       href="https://cdnjs.cloudflare.com/ajax/libs/animate.css/4.0.0/animate.min.css"
//     />
//     <title>Document</title>
//   </head>
//   <body>
//     <nav class="navbar navbar-expand-sm navbar-dark bg-dark">
//       <a class="navbar-brand" href="#">Navbar</a>
//       <button
//         class="navbar-toggler d-lg-none"
//         type="button"
//         data-toggle="collapse"
//         data-target="#collapsibleNavId"
//         aria-controls="collapsibleNavId"
//         aria-expanded="false"
//         aria-label="Toggle navigation"
//       ></button>
//       <div class="collapse navbar-collapse" id="collapsibleNavId">
//         <ul class="navbar-nav mr-auto mt-2 mt-lg-0">
//           <li class="nav-item active">
//             <a class="nav-link" href="#"
//               >Home <span class="sr-only">(current)</span></a
//             >
//           </li>
//           <li class="nav-item">
//             <a class="nav-link" href="#">Link</a>
//           </li>
//           <li class="nav-item dropdown">
//             <a
//               class="nav-link dropdown-toggle"
//               href="#"
//               id="dropdownId"
//               data-toggle="dropdown"
//               aria-haspopup="true"
//               aria-expanded="false"
//               >Dropdown</a
//             >
//             <div class="dropdown-menu" aria-labelledby="dropdownId">
//               <a class="dropdown-item" href="#">Action 1</a>
//               <a class="dropdown-item" href="#">Action 2</a>
//             </div>
//           </li>
//         </ul>
//         <form class="form-inline my-2 my-lg-0">
//           <input
//             class="form-control mr-sm-2"
//             type="text"
//             placeholder="Search"
//           />
//           <button class="btn btn-outline-success my-2 my-sm-0" type="submit">
//             Search
//           </button>
//         </form>
//       </div>
//     </nav>

//     <main class="container">
//       <section class="row">
//         <div class="col">
//           <div id="alertaCargando" class="alert alert-info" role="alert">
//             <h4 class="alert-heading">Cargando...</h4>
//           </div>

//           <table class="table animate__animated animate__fadeIn" id="miTabla" hidden="hidden">
//             <thead>
//               <tr>
//                 <th>#</th>
//                 <th>Id</th>
//                 <th>Nombre</th>
//                 <th>Apellido</th>
//                 <th>Correo</th>
//                 <th>Foto</th>
//               </tr>
//             </thead>
//             <tbody id="tbody"></tbody>
//           </table>
//         </div>
//       </section>
//     </main>

//     <script src="./07-fetch.js"></script>
//   </body>
// </html>





const url = "https://reqres.in/api/users";
const tbody = document.getElementById("tbody");
const alertaCargando = document.getElementById("alertaCargando");
const miTabla = document.getElementById("miTabla");

// fetch(url).then((response) => {
//   response.json().then((final) => {
//     console.log(final);
//   });
// });

const getUsuarios = async () => {
  let response = await fetch(url);
  let myJson = await response.json();

  return myJson;
};

const dibujarTabla = (usuarios) => {
  usuarios.forEach((objUsu, i) => {
    let tr = document.createElement("tr");
    tr.innerHTML = `<td>${i}</td>
										<td>${objUsu.id}</td>
										<td>${objUsu.first_name}</td>
										<td>${objUsu.last_name}</td>
										<td>${objUsu.email}</td>
										<td><img src='${objUsu.avatar}' 
												class='rounded-circle' width='50'/></td>`;
    tbody.appendChild(tr);
  });
  // muestre la tabla y ocultar el cargando
  miTabla.removeAttribute("hidden");
  alertaCargando.setAttribute("hidden", "hidden");
};

getUsuarios().then((rpta) => {
  dibujarTabla(rpta.data);
});


// --- FINAL CON SEMANA 8 CON DIA2


























































// // let numero1=10;
// // let numero2=20;

// // console.log(numero1+numero2);

// // existen 2 formas de declarar string pero con la nueva especificacion de javasript ES2015 podemos crear template literales o template string la cual escapsulamos en comillas invertidad o backticks
// // Como podéis ver, gracias a los emplate literals obtenemos un código mucho más fácil de leer y legible, a desde 1 y retorna el array restantehorrándonos la concatenación de múltiples strings mediante el operador + .
// // -podemos concatenar o interpolar string de modo que nuestro codigo quede mas limpio a diferencia de:
// // console.log(nombre+ " "+edad);
// // console.log(`nombre ${nombre} apellido ${edad}`)
// // - otro beneficio de usar los backticks es que podemos usar los los enter osea string en varias lineas y poder tener un codigo mas limpio cosa que no podemos usarlo con los '' o ""
// // para el salto de linea tenermos que usar el contraslash
// //const html="<article>\
// //<h1>Hola mundito</h1>\
// //</article>";

// // let nombre="jhonatan";
// // let apellido='maquera';

// // console.log(`mis datos son: ${nombre} ${apellido}`);
// // console.log(nombre+ " "+apellido);
// // console.log(numero2 + numero1)
// // let isCasado=false;
// // let isDivorsiado=true;

// // console.log(isDivorsiado);

// console.log("************** Array y  *********************");
// // let numeros=[10,11,12,13,14]
// // console.log(`cantidad de numeros ${numeros.length}`);

// //acceder a un elemento atravez de su indice
// // console.log(numeros[0]);

// // para mostrar el ultimo elemento = cantidad de elementos -1
// // console.log(`el ultimo elemento ${numeros.length-1}`);
// //add un elemento al final del array
// // numeros.push(1200)

// // let nombres=['pamela','fiorella'];
// // console.log(nombres);

// //elimina el ultimo elemento del array
// //nombres.pop()

// //add pamela al inicio del arreglo
// nombres.unshift("pamela");

// //elimina el 1er elemento del arreglo
// nombres.shift();

// //encontrar el indice de un elemento por su nombre -1 si no se encuentra si hay mas coincidencias va mostrar el 1ro que encuentre
// nombres.indexOf("pamela");

// //.splice elimina o separa el arreglo original en partes indicadas y luego el arreglo inicial tendra el restante de lo dividido
// //.splice crea un nuevo arreglo con los parametros dados .splice(posicion_inicial,posicion_final) y guardamos en una nueva variable
// // console.log(numero.splice(1,5)) crea un arreglo con los datos desde la posicion 1 con  5 elementos hacia delante
// nombres.splice(1, 1);

// // metodo que se encaga de realizar una copia de los valores iniciales y si e padre es modificado o cambiado de valores despues de realizar la copia este copiaArray no se ve afectada
// let copiaArray = nombre.sclice();

// // para unir 2 array en 1 solo
// // const array1 = ['a', 'b', 'c'];
// // const array2 = ['d', 'e', 'f'];
// // const array3 = array1.concat(array2);
// console.log(array3);
// // Expected output: Array ["a", "b", "c", "d", "e", "f"]

// console.log("++++++++++++FUNCIONES++++++++++++++");
// //funcion que no retorna nada ni recibe ningun argumento
// // function imprimirFecha(){
// //     let fecha=new Date();
// //     console.log(fecha)
// // }
// //invocando ala funcion imprimir
// // imprimirFecha();

// //function que retorna un valor
// // function retorna_fecha(){
// //     let fecha=new Date();
// //     return fecha;
// // }

// // console.log(retorna_fecha());

// //funcion que recibe parametros y retorna su valor
// //para documenta las funciones
// //basta con colocar /** */ sobre la funcion y automaticamente lo solucionara los parametros y retornos
// /**
//  * funcion que recibe 2 numeros y calcula la suma
// //  * @param {tipo de datos} name_dato - descripcion
//  * @param {number} a 1er numero
//  * @param {number} b 2do numero
//  * @return {number} el resultado de la suma
//  */
// // function suma(a,b){
// //     return a+b;
// // };

// // let rpta=suma(10,0)
// // console.log(rpta);

// // ojo undefined= la variable esta creada pero no tienes un valor adentro
// //null=retorna un valor nulo en alguna busqueda
// // typeof data == para saber que tipo de dato es la variable data

// //funciones con parametros opcionales
// // function suma(a=10,b=30){
// //     console.log(a+b);
// // }

// // suma();

// console.log("---------- funciones anonimas --------------");
// // funciones anonimas fechas son funciones que no tienen nombre
// // cuyo valor se guarda en una variable
// // es nuevo standar usar las funciones anominas y no las otras ahora asi debemos crearlas por referencia
// // lo mejor seria crearlo con const para que asi no se modifique su valor
// // const sumando=function(){
// //     return a+b;
// // };
// // let respuesta=sumando(7,8);
// // console.log(respuesta);

// // con el nuevo standar las funciones arrow function(funciones de flecha) k son funciones anonimas pero otra manera de escribir
// //  ya no hay la palabra reservada function
// // const sumarFecha=(a,b)=>{
// // }
// console.log("+++++++++ CALLBACK +++++++++++++++++");
// // cuando usamos los callback como parametro le pasamos como referencia no como ejecucion de la funcion que seri con el ()
// // const buscarPorDni=(x)=>{
// //     // zona de ejecucion de mostrarResultado
// //     x();
// // }

// // const mostrarResultado=()=>{
// //     console.log('mostrando el resultado')
// // }
// // cuando usamos los callback como parametro le pasamos como referencia y cuando en otro funcion reciba ese callback entonces recien podemos usarlo como () para ejecutar esa function
// // un callback es ejecutar un function dentro de otra funcion pasada como referencia
// // buscarPorDni(mostrarResultado)
// // aplicando otra manera es lo mismo solamente que no esta dentro de una variable si no asi nomas
// // buscarPorDni(()=>{
// //     console.log('mostrando el resultado');
// // })

// // tambien podemos hacerlo como funcion anonima osea no tiene nombre

// // const buscarPorDni =(x,y)=>{

// // }
// //recibe 2 parametros este metodo x y y y cuando lo declaramos alli debemos colocarlo
// // buscarPorDni(function(){
// //     console.log('mostrando el resultadito')
// // },175)

// // la funcion se activa en 2 segundo
// // setTimeout(() => {

// // }, timeout);
// // setTimeout(function(){

// // },10)

// console.log("+++++ function flecha o anonima simplificada ++++++");

// // si la funcion solo tiene una 1 de codigo de ejecucion  entonces puedes omitir la llaves
// // const sumar=(a,b)=> console.log('sumando...');

// //si la function recibe 1 parametro podemos omitir las cosas(){}
// // const cuadrado = a => console.log(a*a);

// //si la function retorna solo una linea de ejecucion podemos obviar el return  por los parentesis
// // const cubo=n =>(n*n*n);

// console.log("++++++++++++ OBJETOS ++++++++++++");
// //los arreglos se basan en sus posiciones y los objetos en sus nombre
// // no se usa mucho el poo en js xk podemos crear objetos sin la necesidad de crear clases entonces x eso no se usa mucho
// // por que bien sabes nostros que debemos crear una clases e instanciar para crear su objeto asi es normalmente

// // como crear un objeto
// let objPersona = {
//   nombre: "jhonatan",
//   apellido: "maquera",
//   edad: 10,
//   peso: 20.1,
//   casado: true,
// };

// // forma de acceder a los objetos con el . podemos haceder a cualquier atributo del objeto
// console.log(objPersona.nombre);
// console.log(objPersona.apellido);
// console.log(objPersona.edad);
// console.log(objPersona.casado);

// console.log(
//   `mi nombre es ${objPersona.nombre} mi apelido ${objPersona.apellido} mi edad es ${objPersona.edad}`
// );

// // forma de 2 de acceder a los objetos con un string en los corchetes
// // esta forma es la mejor para poder acceder a los formularios
// console.log(objPersona.nombre["nombre"]);

// // como modificar los valores del objetito

// objPersona["nombre"] = "jhonael";
// objPersona["apellido"] = "ramos";

// console.log(objPersona);
// // add un nuevo atributo
// objPersona["comida"] = "picante";
// objPersona.postresFavoritos = ["mazamorrita", "el flan", "keke"];

// //ojo para la identacion usamos alf+shit+F y super vacan

// let productos = [
//   { nombre: "TV Samsung 50", precio: 100 },
//   { nombre: "TV Samsung 40", precio: 50 },
//   { nombre: "TV Samsung 30", precio: 25 },
// ];

// //recorrer un array
// for (let i = 0; i < productos.length; i++) {
//   console.log(`Producto ${i}`);
//   console.log(`nombre ${productos[i].nombre}`);
//   console.log(`precio ${productos[i].precio}`);
// }
