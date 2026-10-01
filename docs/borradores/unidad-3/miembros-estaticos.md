# Miembros estáticos

## Objetos y clases

Hasta ahora hemos trabajado siempre con objetos.

```php
$alumno = new Alumno();
```

!!! info "Idea clave"

    Los miembros estáticos pertenecen a la clase y no a los objetos creados a partir de ella.

## ¿Qué es un miembro estático?

Un miembro estático es una propiedad o método asociado directamente a una clase.

```php
class Ejemplo
{
    public static string $mensaje;
}
```

## Propiedades estáticas

!!! example "Contador de alumnos"

    ```php
    class Alumno
    {
        public static int $totalAlumnos = 0;
    }
    ```

## Accediendo a propiedades estáticas

!!! example "Acceso"

    ```php
    echo Alumno::$totalAlumnos;
    ```

## Contador de instancias

!!! example "Uso práctico"

    ```php
    class Alumno
    {
        public static int $totalAlumnos = 0;

        public function __construct()
        {
            self::$totalAlumnos++;
        }
    }
    ```

## Métodos estáticos

!!! example "Método estático"

    ```php
    class Utilidades
    {
        public static function saludar(): void
        {
            echo 'Hola';
        }
    }
    ```

Uso:

```php
Utilidades::saludar();
```

## ¿Cuándo utilizar métodos estáticos?

!!! tip "Casos habituales"

    - Métodos utilitarios.
    - Cálculos matemáticos.
    - Conversión de datos.
    - Funciones que no dependen del estado de un objeto.

## La palabra clave self

!!! info "Importante"

    `self` hace referencia a la clase actual, mientras que `$this` hace referencia al objeto actual.

!!! example "Utilización de self"

    ```php
    class Alumno
    {
        public static int $total = 0;

        public function __construct()
        {
            self::$total++;
        }
    }
    ```

## Diferencias entre self y $this

| Elemento | Referencia |
|-----------|-----------|
| `$this` | Objeto actual |
| `self` | Clase actual |

## Constantes de clase

!!! example "Constante"

    ```php
    class Configuracion
    {
        public const VERSION = '1.0';
    }
    ```

Acceso:

```php
echo Configuracion::VERSION;
```

## Limitaciones de los miembros estáticos

!!! warning "Importante"

    Los métodos estáticos no pueden acceder a propiedades de instancia mediante `$this`.

## Buenas prácticas

!!! tip "Recomendaciones"

    - Usa miembros estáticos sólo cuando no necesites un objeto.
    - Evita abusar del estado global.
    - Utiliza constantes para valores inmutables.

## Ejemplo completo

!!! example "Clase Utilidades"

    ```php
    class Utilidades
    {
        public const VERSION = '1.0';

        public static function obtenerVersion(): string
        {
            return self::VERSION;
        }
    }
    ```

## Resumen

Hemos aprendido a utilizar propiedades estáticas, métodos estáticos, `self` y constantes de clase.

## Actividades propuestas

### Actividad 11. Contador de visitantes

Implementa una clase que contabilice cuántos objetos se han creado.

### Actividad 12. Biblioteca matemática

Implementa una clase `Matematicas` con métodos estáticos.

### Actividad 13. Configuración de la aplicación

Define constantes para almacenar versión, nombre y curso académico.
