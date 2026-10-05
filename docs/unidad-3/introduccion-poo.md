# Introducción a la programación orientada a objetos en PHP

## ¿Por qué utilizar programación orientada a objetos?

Hasta ahora hemos desarrollado programas utilizando variables, estructuras de control y funciones. Este enfoque resulta adecuado para aplicaciones pequeñas, pero, a medida que los proyectos crecen, aumenta la dificultad para organizar el código y reutilizar funcionalidades.

La programación orientada a objetos (POO) permite estructurar una aplicación en elementos llamados **objetos**, que agrupan datos y comportamientos relacionados.

!!! info "Idea clave"
    La POO facilita la reutilización, el mantenimiento y la escalabilidad de las aplicaciones.

### Ventajas de la programación orientada a objetos

- Mayor organización del código.
- Reutilización de funcionalidades.
- Facilita el mantenimiento de aplicaciones complejas.
- Reduce la duplicidad de código.
- Permite modelar entidades del mundo real.
- Favorece el trabajo colaborativo.

!!! example "Ejemplo de entidades"
    En una aplicación académica podríamos identificar las clases:

    - `Alumno`
    - `Profesor`
    - `Modulo`
    - `Matricula`

---

## La orientación a objetos en PHP

PHP nació como un lenguaje orientado principalmente al desarrollo web mediante programación procedural. Sin embargo, actualmente dispone de un completo soporte para programación orientada a objetos.

!!! info "Características disponibles"
    PHP incorpora soporte para:

    - Clases.
    - Objetos.
    - Herencia.
    - Polimorfismo.
    - Interfaces.
    - Clases abstractas.
    - Namespaces.

Por este motivo, la mayor parte de las aplicaciones PHP modernas se desarrollan siguiendo este paradigma.

!!! tip "PHP moderno"
    Utiliza siempre tipado en propiedades, parámetros y valores de retorno cuando sea posible.

---

## Recordatorio de conceptos fundamentales

Los conceptos fundamentales de la programación orientada a objetos ya fueron estudiados previamente utilizando Java.

A lo largo de esta unidad asumiremos que conoces conceptos como:

- Clase.
- Objeto.
- Atributo.
- Método.
- Encapsulación.
- Herencia.
- Polimorfismo.

Nuestro objetivo será aprender cómo se implementan estos mecanismos en PHP.

---

## Diferencias entre Java y PHP

Aunque ambos lenguajes permiten trabajar con orientación a objetos, existen algunas diferencias importantes.

### Declaración de variables

!!! example "Variables en Java y PHP"

    Java:

    ```java
    String nombre = "Ana";
    int edad = 20;
    ```

    PHP:

    ```php
    $nombre = 'Ana';
    $edad = 20;
    ```

### Acceso a propiedades y métodos

!!! example "Acceso a atributos"

    Java:

    ```java
    this.nombre;
    ```

    PHP:

    ```php
    $this->nombre;
    ```

### Creación de objetos

!!! example "Instanciación"

    Java:

    ```java
    Alumno alumno = new Alumno();
    ```

    PHP:

    ```php
    $alumno = new Alumno();
    ```

### Constructores

!!! example "Constructores"

    Java:

    ```java
    public Alumno(String nombre) {
        this.nombre = nombre;
    }
    ```

    PHP:

    ```php
    public function __construct(string $nombre)
    {
        $this->nombre = $nombre;
    }
    ```

### Tipado

En las versiones actuales de PHP es posible declarar tipos en propiedades, parámetros y valores de retorno.

!!! example "Tipado en PHP 8.2"

    ```php
    private string $nombre;

    public function obtenerNombre(): string
    {
        return $this->nombre;
    }
    ```

!!! warning "Atención"
    Aunque PHP permite tipado estricto, su sistema de tipos sigue siendo diferente al de Java.

---

## La programación orientada a objetos en aplicaciones web

La orientación a objetos facilita el desarrollo de aplicaciones web complejas.

!!! example "Modelado de una tienda online"

    ```text
    Producto
    Usuario
    Pedido
    Carrito
    Categoria
    ```

Cada clase se encarga de gestionar la información y el comportamiento relacionados con una responsabilidad concreta.

### Beneficios en aplicaciones web

- Código más organizado.
- Mayor reutilización.
- Menor coste de mantenimiento.
- Facilidad para ampliar funcionalidades.

---

## Resumen

En este apartado hemos recordado los conceptos fundamentales de la programación orientada a objetos y hemos analizado algunas de las principales diferencias entre Java y PHP.

!!! note "Recuerda"
    En los siguientes apartados trabajaremos con clases, objetos y mecanismos propios de PHP utilizando sintaxis compatible con PHP 8.2.

---

## Actividad propuesta

### Actividad 1. Java y PHP

A partir de la siguiente clase escrita en Java:

```java
public class Alumno {

    private String nombre;

    public Alumno(String nombre) {
        this.nombre = nombre;
    }
}
```

1. Identifica el atributo de la clase.
2. Indica cuál es su constructor.
3. Escribe una versión equivalente utilizando PHP.

!!! tip "Consejo"
    Compara la sintaxis de ambos lenguajes e identifica los elementos que cambian.
