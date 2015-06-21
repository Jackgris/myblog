---
date: 2013-07-16T12:37:48-03:00
draft: true
title: Lenguaje Go funciones y bucles
---

Hola a todos, nuevamente otro post de este lenguaje llamado Go!, en este caso vamos a ver un tema fundamental en la programación,
que es el tema de las funciones, como utilizar y declararlas.

![Logo de Go](http://myblog-965.appspot.com/2013/07/squishable.jpg?raw=true)

### Primero y antes que nada, que es una función?

En programación, una función es un grupo de instrucciones con un objetivo en particular y que se ejecuta al ser llamada desde otra función o procedimiento.
Una función puede llamarse múltiples veces e incluso llamarse a sí misma (función recurrente).
Las funciones pueden recibir datos desde afuera al ser llamadas a través de los parámetros y deben entregar un resultado.
Se diferencian de los procedimientos porque estos no devuelven un resultado.
En general las funciones deben tener un nombre único en el ámbito para poder ser llamadas, un tipo de dato de resultado,
una lista de parámetros de entrada y su código.
En muy pocas palabras, un pequeño trozo de código que va a realizar algo, donde uno puede enviarles algunos datos y recibir un resultado de el.

#### El siguiente es un ejemplo de cómo podríamos plasmarlo en nuestro código fuente:

```
func printf(str string, args ...interface{}) (int , error) {
    _, err := fmt.Printf(str, args...)
    return len(args), err
}

func main() {
    count := 1
    closure := func(msg string) {
        printf("%d %s\n", count, msg)
        count++
    }
    closure("Un Mensaje")
    closure("Otro Mensaje")
}
```

Y ahora un poco de la teoría para ver como es la cosa :D
Las funciones se declaran con la palabra reservada `func`, lo que nos devuelve la misma va al final, en este caso para la función `printf`,
nos va a devolver `(int, error)`, lo que nos muestra, que no necesariamente nos puede devolver una cosa, si no que puede ser una lista de cosas,
en este caso un entero y un objeto `error`. También podemos notar que al llamar a la función, podemos ignorar lo que nos devuelve o asignarlo a
diferentes variables, teniendo la opción de usar el guión bajo `_` para descartar algún valor que no deseemos utilizar, como se ve en la llamada
a `fmt.Printf()`.
Si nosotros queremos declarar una función que utilice una cantidad de argumento  variable podemos usar una interfaz vacía `...interface{}`
donde le vamos a poder pasar los argumentos que queramos.
Como dijimos anteriormente, la función `main()` va a ser el punto de entrada de nuestro programa, que a diferencia de otros lenguajes, este no toma argumentos.

Tenemos que tener en cuenta algo, que viene del anterior, post, cuando uno declara una variable, fuera de cualquier función,
esta va a tener un alcance en todo el código del archivo que escribimos, pero si nosotros declaramos variables dentro de una función,
la misma no se va a poder acceder desde afuera y no vamos a poder usar el valor de la misma. Para eso simplemente debemos utilizar el retorno de la función ;)
Un ejemplo de esto, es la variable `count` la cual es únicamente visible dentro de la función `main` pero no puede ser accedida desde la función `printf`.

#### Bucles en Go!

Código de ejemplo:

```
package main

import "fmt"

func main() {
    loops := 1
    // bucle while:
    for loops > 0 {
        fmt.Printf("\n Numero de vueltas?\n")
        fmt.Scanf("%d", &loops)
        // bucle for
        for i := 0 ; i < loops ; i++ {
            fmt.Printf("%d ", i)
        }
    }
    // bucle infinito
    for {
        // Finalizamos el bucle de manera explícita
        break
    }
}
```

Normalmente en los lenguajes de programación derivados de `C` tenemos tres diferentes tipo de bucles, y cada uno con una sintaxis diferente,
en cambio en `Go` para los tres tipo de bucle usamos la misma palabra reservada `for`, como se puede ver en el código, el tercero es el más sencillo,
un bucle infinito. Esto quiere decir que el código ahí dentro se repetirá y no va a parar de repetirse hasta que llegue a una sentencia `break`,
esto puede ser muy útil, supongamos que simplemente queremos que algo se repita hasta que suceda algo en particular, en ese caso,
simplemente arrancamos el bucle, y colocamos el break cuando se cumpla esa serie de condiciones que nosotros queremos para finalizar el bucle ;)
Dentro de un bucle ademas de desear terminarlo puede suceder, que queramos, que al suceder cierta condición, es que queremos que vuelva a arrancar el mismo,
y no que siga hasta terminarlo, para eso tenemos la sentencia `continue`
Los otros dos bucles que podemos armar con for serían los típicos while y el for común como los que podemos encontrar en `Java`.
Por ejemplo en el código de mas arriba, el primer for sería los mismo que el típico `while`, y el segundo lo mismo que el for en `Java`.
El primero se repetiría mientras que se cumpla la condición `loops > 0`, y el segundo hasta que se cumpla la condición `i < loops`

Web Oficial
http://golang.org

Ver por lo de la licencia
http://golang.org/project

Bueno eso es todo por ahora, seguiremos con esta serie de post mas adelante, mi intención con esto se resume a dos cosas,
que aprendamos juntos un lenguaje muy interesante, y además, dejar plasmada casi una introducción a la programación con un lenguaje nuevo,
con conceptos bastante interesantes. Y que pare ser un lenguaje compilado, tiene la ventaja de ser muy sencillo y tener muchas características
en la sintaxis que me recuerda a `Python`, cosa que me gusta mucho :D Espero que les guste, nos vemos en la próxima.
