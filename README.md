# Programación - 04 Programación Orientada a Objetos

Tema 04 Programación Orientada a Objetos. 1DAM. Curso 2022/2023.

![imagen](https://raw.githubusercontent.com/joseluisgs/Programacion-00-2022-2023/master/images/programacion.png)


- [Programación - 04 Programación Orientada a Objetos](#programación---04-programación-orientada-a-objetos)
  - [Contenidos](#contenidos)
  - [Programación Orientada a Objetos](#programación-orientada-a-objetos)
  - [Objetos](#objetos)
  - [Clases](#clases)
  - [Instanciación de Objetos](#instanciación-de-objetos)
  - [Propiedades y métodos](#propiedades-y-métodos)
  - [Constructores](#constructores)
  - [Referencia this](#referencia-this)
  - [Getters y Setters](#getters-y-setters)
  - [Igualdad e identidad](#igualdad-e-identidad)
  - [POJOS y POKOS. Data classes](#pojos-y-pokos-data-classes)
  - [Atributos y métodos de clase](#atributos-y-métodos-de-clase)
  - [Composición de objetos](#composición-de-objetos)
  - [Enums class](#enums-class)
  - [Recursos](#recursos)
  - [Autor](#autor)
    - [Contacto](#contacto)
    - [¿Un café?](#un-café)
  - [Licencia de uso](#licencia-de-uso)

## Contenidos
1. Programación Orientada a Objetos
2. Objetos
3. Clases
4. Instanciación de objetos
5. Propiedades y métodos
6. Constructores
7. Referencia this
8. Getters y Setters
9. Igualdad e identidad
10. POJOS y POKOS. Data classes
11. Atributos y métodos de clase
12. Composición de objetos
13. Enums Class

## Programación Orientada a Objetos
La programación orientada a objetos es un paradigma de programación que se basa en el concepto de objetos, los cuales contienen información en forma de campos (a veces también referidos como atributos o propiedades) y código en forma de métodos.

Los objetos son capaces de interactuar y modificar los valores contenidos en sus campos o atributos (estado) a través de sus métodos (comportamiento) y siempre tienen una identidad.

Algunas características clave de la programación orientada a objetos son herencia, cohesión, abstracción, polimorfismo, acoplamiento y encapsulamiento.

## Objetos
Un objeto es una entidad que tiene un estado y un comportamiento. El estado de un objeto es almacenado en campos (atributos) y el comportamiento es mostrado por métodos (funciones) y tienen una identidad. En lenguajes tipados, un objeto es una instancia de una clase (nos sirve para tipar). 

- Objetos: unidad que engloba dentro de sí un conjunto de datos y módulos necesarios para el tratamiento de esos datos. Cada objeto contiene datos y funciones.
- Atributos: Son los datos incluidos en el objeto. Parecidas a las variables de C clásico pero incluidas en los objetos.
- Métodos: Son módulos que pertenecen a los objetos y que manejarán los atributos.
- Identidad: Cada objeto tiene una identidad única que lo distingue de los demás objetos. La identidad de un objeto no puede ser cambiada durante la ejecución del programa.
- Mensajes: El modo mediante el que se comunican los objetos. Consiste en llamar a un método de un objeto.
- Interfaz: Las clases (y, por lo tanto, los objetos) tienen partes públicas y partes privadas. La parte pública es visible para todos los objetos, mientras que la parte privada es sólo visible para el propio objeto. A la parte pública de un objeto se le denomina interfaz.

```kotlin
// Llamando a un objeto
val persona = Persona()
persona.nombre = "José Luis"
persona.apellidos = "González Sánchez"
persona.programar(lenguaje= "Kotlin")
```

## Clases
Una clase es un modelo o plantilla para crear objetos. Una clase define los campos y los métodos de un objeto. Un objeto es una instancia de una clase. La clase nos va a servir para tipar los objetos.

```kotlin
// Definiendo una clase
class Persona {
    // Estado del objeto
    var nombre: String = ""
    var apellidos: String = ""

    // Comportamiento del objeto
    fun programar(lenguaje: String) {
        println("Programando en $lenguaje")
    }
}
```

## Instanciación de Objetos
La instanciación de objetos es el proceso de crear un objeto a partir de una clase. La instanciación de objetos se realiza mediante la palabra reservada new (Java), o llamando a su constructor (Kotlin).

A los miembros de un objeto se accede a través de su referencia. La sintaxis es:
nombre_referencia.miembro

```kotlin
// Instanciando un objeto
val persona = Persona()
persona.nombre = "José Luis"
persona.programar(lenguaje= "Kotlin")
```

## Propiedades y métodos
Los atributos definen el estado de un objeto. Las propiedades se definen en la clase y representan los atributos del estado y se acceden a través de la referencia del objeto.

Los métodos definen el comportamiento de un objeto. Los métodos se definen en la clase y representan las acciones del comportamiento y se acceden a través de la referencia del objeto.

Podemos tener propiedades y métodos públicos, privados y protegidos. Por defecto, las propiedades y métodos son públicos. Si son privados, sólo pueden ser accedidos desde la propia clase. Si son protegidos, sólo pueden ser accedidos desde la propia clase y sus subclases. De esta manera podemos encapsular y ocultar la información y acciones que deseemos.

```kotlin
// Definiendo una clase
class Persona {
    var nombre: String = ""
    var apellidos: String = ""
    private var experiencia: Int = 99

    fun programar(lenguaje: String) {
        println("Programando en $lenguaje")
    }
    private fun dormir() {
        println("Durmiendo...")
    }
}

// Instanciando un objeto
val persona = Persona()
persona.nombre = "José Luis"
persona.programar(lenguaje= "Kotlin")
// No puedo acceder a lo privados de la clase
```

## Constructores
Los constructores son métodos especiales que se utilizan para inicializar los objetos. Los constructores se definen en la clase y se ejecutan al instanciar un objeto. Los constructores pueden tener parámetros y pueden ser sobrecargados.

En Kotlin existe un constructor primario y uno secundario. El constructor primario se define en la cabecera de la clase y el secundario se define en el cuerpo de la clase. El constructor primario no puede tener código, pero el secundario sí. Si no se define ningún constructor, se crea un constructor primario vacío.

Inicializador de instancia: es un bloque de código que se ejecuta al instanciar un objeto. Se define en el cuerpo de la clase y se ejecuta antes del constructor secundario.

```kotlin
// Definiendo una clase con constructor primario
class Persona(nombre: String, apellidos: String, experiencia: Int = 0) {
    var nombre: String = ""
    var apellidos: String = ""

    private val experiencia: Int = 99
    private val nivel: Int = 0

    // Constructor secuendario 
    constructor(nombre: String, apellidos: String, experiencia: Int = 0, nivel: Int = 0) : this(nombre, apellidos, experiencia) {
        this.nivel = nivel
    }
    init {
        println("Inicializando instancia")
    }
    
    fun programar(lenguaje: String) {
        println("Programando en $lenguaje")
    }

    private fun dormir() {
        println("Durmiendo...")
    }
}
```

## Referencia this
La referencia this es una referencia al objeto actual. Se utiliza para acceder a los miembros de la clase. Si no se utiliza la referencia this, se accede a los miembros de la clase.

```kotlin
// Definiendo una clase con constructor primario
class Persona(nombre: String, apellidos: String, experiencia: Int = 0) {
    var nombre: String = ""
    var apellidos: String = ""

    private val experiencia: Int = 99
    private val nivel: Int = 0

    // Constructor secuendario, utilizando la referencia this para llamar al constructor primario
    // y acceder a los miembros de la clase y no a los parámetros del constructor
    constructor(nombre: String, apellidos: String, experiencia: Int = 0, nivel: Int = 0) : this(nombre, apellidos, experiencia) {
        this.nivel = nivel
    }
    init {
        println("Inicializando instancia")
    }
    
    fun programar(lenguaje: String) {
        println("Programando en $lenguaje")
    }

    private fun dormir() {
        println("Durmiendo...")
    }
    
    // usamos la referencia this para acceder a los miembros de la clase y no a los parámetros
    fun setExperiencia(experiencia: Int) {
        this.experiencia = experiencia
    }
}
```

## Getters y Setters
Los getters y setters son métodos especiales que se utilizan para acceder/cambiar a los atributos de un objeto. Los getters y setters se definen en la clase y se acceden a través de la referencia del objeto.
```kotlin
// Definiendo una clase con getters y setters
class Persona {
    var nombre: String = ""
    var apellidos: String = ""
    private var experiencia: Int = 99

    fun programar(lenguaje: String) {
        println("Programando en $lenguaje")
    }
    private fun dormir() {
        println("Durmiendo...")
    }
    
    // Getter
    fun getExperiencia(): Int {
        return experiencia
    }
    // Setter
    fun setExperiencia(experiencia: Int) {
        this.experiencia = experiencia
    }
}
```

En Kotlin podemos definir getters y setters de forma automática. Para ello, debemos definir los atributos con la palabra reservada var. Si definimos los atributos con la palabra reservada val, sólo se creará el getter.

Podemos crear campos calculados, es decir, campos que no se almacenan en memoria, sino que se calculan a partir de otros campos. Para ello, debemos definir el campo con la palabra reservada val y no con var.

También podemos cambiar como se almacenan los atributos en memoria. Por ejemplo, podemos almacenarlos en minúsculas o en mayúsculas. Para ello, debemos definir el getter y el setter de forma manual.

```kotlin
// Clase con getters y setters automáticos
class Persona {
    var nombre: String = ""
    var apellidos: String = ""
    private var experiencia: Int = 99

    fun programar(lenguaje: String) {
        println("Programando en $lenguaje")
    }
    private fun dormir() {
        println("Durmiendo...")
    }
    
    // Campos calculados
    val nombreCompleto: String
        get() = "$nombre $apellidos"

    // Campos con almacenamiento personalizado
    var experiencia: Int = 99
        get() = field
        set(value) {
            if (value > 0) {
                field = value
            } else {
                field = 0
            }
        }
}
```

## Igualdad e identidad
En Kotlin, para comparar objetos, debemos utilizar el operador ==. Este operador compara el contenido de los objetos (estado). Realmente ejecuta el método equals. Si queremos comparar la identidad de los objetos, debemos utilizar el operador ===. Este operador compara la referencia de los objetos (identidad).

En Java el operador == compara la identidad de los objetos. Para comparar el contenido de los objetos, debemos utilizar el método equals.

```kotlin
// Clase Persona
class Persona {
    var nombre: String = ""
    var apellidos: String = ""
    private var experiencia: Int = 99

    fun programar(lenguaje: String) {
        println("Programando en $lenguaje")
    }
    private fun dormir() {
        println("Durmiendo...")
    }
    
    // Campos calculados
    val nombreCompleto: String
        get() = "$nombre $apellidos"

    // Campos con almacenamiento personalizado
    var experiencia: Int = 99
        get() = field
        set(value) {
            if (value > 0) {
                field = value
            } else {
                field = 0
            }
        }

        // Sobreescribimos el método equals, solo serán iguales si tienen el mismo nombre y apellidos
        override fun equals(other: Any?): Boolean {
            if (other == null || other !is Persona) {
                return false
            }
            return nombre == other.nombre && apellidos == other.apellidos
        }
}

// Comparar con equals
val persona1 = Persona()
persona1.nombre = "Juan"
persona1.apellidos = "Pérez"

val persona2 = Persona()
persona2.nombre = "Juan"
persona2.apellidos = "Pérez"

println(persona1 == persona2) // true
println(persona1.equals(persona2)) // true
println(persona1 === persona2) // false

// Comparar con ===
val persona3 = persona1
println(persona1 === persona3) // true
```

## POJOS y POKOS. Data classes
Los POJOS (Plain Old Java Objects) son objetos simples que no tienen lógica de negocio en Java. Los POKOS (Plain Old Kotlin Objects) son objetos simples que no tienen lógica de negocio en Kotlin. En Kotlin, los POJOS y POKOS se definen como clases de datos. Para definir una clase de datos, debemos utilizar la palabra reservada data en Kotlin, en Java podremos usar los records.

Las data classes tienen los siguientes miembros:
- Constructor primario con los parámetros que se pasan al constructor.
- Propiedades deberían ser inmutables para cada parámetro del constructor primario.
- Método equals: compara el contenido de los objetos.
- Método hashCode: calcula el hash del objeto. Se utiliza para comparar objetos, pues dos objetos con el mismo hash son iguales.
- Método toString: devuelve una cadena con el nombre de la clase y los valores de los atributos.


Si las propiedades de la data class son inmutables, se creará un getter para cada propiedad. Si las propiedades de la data class son mutables, se creará un getter y un setter para cada propiedad. Podemos hacer uso de copy para crear una copia de la data class variando las propiedades que nos interesen.

```kotlin
// Definiendo una clase de persona como data class
data class Persona(val nombre: String, val apellidos: String, var experiencia: Int)

val persona1 = Persona("Juan", "Pérez", 99)
println(persona1) // Persona(nombre=Juan, apellidos=Pérez, experiencia=99)
println(persona1.nombre) // Juan

val persona2 = persona1.copy(nombre = "Pepe")
println(persona2) // Persona(nombre=Pepe, apellidos=Pérez, experiencia=99)

val persona3 = persona1.copy()
println(persona3) // Persona(nombre=Juan, apellidos=Pérez, experiencia=99)

println(persona1 == persona2) // false
println(persona1 == persona3) // true
println(persona1 === persona2) // false
println(persona1 === persona3) // false
println(persona1.hashCode() == persona2.hasCode()) // false
println(persona1.hashCode() == persona3.hasCode()) // true
```

Los métodos equals, hashCode y toString se generan automáticamente. Si queremos sobreescribirlos, debemos hacerlo manualmente. Esto nos permite poder usarlos en cualquier clase, no solo en las data classes.

```kotlin
// Clase Persona, equivalente a la data class Persona
class Persona(val nombre: String, val apellidos: String, var experiencia: Int) {
    // Sobreescribimos el método equals, solo serán iguales si tienen el mismo nombre y apellidos
    override fun equals(other: Any?): Boolean {
        if (other == null || other !is Persona) {
            return false
        }
        return nombre == other.nombre && apellidos == other.apellidos
    }

    // Sobreescribimos el método hashCode, solo serán iguales si tienen el mismo nombre y apellidos
    override fun hashCode(): Int {
        return nombre.hashCode() + apellidos.hashCode()
    }

    // Sobreescribimos el método toString, solo serán iguales si tienen el mismo nombre y apellidos
    override fun toString(): String {
        return "Persona(nombre=$nombre, apellidos=$apellidos, experiencia=$experiencia)"
    }
}
```

## Atributos y métodos de clase
Un atributo de clase es una variable miembro que no se asocia a un objeto (instancia) de una clase, sino que se asocia a la clase misma; no hay una copia del dato para cada objeto sino una sola copia que es compartida por todos los objetos de la clase. El acceso a las variables estáticas desde fuera de la clase donde se definen se realiza a través del nombre de la clase y no del nombre del objeto como sucede con las variables miembro normales (no estática). 

Para los métodos, la idea es la misma que para los datos: los métodos de clase se asocian a una clase, no a una instancia. Los métodos de clase se pueden invocar sin necesidad de crear una instancia de la clase.

En Java podemos definir atributos y métodos estáticos con la palabra reservada static. En Kotlin, no existe la palabra reservada static, pero podemos definir atributos y métodos estáticos con la palabra reservada companion object. Los atributos y métodos de companion object se pueden acceder sin necesidad de crear una instancia de la clase.

```kotlin
class Persona(val nombre: String, val apellidos: String, var experiencia: Int) {
    val id = Persona.nextId()

    override toString(): String {
        return "Persona(id=$id, nombre=$nombre, apellidos=$apellidos, experiencia=$experiencia)"
    }

    // Definimos un companion object, es decir los atributos y metodos de clase
    companion object {
        var contador = 0
        private fun nextId() {
            return contador++
        }

        fun gritar() {
            println("¡¡¡¡¡¡¡¡¡¡¡¡¡¡¡¡¡¡¡¡¡¡¡¡¡¡¡¡¡¡¡¡¡¡¡¡¡¡¡¡¡¡¡¡¡¡¡¡¡¡¡¡¡¡¡¡¡¡¡¡¡¡¡¡¡¡¡")
        }
    }
}

val persona1 = Persona("Juan", "Pérez", 99)
println(persona1) // Persona(id=1, nombre=Juan, apellidos=Pérez, experiencia=99)
val persona2 = Persona("Pepe", "García", 99)
println(persona2) // Persona(id=2, nombre=Pepe, apellidos=García, experiencia=99)
val persona3 = Persona("Ana", "García", 99)
println(persona3) // Persona(id=3, nombre=Ana, apellidos=García, experiencia=99)

Persona.gritar() // ¡¡¡¡¡¡¡¡¡¡¡¡¡¡¡¡¡¡¡¡¡¡¡¡¡¡¡¡¡¡¡¡¡¡¡¡¡¡¡¡¡¡¡¡¡¡¡¡¡¡¡¡¡¡¡¡¡
```

## Composición de objetos
La composición de objetos es una forma de reutilizar código. Consiste en crear una clase que contenga como atributos objetos de otras clases. De esta forma, podemos reutilizar los métodos de las clases que componen la clase que estamos creando.

Si es una relación 1-1 asignamos el objeto como atributo de la clase. Si es una relación 1-N asignamos una colección de objetos como atributo de la clase.

```kotlin
// una persona tiene un coche
data class Coche(val marca: String, val modelo: String, val color: String)
data class Persona(val nombre: String, val apellidos: String, val coche: Coche)

// una persona tiene varios coches
data class Persona(val nombre: String, val apellidos: String, val coches: Array<Coche>)
```

## Enums class
Los tipos enumerados son una forma de definir un conjunto de constantes. En Kotlin, los tipos enumerados se definen con la palabra reservada enum class. Los valores de un tipo enumerado se pueden acceder con el nombre de la clase y el nombre del valor separados por un punto. A veces es necesario acceder al valor de un tipo enumerado como un objeto, en ese caso podemos usar la función valueOf(). Por otro lado, podemos almacenar un valor en base a su constructor si lo definimos (solo en Kotlin).

```kotlin
// Enums colores
enum class Color {
    ROJO, VERDE, AZUL
}

// Accedemos a los valores del enum
println(Color.ROJO) // ROJO
println(Color.VERDE) // VERDE
println(Color.AZUL) // AZUL

// Accedemos a los valores del enum como objetos
println(Color.valueOf("ROJO")) // ROJO
println(Color.valueOf("VERDE")) // VERDE
println(Color.valueOf("AZUL")) // AZUL

// saber el orden de los valores del enum
println(Color.ROJO.ordinal) // 0
println(Color.VERDE.ordinal) // 1

// Obtener values del enum
val colores = Color.values()
println(colores) // [ROJO, VERDE, AZUL]

// Enums con constructor, solo en Kotlin
enum class Color(val rgb: Int) {
    ROJO(0xFF0000),
    VERDE(0x00FF00),
    AZUL(0x0000FF)
}

// Accedemos a los valores del enum
println(Color.ROJO) // ROJO
// Obtenemos el valor rgb
println(Color.ROJO.rgb) // 0xFF0000
```


## Recursos
- Twitter: https://twitter.com/joseluisgonsan
- GitHub: https://github.com/joseluisgs
- Web: https://joseluisgs.github.io
- Discord del módulo: https://discord.gg/RRGsXfFDya
- Aula DAMnificad@s: https://discord.gg/XT8G5rRySU


## Autor

Codificado con :sparkling_heart: por [José Luis González Sánchez](https://twitter.com/joseluisgonsan)

[![Twitter](https://img.shields.io/twitter/follow/joseluisgonsan?style=social)](https://twitter.com/joseluisgonsan)
[![GitHub](https://img.shields.io/github/followers/joseluisgs?style=social)](https://github.com/joseluisgs)

### Contacto
<p>
  Cualquier cosa que necesites házmelo saber por si puedo ayudarte 💬.
</p>
<p>
 <a href="https://joseluisgs.github.io/" target="_blank">
        <img src="https://joseluisgs.github.io/img/favicon.png" 
    height="30">
    </a>  &nbsp;&nbsp;
    <a href="https://github.com/joseluisgs" target="_blank">
        <img src="https://distreau.com/github.svg" 
    height="30">
    </a> &nbsp;&nbsp;
        <a href="https://twitter.com/joseluisgonsan" target="_blank">
        <img src="https://i.imgur.com/U4Uiaef.png" 
    height="30">
    </a> &nbsp;&nbsp;
    <a href="https://www.linkedin.com/in/joseluisgonsan" target="_blank">
        <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/c/ca/LinkedIn_logo_initials.png/768px-LinkedIn_logo_initials.png" 
    height="30">
    </a>  &nbsp;&nbsp;
    <a href="https://discordapp.com/users/joseluisgs#3560" target="_blank">
        <img src="https://logodownload.org/wp-content/uploads/2017/11/discord-logo-4-1.png" 
    height="30">
    </a> &nbsp;&nbsp;
    <a href="https://g.dev/joseluisgs" target="_blank">
        <img loading="lazy" src="https://googlediscovery.com/wp-content/uploads/google-developers.png" 
    height="30">
    </a>    
</p>

### ¿Un café?
<p><a href="https://www.buymeacoffee.com/joseluisgs"> <img align="left" src="https://cdn.buymeacoffee.com/buttons/v2/default-blue.png" height="50" alt="joseluisgs" /></a></p><br><br><br>

## Licencia de uso

Este repositorio y todo su contenido está licenciado bajo licencia **Creative Commons**, si desea saber más, vea la [LICENSE](https://joseluisgs.github.io/docs/license/). Por favor si compartes, usas o modificas este proyecto cita a su autor, y usa las mismas condiciones para su uso docente, formativo o educativo y no comercial.

<a rel="license" href="http://creativecommons.org/licenses/by-nc-sa/4.0/"><img alt="Licencia de Creative Commons" style="border-width:0" src="https://i.creativecommons.org/l/by-nc-sa/4.0/88x31.png" /></a><br /><span xmlns:dct="http://purl.org/dc/terms/" property="dct:title">JoseLuisGS</span> by <a xmlns:cc="http://creativecommons.org/ns#" href="https://joseluisgs.github.io/" property="cc:attributionName" rel="cc:attributionURL">José Luis González Sánchez</a> is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by-nc-sa/4.0/">Creative Commons Reconocimiento-NoComercial-CompartirIgual 4.0 Internacional License</a>.<br />Creado a partir de la obra en <a xmlns:dct="http://purl.org/dc/terms/" href="https://github.com/joseluisgs" rel="dct:source">https://github.com/joseluisgs</a>.
