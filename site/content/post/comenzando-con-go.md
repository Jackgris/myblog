---
date: 2013-07-11T23:19:26-03:00
draft: true
title: Comenzando con Go
---

Hola a todos, en este post les vengo a hablar de un lenguaje nuevo, con el que hace un tiempo estoy haciendo algunas cosas, y mientras estoy agarrando experiencia con el mismo, cada vez me gusta mas.

![Logo de Go](http://myblog-965.appspot.com/2013/07/golang-post1.jpg?raw=true)

### Datos generales:

Go es un lenguaje de programación concurrente y compilado inspirado en la sintaxis de C.

Go es un nuevo lenguaje de programación para sistemas lanzado por Google en Noviembre del 2009. Aunque empezó a ser desarrollado en Septiembre del 2007 por Robert Griesemer, Rob Pike y Ken Thompson.

### Características:

Go es un lenguaje de programación compilado, concurrente, imperativo, estructurado, no orientado a objetos —de una manera bastante especial— y con recolector de basura que de momento está soportado en diferentes tipos de sistemas UNIX, incluidos Linux, FreeBSD y Mac OS X. También está disponible en Plan 9 puesto que parte del compilador está basado en un trabajo previo sobre el sistema operativo Inferno. Las arquitecturas soportadas son i386, amd64 y ARM

- Go usa una sintaxis parecida a C por lo que los programadores que hayan usado dicho lenguaje se sienten muy cómodos con él.
- Go usa tipado estático (estatically typed) y es tan eficiente como C.
- Go tiene muchas de las características y facilidad de lenguajes dinámicos como Python
- Aún siendo un lenguaje diseñado para la programación de sistemas, provee de un recolector de basura, reflexión y otras capacidades de alto nivel que lo convierten en un lenguaje muy potente.
- Go no está orientado a objetos porque no existe jerarquía de tipos pero implementa interfaces.


Esta última característica, me parece realmente interesante, además de que la sintaxis muy parecida a la de Python realmente me atrae. A que voy con eso Go admite la tipificación dinámica de datos también conocida como duck Typing presente en multitud de lenguajes dinámicos como por ejemplo JavaScript, Ruby o Python. Un struct puede implementar una interfaz de forma automática, lo cual es una característica potente y novedosa.
Una de las cosas que lo hacen un excelente lenguaje concurrente es que tiene algo que no son ni threads, ni co-rutinas ni procesos. La comunicación entre goroutines se realiza a través de una característica del lenguaje llamada canales —basada en CSP—, que es más segura y fácil de usar que los sistemas predominantes basados en bloqueos de pthreads o características modernas de Java

Esto si que es llamativo, el tema de las excepciones:
Go no tiene excepciones. Los creadores del lenguaje dan varios motivos para que esto sea así. Uno de ellos es que añadir una capa de excepciones añade una complejidad innecesaria al lenguaje y al entorno de ejecución. Por definición deberían de ser excepcionales pero al final se acaban usando como controladores del flujo de la aplicación y dejan de tener nada de excepcional. Según los creadores, las excepciones tienen que ser realmente excepcionales y el uso que se le da mayoritariamente no justifica su existencia.

### ¿Es Go un lenguaje orientado a objetos?

Bueno, esta no es una pregunta fácil de responder. Digamos que si y no. Go tiene tipos y métodos y permite un estilo de programación orientado a objetos pero no existe una jerarquía de objetos, por lo tanto, no existe la herencia. En Go, el concepto de “interfaz“ diferente que los creadores creen es fácil de usar y en muchos sentidos es más general. También existen formas de embeber tipos dentro de otros tipos para obtener algo análogo a las subclases. Los métodos de Go son más generales que los de C++ o Java, pueden ser definidos para cualquier tipo de datos no solo para los structs.
La ausencia de jerarquía de tipos en Go, hace que los “objetos“ den una sensación de ser más ligeros que en lenguajes como C++ o Java.

### Instalación de nuestro entorno de desarrollo:

En un sistema operativo Linux nos descargamos el archivo comprimido correspondiente a nuestro sistema operativo y arquitectura de acá:
https://golang.org/dl/


Luego de eso simplemente descomprimimos el archivo en esta ubicación:
```
tar -C /usr/local -xzf go1.1.linux-amd64.tar.gz
```

Para ello vamos a necesitar permisos de root, y al terminar de descomprimirlo, para poder utilizarlo de manera cómoda, vamos a agregarlo a nuestro path, escribiendo en el archivo .bashrc de nuestro home, o en /etc/profile  la siguiente línea:
```
export PATH=$PATH:/usr/local/go/bin
```

### Ver documentación oficial:
http://golang.org/doc/install


### Hola Mundo :D

Para probar que la instalación salió correctamente vamos a crear un archivo con extensión .go por ejemplo hola.go, y dentro del mismo escribimos el siguiente código:

```go
package main

import "fmt"

func main(){
    fmt.Printf("Comenzando con GO!\n")
}
```

Luego desde la consola, tipeamos (si tenemos todo correctamente instalado, y configurado nuestro PATH, y situados en donde se encuentra el archivo que creamos recién ):
```
go run hola.go
```

Y nuestra salida en la consola deberá ser la siguiente:
```
Comenzando con GO!
```
Si es así, tenemos todo correctamente para comenzar con este interesante lenguaje ;)

### Recomendación:

Para trabajar con este lenguaje es muy recomendable configurar la variable de entorno llamada $GOPATH ;) esto nos va a servir para poder utilizar algunas herramientas como go get, para poder descargar librerías y que las instale y compile automáticamente ;)
Para eso deberemos crear una carpeta donde Go va a poder descargar el código fuente y creara los binarios, para seo podemos crear una carpeta de esta forma:

```
mkdir $HOME/go
```

Y para que nos resulte mucho más comodo agregar esto como lo hicimos antes a nuestro archivo .bashrc o bash_profile
```
export GOPATH=$HOME/go
```

Y también es muy util agregar la carpeta bin dentro de nuesto $GOPATH a nuestro $PATH
```
$ export PATH=$PATH:$GOPATH/bin
```

Para poder utilizar las herramientas en nuestra terminal de forma mucho mas cómoda.

Web Oficial
http://golang.org/

Ver por lo de la licencia
http://golang.org/project/

Bueno, eso es todo por ahora, espero que les allá gustado el post, creo que el aprender de este lenguaje puede ser muy interesante, sobre todo porque es apoyado totalmente por google, donde se esta migrando mucho de su código en C++ hacia este lenguaje, y ademas hay muchas empresas mas, como por ejemplo Modzilla https://github.com/mozilla-services/heka
Espero que les allá gustado el post, por supuesto que vamos a interiorizarnos más sobre el tema, además en algún momento, combinarlo con algún proyecto Android.

