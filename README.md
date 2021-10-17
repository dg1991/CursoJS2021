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
- Sin embargo, si declaramos variables con let(ES2105), tenemos **ámbito de bloque**, es decir, solo pueden ser accedidas desde el bloque en el que se declararon, o bloques interiores. 

**IMPORTANTE: Seguir acá: https://www.youtube.com/watch?v=iIkeGM1I-cM&list=PLM-Y_YQmMEqB4FVmgxZqG-f7R3ESkcIPA&index=3**

## NO VISTO -> Callbacks 

Es una función que se pasa a otra función como argumento para su ejecución posterior.

```
function miFuncion(fn) {
    // Callback
    fn()
}
```

Existen callbacks síncronicos y asíncronicos



