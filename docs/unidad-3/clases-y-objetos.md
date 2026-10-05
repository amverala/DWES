# Clases y objetos

## ¿Qué es una clase?

Cuando desarrollamos una aplicación orientada a objetos necesitamos representar las distintas entidades que intervienen en ella.

Por ejemplo, en una aplicación de gestión académica podríamos encontrar elementos como:

- Alumnos.
- Profesores.
- Módulos.
- Matrículas.

Cada una de estas entidades puede representarse mediante una clase.

!!! info "Idea clave"

    Una clase es una plantilla que define los datos y comportamientos que tendrán los objetos creados a partir de ella.

Una clase describe:

- Qué información almacenarán los objetos.
- Qué operaciones podrán realizar.

## Definiendo una clase

En PHP las clases se definen mediante la palabra reservada `class`.

!!! example "Nuestra primera clase"

    ```php
    class Alumno
    {
    }
    ```

## ¿Qué es un objeto?

Un objeto es una instancia concreta de una clase.

!!! example "Clase y objetos"

    ```text
    Clase: Alumno

    Objetos:
    - Ana
    - Pedro
    - Lucía
    ```

## Propiedades

Las propiedades representan la información que almacena un objeto.

!!! example "Definiendo propiedades"

    ```php
    class Alumno
    {
        public string $nombre;
        public string $apellidos;
        public int $edad;
    }
    ```

## Propiedades tipadas en PHP 8.2

!!! info "PHP moderno"

    Utilizar propiedades tipadas ayuda a detectar errores y hace el código más fácil de mantener.

!!! warning "Error frecuente"

    En PHP 8.2, acceder a una propiedad tipada que no ha sido inicializada provoca un error.

## Creación de objetos

Para crear objetos se utiliza la palabra reservada `new`.

!!! example "Creando un objeto"

    ```php
    $alumno = new Alumno();
    ```

## Accediendo a las propiedades

Para acceder a las propiedades de un objeto se utiliza el operador `->`.

!!! example "Asignando valores"

    ```php
    $alumno = new Alumno();

    $alumno->nombre = 'Ana';
    $alumno->apellidos = 'Martínez';
    $alumno->edad = 20;
    ```

!!! example "Leyendo propiedades"

    ```php
    echo $alumno->nombre;
    ```

Resultado:

```text
Ana
```

## Un primer ejemplo completo

!!! example "Clase Alumno"

    ```php
    class Alumno
    {
        public string $nombre;
        public string $apellidos;
        public int $edad;
    }

    $alumno = new Alumno();

    $alumno->nombre = 'Ana';
    $alumno->apellidos = 'Martínez';
    $alumno->edad = 20;
    ```

# Métodos

Los objetos también pueden realizar acciones mediante métodos.

!!! info "Idea clave"

    Un método es una función definida dentro de una clase.

## Definiendo métodos

!!! example "Nuestro primer método"

    ```php
    class Alumno
    {
        public function saludar(): void
        {
            echo 'Hola';
        }
    }
    ```

## Ejecutando métodos

!!! example "Llamando a un método"

    ```php
    $alumno = new Alumno();
    $alumno->saludar();
    ```

## Métodos con parámetros

!!! example "Método con parámetros"

    ```php
    class Alumno
    {
        public function saludar(string $nombre): void
        {
            echo "Hola $nombre";
        }
    }
    ```

## Métodos con valor de retorno

!!! example "Método con retorno"

    ```php
    class Calculadora
    {
        public function sumar(int $a, int $b): int
        {
            return $a + $b;
        }
    }
    ```

# La referencia $this

!!! info "¿Qué representa $this?"

    `$this` hace referencia al objeto que está ejecutando el método.

## Accediendo a propiedades mediante $this

!!! example "Uso de $this"

    ```php
    class Alumno
    {
        public string $nombre;

        public function mostrarNombre(): void
        {
            echo $this->nombre;
        }
    }
    ```

## ¿Por qué es necesario $this?

!!! example "Variable local y propiedad"

    ```php
    class Alumno
    {
        public string $nombre;

        public function cambiarNombre(string $nombre): void
        {
            $this->nombre = $nombre;
        }
    }
    ```

# Modificadores de acceso

PHP dispone de tres niveles principales de visibilidad.

## Public

!!! example "Propiedad pública"

    ```php
    public string $nombre;
    ```

## Private

!!! example "Propiedad privada"

    ```php
    private string $nombre;
    ```

## Protected

!!! example "Propiedad protegida"

    ```php
    protected string $nombre;
    ```

## Comparativa de visibilidad

| Modificador | Misma clase | Clase hija | Exterior |
|-------------|------------|------------|----------|
| public | ✅ | ✅ | ✅ |
| protected | ✅ | ✅ | ❌ |
| private | ✅ | ❌ | ❌ |

# Un ejemplo completo

!!! example "Clase Alumno completa"

    ```php
    class Alumno
    {
        public string $nombre;
        public string $apellidos;
        public int $edad;

        public function mostrarDatos(): void
        {
            echo "Nombre: {$this->nombre}<br>";
            echo "Apellidos: {$this->apellidos}<br>";
            echo "Edad: {$this->edad}";
        }
    }
    ```

# Buenas prácticas

!!! tip "Recomendaciones"

    - Utiliza nombres descriptivos.
    - Una clase por archivo.
    - Declara tipos en propiedades y métodos.
    - Evita clases con demasiadas responsabilidades.

# Resumen

En este apartado hemos aprendido a trabajar con clases, objetos, propiedades, métodos, visibilidad y la referencia `$this`.

!!! note "Próximo paso"

    En el siguiente tema aprenderemos a utilizar constructores y encapsulación.

# Actividad propuesta

## Actividad 2. Gestionando alumnos

Crea una clase `Alumno` que:

- Almacene nombre, apellidos y edad.
- Disponga de un método `saludar()`.
- Disponga de un método `mostrarDatos()`.
- Permita crear al menos dos objetos diferentes.

!!! tip "Consejo"

    Comprueba que cada objeto mantiene sus propios datos de forma independiente.
