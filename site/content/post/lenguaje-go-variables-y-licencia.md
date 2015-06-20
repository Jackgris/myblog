---
date: 2013-07-20T09:36:49-03:00
draft: true
title: Lenguaje Go, variables y licencia
---

Hola a todos nuevamente, como dije anteriormente, este nuevo lenguaje, me está gustando cada vez más, así que voy a continuar con otro post sobre el.

![Logo de Go](http://myblog-965.appspot.com/2013/07/appenginegophercolor.jpg?raw=true)

### La licencia
Un tema muy importante, y de la cual creo que vamos a poder aprender mucho sobre como programar en general,
es que los que contribuyeron código al mismo, además de haber muchos ingenieros de Google, entre ellos están personas como Robert Griesemer,
Rob Pike y Ken Thompson. Y al estar licenciado bajo la licencia BSD, nos podemos bajar todo el código de acá:

https://code.google.com/p/go/source/checkout

Donde vamos a poder revisarlo, ver los commit que cada uno aportó, y de esta manera, ver los estilos de cada uno.
Lo cual creo que es una excelente fuente de apredizaje.
Desde este enlace, vamos a poder ver los cambios que fue recibiendo cada release:

http://golang.org/doc/devel/release.html

También con el siguiente enlace vas a poder unirte a la lista de desarrolladores del mismo, a comunidades y demás:

http://golang.org/project/


Ahora si, vamos a ver un poco de código ;)

### Un poco de la estructura


Bueno vamos a arrancar bien por lo básico, como en el anterior post, vamos a crear un archivo que se llame, `hola.go` para ver como funciona la cosa :D
en el mismo vamos a incluir el siguiente código.

```
package main

import "fmt"

func main() {
    fmt.Printf("Hola lenguaje Go!\n")
}
```

Un archivo de código fuente consiste básicamente en tres partes, la primera como podrán ver es la sentencia `package`,
el código en Go! esta dispuesto en `packages` que cumplen ambos roles, el de librerías y el de `headers` en `C`
El paquete en este ejemplo se llama `main`, el cual al igual que en `C` es un nombre especial, ya que todo programa escrito
en este lenguaje debe contener un package main y un método `main()`, el cual va a ser el punto de entrada de nuestro programa.
La siguiente sección `import` es la que se encarga de especificar qué paquetes va a usar nuestro programa, y como vamos a importarlos,
en este caso vamos a importar `fmt`, una vez que lo hayamos realizado, vamos a poder utilizar cualquiera de los tipos, variables, constantes y funciones,
anteponiendo el nombre del paquete, en este caso vamos a usar el método `Printf()` del paquete `fmt`.
El cual nos va a dar la salida en la terminal con la string que le pasamos.

A pesar de que `Go` utiliza compilación estática, es importante tener en cuenta que las declaraciones de importación son mucho más cercanas a las
de `Java` o `Python` que las directivas de inclusiones en `C`. Ellas no lo hacen incluir el código fuente en la unidad de compilación actual.
Pero a diferencia de los paquetes de `Java` y `Python`, en `Go` los paquetes se importan cuando el código es vinculado, y no cuando se ejecuta.
Esto nos asegura que nuestra aplicación no fallará debido a la falta paquete en el sistema.
El tema de los paquetes son más importantes en `Go` que en lenguajes como `Java`, porque `Go` solo provee control de acceso a paquetes y no a clases.


Al importar un paquete también podríamos realizar cosas como estas:
`import format "fmt"`
Donde renombramos el paquete y lo podríamos llamar format en nuestro código, aunque normalmente es muy mala idea usarla,
ya que hacemos más difícil la lectura a otra persona de nuestro código y solo deberemos usarlo si necesitamos separar dos paquetes con el mismo nombre.
Con este tipo de `import` terminarían llamando al mismo método de la siguiente manera: `format.Printf("")` y no `fmt.Printf("")`

### Vamos a declarar variables

```
var i int
var Θ  float32
var explicitly, typed, pointers *complex128

intPointer := &i
anotherInt pointer := new(int)
genericChannel := make(chan interface{})
```

Las variables vamos a declararlas con la palabra reservada `var` seguido del nombre y despues del tipo por ej: int, float32, etc.
Como pueden ver también una de las variables fue declarada con el nombre Θ, esto es posible porque `Go` permite como identificador cualquier
símbolo que tiene la codificación `Unicode`, de todas maneras no es bueno abusar de ello, porque pueden haber símbolos complicados de encontrar
en el teclado y  uno de los únicos motivos para usarlos debería ser para simbología en matemática o similar.
Otra cosa, como pueden ver en los ejemplos, tenemos dos formas de declarar una variable, de la que hablamos recién es la forma larga,
la cual en realidad no vamos a tener que usar tan comúnmente, una de las claves de escribir buen código es el `principio del alcance mínimo`,
esto quiere decir que deberíamos buscar el alcance mínimo de nuestras variables.
Con las declaraciones largas, tendríamos variables por fuera de los metodos, básicamente el alcance de las mismas sería el de nuestro archivo,
en cambio para un alcance corto dentro de nuestro métodos tenemos el operador `:=` como se ve en un ejemplo: `intPointer := &i`
(en este ejemplo también se puede ver el uso de punteros con el operador `&`, el cual nos recordará seguramente a `C`,
aunque el valor de retorno funciona de manera similar al pasaje por referencia de `Java`)
Todavía hay más elementos sobre la inicialización de variables, pero los vamos a ir viendo en próximos post ;)

### Web Oficial
 
http://golang.org/

### Licencia
 
http://golang.org/project/

Bueno eso es todo por este post, de a poco seguiremos viendo como es la sintaxis en este lenguaje, para poder programar de manera correcta con el.
