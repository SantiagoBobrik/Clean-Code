# Clean Code

Este es un resumen o apunte personal basado en los libros [Clean Code](https://www.amazon.com/-/es/Robert-C-Martin/dp/0132350882) de Robert C. Martin, [Clean Javascritp](https://softwarecrafters.io/javascript/clean-code-javascript) de Software Crafters y mucho google.
Y su objetivo principal es mejorar las buenas practicas y escritura de codigo.

## Intro

> *Clean Code es aquel que se ha escrito con la intención de que otra persona (o vos en el futuro) lo entienda.*

Tratar de entender el código de un tercero, o incluso el que escribimos nosotros hace tan solo unas semanas, se puede volver una tarea realmente difícil. Es por eso que hacer un esfuerzo extra para que nuestra solución sea legible e intuitiva es la base para que sea todo más llevadero y sobre todo barato.

## Principios y conceptos

### Deuda técnica

La deuda  técnica trata de explicar que la falta de calidad en el código de un proyecto de software genera una deuda que repercutirá en sobre costos futuros.

### **¿Cómo paga un desarrollador la deuda técnica?**

**La refactorizacion.**

La factorización  es simplemente un proceso que tiene como objetivo mejorar el código de un proyecto sin alterar su comportamiento para que sea más entendible y tolerante a los cambios.

Aveces es inevitable caer en la deuda técnica, pero está buenísimo ser consciente y pagarla lo antes posible.

Debemos re factorizar cuando detectamos algún **CODE SMELL.**

### Code Smell

Un Code Smell, también conocido como un código rancio,  son una serie de síntomas en el código que nos vienen a indicar que tal vez no se están haciendo las cosas de una forma del todo correcta, lo que puede llevar a que haya algún problema a futuro y un problema de trasfondo.

**Características**:

- No siempre es un bug.
- Indican deficiencias de diseño.
- Riesgo alto de errores o fallas a futuro.

Los **code smell**  más comunes son como por ejemplo, duplicidad de código, funciones muy grandes o clases enormes.

### Ley boy scout

Esta es una regla muy sencilla, consiste simplemente en hacer lo mismo que hacen los Boy Scout cada vez que salen al campo, y es dejar la zona cuando se marchan un poquito mejor de lo que la encontraron al llegar.

 No hace falta una limpieza masiva, esto se trata de cambiar el nombre a una variable mal nombrada, desacoplar una función, simplificar sentencias if, etc.

Si todos entregamos el código más limpio de lo que lo recibimos, este mismo mejoraría constantemente con el tiempo.

### Principio DRY

Teniendo en cuenta que la duplicidad de código puede llevarnos a muchos problemas, una muy buena practica es implementar el principio **DRY** (don’t repeat yourself), que en el español significa no repetirse

Cuando el principio **DRY** se aplica de forma eficiente, los cambios en cualquier parte de la aplicación requieren cambios en un único lugar. Por el contrario, si algunas partes del proceso están repetidas por varios sitios, los cambios pueden provocar fallos con mayor facilidad si todos los sitios en los que aparece no se encuentran sincronizados.

### Principio Tell don't ask

El principio Tell Don’t Ask dice que no se debe preguntar a un objeto sobre su estado para luego realizar una acción. Por el contrario, debe realizar la acción directamente.

### SOLID (por [Tienda Nube](https://github.com/TiendaNube/php-programming-best-practices))

SOLID es un acrónimo donde cada letra representa un principio del diseño orientado a objetos. Los cinco principios están muy relacionados entre si y nos brindan distintas técnicas para crear código de alta calidad.

- S: Principio de responsabilidad única (SRP)
- O: Principio abierto/cerrado (OCP)
- L: Principio de sustitución de Liskov (LSP)
- I: Principio de la segregación de la interfaz (ISP)
- D: Principio de la inversión de dependencias (DIP)

**Principio de responsabilidad única (SRP)**

El Principio de Responsabilidad Única (SRP) es la S del Principio SOLID y nos dice que una clase debe tener un único motivo por el cual debe ser modificada.

**Principio abierto/cerrado (OCP)**

Las entidades de software (clases, módulos, funciones, etc) deben ser abiertas para ser extendidas, pero cerradas para modificarlas. Este principio establece que puedes permitir a tus colegas desarrolladores agregar nuevas funcionalidades pero sin cambiar el código existente.

Parece complicado pero gracias a las interfaces y abstracciones se convierte en algo muy simple.

**Principio de sustitución de Liskov (LSP)**

El principio de Liskov establece que, dada una clase padre y una clase hija, pueden intercambiarse sin obtener resultados incorrectos.

La conclusión aca es que si se anulando gran parte del código, entonces tal vez la arquitectura no sea la correcta y se debería pensar en el principio de sustitución de Liskov.

**Principio de la segregación de la interfaz (ISP)**

El principio de segregación de la interfaz dice que un cliente solo debe conocer los métodos que van a utilizar y no aquellos que no utilizará.

**Principio de la inversión de dependencias (DIP)**

El principio de la inversión de dependencias consiste en que las clases no deben depender de clases concretas, sino que deben depender de abstracciones.

## Naming

### Variables.

Nuestro código debería poder leerse  con la misma facilidad que un texto, es por eso elegir buenos nombres para variables, métodos y clases deben  seleccionarse contemplando que den expresividad y significado a nuestro código.

### Nombres pronunciables y expresivos.

Los nombres siempre priorizarlos en ingles, debe ser pronunciables, no deben llevar abreviaturas, guion bajo o medio, siempre es prioridad *camelCase*  y también no debemos ahorrarnos caracteres.

**MAL**

```php
$yyyymmdstr = date('Y-m-d');
```

**BIEN**

```php
$currentDate= date('Y-m-d');
```

### Léxico coherente

Debemos mantener el mismo vocabulario para referirnos a la misma cosa en lugares diferentes.

**MAL**

```php
$user  = new User();
$client =  new User();
```

**BIEN**

```php
$user  = new User();
```

### Nombres según el tipo de dato

**Arrays**

Los arrays al ser un conjunto de elementos siempre es buena idea usar la forma plural de su contenido,  ej.: users, fruits.

**MAL**

```php
$fruit = ['manzana', 'platano', 'fresa'];
```

**BIEN**

```php
//Regular
$fruits = ['manzana', 'platano', 'fresa'];
//Bien
$fruitNames = ['manzana', 'platano', 'fresa'];
```

**Booleanos**

Los booleanos solo pueden tener dos valores, verdadero o falso, por eso el uso de prefijos es la mejor opción, ej.: is, has, can. isEmpty, hasFruits,  canWrite

**MAL**

```php
$open = true;
```

**BIEN**

```php
$isOpen= true;
```

**Números**

Para números es interesante escoger palabras que describan que son, ej.: max, min.

**MAL**

```php
$users= 3;
```

**BIEN**

```php
$totalUsers= 3;
$maxUsers =  2;
```

**Funciones**

> *Cuanto más reducida es la función más fácil es asignarle un nombre.*

Los nombres de las funciones deben representar acciones, por lo que se deben construir de un verbo seguido de un sustantivo. Esto quiere decir que el nombre de la función debe expresar lo que hace,  ej.: createUser, updateUser, sendEmail. 

Se puede resumir en : 

- Que vamos a hacer (update, create, get)
- Sobre que lo vamos a hacer (user, email,contact)
- Y opcionalmente al final le podemos poner la condicion (byId)

**MAL**

```php
$this->createUserIfNotExists();
$this->createProcesoVenta();
```

**BIEN**

```php
$this->createUser();
$this->createVenta();
```

**Clases**

Los nombre para las clases y objetos deben estar formados por sustantivos o frases con estos mismos y debemos evitar nombres genéricos a toda costa, ya que esto ultimo nos dará la tendencia a crear clases con múltiples responsabilidades, ej.: User, UserProfile.

## Funciones

> *Sabemos que estamos desarrollando código limpio cuando cada función hace exactamente lo que su nombre indica, por eso las funciones debe hacer una única cosa y hacerla bien.*

### Tamaño

El tamaño de la función suele variar dependiendo la complejidad del problema o la lógica de negocio, generalmente un tamaño óptimo de una función oscila entre las 5 y 20 líneas de código, pero suele haber casos donde la función no pueda ser dividida y requiera más lineas del tamaño óptimo.

### Números de argumentos

Siempre es bueno delimitar el número de parámetros a un máximo de 3, si llegado al caso de que necesitemos enviar más de un parámetro siempre es buena opción pasarle un array u objeto.

**MAL**

```php
function updateUser($name,$age,$id,$email){...};
```

**BIEN**

```php
$user = ["name" => $name , "age" => $age , "id" => $id , "email" => $email];
//OR
$user = new User();

function updateUser($user){...};
```

### Funciones Anónimas

La mejor forma de definir un nombre para una función es no tener que hacerlo por eso siempre que el contexto lo permita una función anónima siempre es una buena elección.

### Funciones Puras/Transparencia Referencial

Una forma muy rápida  de definir a las Funciones Puras sería decir que son aquellas que operan utilizando solo los parámetros de entrada sin recurrir a ningún otro elemento fuera de ellas.

Las Funciones Puras son aquellas que cumplen con dos requisitos básicos:

- Dado unos parámetros de entrada, la función siempre devolverá el mismo resultado.
- El cómputo de la función, su lógica, no implica ningún efecto observable colateral fuera de ella.

**EJEMPLO**

```php
function sumNumbers($a, $b) {
	return $a + $b;
}

sumNumbers(1,2) // 3
sumNumbers(2,2) // 4
```

### Separación de consultas de comandos/acciones

Las funciones deben hacer algo o responder algo, pero no las dos. Una función debe cambiar el estado de un objeto o devolver información del mismo, pero ambas operaciones juntas causan confusión.

## Comentarios

> *El uso de comentarios permite compensar nuestra incapacidad de escribir código.*

- No hay nada más útil que un comentario bien colocado.
- No hay nada que colapse más un módulo que un comentario innecesario.
- No hay nada más dañino que un comentario antiguo que propague mentiras y desinformación.

### Los comentarios no compensan el código incorrecto.

Una de las principales motivaciones para crear comentarios es el codigo incorrecto.

Creamos un módulo y sabemos que es confuso y está desorganizado. Sabemos que está mal y entonces decidimos comentar que es ese código. Error

### Comentarios permitidos.

Los comentarios permitidos suelen ser varios y dependen de la situación, unos claros ejemplos son los comentarios informativos  que tratan de proporcionar información básica de un método o una expresión regular, 

Otro permitido también son los comentarios de advertencia, estos nos indican que el siguiente código puede generar consecuencias o se debe tener en cuenta para ciertas acciones como por ejemplo la conexión a la base de datos donde advertimos setear el entorno de prueba.

 Otro ejemplo son los comentarios TODO (por hacer) en estos comentarios indicamos que el siguiente código está en desarrollo o esta a la espera de una decisión de diseño.

**EJEMPLO**

```php

//En ambiente local quitar la conexion a la db de prod.
$dbConnection = new PDO($dsn, $usuario, $contraseña)

//TODO Esperando confirmacion feature
function updateUserAge(){...}
```

### Comentarios incorrectos.

Hay muchos comentarios que pertenecen a esta categoría siempre acompañada de código poco expresivo.

### Balbucear

No sirve de nada escribir un comentario que no tenga sentido o que no aporte nada al desarrollador que lea ese código. Si se  escribe un comentario hay que tomarse el tiempo de que esté bien redactado.

**EJEMPLO**

```php
//Retorna null si el idServicio es igual a 5 sino retorna false
```

### Comentarios Redundantes

Si hay funciones, bloques de código, etc que con solo leerlos entendemos de que va, no hace falta agregar un comentario explicando lo obvio. Seguramente tardemos más en leer el comentario que el propio código en sí.

**EJEMPLO**

```php
//Usuario por id
function getUserById(){...}
```

### Comentarios confusos

A pesar de las buenas intenciones de un comentario, este mismo al realizar una afirmación de que no es del todo precisa  puede desencadenar un problema aún más grande para el desarrollador que implemente ese bloque de código basado en la afirmación del comentario.

```php
//Retorna null si age es menor a 21
function sendBeerToUser($age){
	if($age == 21) return null;
	return new Beer();
}
```

### Código Comentado

**¡No dejar código comentado!**

El código comentado se convierte en código valioso que ningún desarrollador se atreverá a borrar porque entiende de que si está comentado es por algo o es de gran utilidad para el sistema. Esto lo único que genera es propagar código comentado por todo el proyecto.
