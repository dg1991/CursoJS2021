**Curso JavaScript a Fondo 2021: https://www.youtube.com/playlist?list=PLM-Y_YQmMEqB4FVmgxZqG-f7R3ESkcIPA**

## Declaraciones de variables

### La etiqueta `<script>`

Esto es una entrada

- Puerta de entrada al código JS en nuestros proyectos.
- Vive en el <head> de nuestros documentos HTML.
- A través de `<script>` podemos cargar JS externo.
- Para ello, utilizamos el atributo src y una URL al recurso, ya sea relativo o absoluto. `<script src="..."></script>`
- **IMPORTANTE: https://cdnjs.com/**
- Muchas veces encontraremos `<script>` en `<footer>` en lugar de `<header>`, para asegurarnos de que el DOM está listo antes de acceder a él.
- Hoy en día no es necesario usar este patrón, ya que tenemos el atributo _defer_ a nuestro alcance. `<script defer src="..."></script>`
- Con la etiqueta `<noscript>` podemos mostrar un mensaje al usuario cuyo navegador tenga JS desactivado. `<noscript>JavaScript desactivado</noscript>`

## Alzado (hoisting)

- JS es un lenguaje con tipos dinámicos, es decir, podemos asignar y reasignar diferentes tipos a una misma varible (de ahí el nombre: variable).
- Para hacerlo tenemos que utilizar dos fases diferentes: declaración e inicialización.

```
var favorito // Declaración 
favorito = 66 // Inicialización
favorito = "Juan" // Reasignación
```

- Cuando creamos declaramos una variable, JS le asigna el tipo _undefined_.
- Si intentamos referenciar una variable antes de ser declarada, ¿qué crees que ocurrirá?.

```
console.log(nombre)
var nombre = "Juan"
```

- La respuesta es _undefined_ **porque JS, al interpretar tu código alza al inicio del programa la declaración de variables** (no la inicialización) y las funciones declaradas.
- Esto explica el por qué, por ej., puedes _invocar_ una función antes de declararla.

```
saludar()
function saludar() {
    console.log("Hola")
}
```

## Ámbito y let

- Hasta ahora hemos creado variables con var. Estas tienen **ámbito de función:** pueden ser accedidas desde la función donde fueron declaradas (y funciones interiores).

```
var nombre = "Juan";
function Saludar() {
    var nombre = "Andres";
    console.log("Hola " + nombre);
}
Saludar();
```

- Sin embargo, si declaramos variables con let(ES2105), tenemos **ámbito de bloque**, es decir, solo pueden ser accedidas desde el bloque en el que se declararon, o bloques interiores. 

```
{
let name = "Juan";
}

console.log(name);
```

- Este ámbito de bloque tiene sus ventajas. Por ej. al utilizarlo con estructuras de control y de flujo.

```
for (let i = 0; i <= 100; i++) {
    console.log(i);
}
console.log(i);
```

- Además, al usar _let_ tenemos un comportamiento mucho más estricto en el _alzado_ (hoisting), algo que para muchos es otra ventaja.

```
console.log(isname)
let isname = "Juan"
```

## Constantes
- Como ahora ya sabes, _var y let_ permiten declarar variables dinámicas: puedes re-asociarlas a otro valor.
- Si queremos crear una asociación constante a un valor, podemos usar _const_ para la creación de variables.

```
const edad = 30;
```

- Al utilizar _const_ nos aseguramos que no ocurrirá ninguna re-asociación a otro valor eb esa variable.
- Eso sí, usar _constantes_ no significa que sean inmutables. Podemos mutar propiedades del valor asociado a la constante.

```
const persona = { nombre: "Juan" }
persona.nombre = "Andres"
console.log(persona.nombre);
```

- En cuanto a su acceso, igual que con _let_ disponemos de ámbito de bloque

```
{
const name = "Juan";
}

console.log(name);
```

- Por último, las variables creadas con _const_ no son alzadas.

```
console.log(persona.nombre);
const persona = { nombre: "Juan" }
persona.nombre = "Andres"
```

## Parámetros y argumentos 

- Todas las funciones pueden tener parámetros para hacerlas aún más polivalentes.
- Los parámetros son accesibles como variables en el cuerpo de la función.
- Al invocar la función, pasamos valores como argumento que son aceptados como parámetros.

```
function saludar (nombre) {
    console.log("Hola me llamo " + nombre);
}

saludar('Juan');
```

- Podemos establecer valores por defecto para los parámetros, en el caso de que no se satisfagan en la invocación.

```
function saludar (nombre = "Juan", apellido = "Núñez") {
    console.log("Soy " + nombre + " " + apellido);
}

saludar();
```

```
function saludar (nombre = "Juan", apellido = "Núñez") {
    console.log("Soy " + nombre + " " + apellido);
}

saludar(undefined, "Charro");
```

## NO VISTO -> Callbacks 

Es una función que se pasa a otra función como argumento para su ejecución posterior.

```
function miFuncion(fn) {
    // Callback
    fn()
}
```

Existen callbacks síncronicos y asíncronicos



