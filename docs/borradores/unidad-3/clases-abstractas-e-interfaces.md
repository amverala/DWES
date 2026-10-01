# Clases abstractas e interfaces

## El problema de las clases demasiado generales

Supongamos que estamos trabajando con la siguiente jerarquía:

```text
Figura
│
├── Circulo
├── Rectangulo
└── Triangulo
```

Todas las figuras deben ser capaces de calcular su área.

!!! example "Clase poco útil"

    ```php
    class Figura
    {
        public function calcularArea(): float
        {
            return 0;
        }
    }
    ```

La clase `Figura` es demasiado genérica.

## ¿Qué es una clase abstracta?

!!! info "Idea clave"

    Una clase abstracta define una base común para varias clases relacionadas y no puede instanciarse directamente.

## Definiendo una clase abstracta

!!! example "Clase abstracta"

    ```php
    abstract class Figura
    {
    }
    ```

```php
$figura = new Figura();
```

El código anterior produciría un error.

## Métodos abstractos

!!! example "Método abstracto"

    ```php
    abstract class Figura
    {
        abstract public function calcularArea(): float;
    }
    ```

## Implementando métodos abstractos

!!! example "Figura circular"

    ```php
    class Circulo extends Figura
    {
        public function __construct(
            private float $radio
        ) {}

        public function calcularArea(): float
        {
            return pi() * $this->radio ** 2;
        }
    }
    ```

!!! example "Rectángulo"

    ```php
    class Rectangulo extends Figura
    {
        public function __construct(
            private float $base,
            private float $altura
        ) {}

        public function calcularArea(): float
        {
            return $this->base * $this->altura;
        }
    }
    ```

## Clases abstractas con implementación

!!! example "Métodos heredados"

    ```php
    abstract class Figura
    {
        abstract public function calcularArea(): float;

        public function mostrarTipo(): void
        {
            echo 'Figura geométrica';
        }
    }
    ```

---

# Interfaces

## ¿Qué es una interfaz?

!!! info "Idea clave"

    Una interfaz define un contrato que las clases deben cumplir.

## Definiendo una interfaz

!!! example "Interfaz Exportable"

    ```php
    interface Exportable
    {
        public function exportar(): string;
    }
    ```

## Implementando una interfaz

!!! example "Implementación"

    ```php
    class Informe implements Exportable
    {
        public function exportar(): string
        {
            return 'Datos exportados';
        }
    }
    ```

## Implementación múltiple

!!! example "Varias interfaces"

    ```php
    interface Exportable
    {
        public function exportar(): string;
    }

    interface Imprimible
    {
        public function imprimir(): void;
    }

    class Informe implements Exportable, Imprimible
    {
        public function exportar(): string
        {
            return 'Exportando';
        }

        public function imprimir(): void
        {
            echo 'Imprimiendo';
        }
    }
    ```

## Diferencias entre clases abstractas e interfaces

| Característica | Clase abstracta | Interfaz |
|---------------|---------------|-----------|
| Puede contener implementación | ✅ | ❌ |
| Puede contener propiedades | ✅ | ❌ |
| Se utiliza con `extends` | ✅ | ❌ |
| Se utiliza con `implements` | ❌ | ✅ |
| Implementación múltiple | ❌ | ✅ |

!!! warning "Error frecuente"

    No confundas `extends` con `implements`. Las clases heredan clases abstractas e implementan interfaces.

## ¿Cuándo utilizar cada una?

!!! tip "Clase abstracta"

    Utilízala cuando quieras compartir comportamiento y código común.

!!! tip "Interfaz"

    Utilízala cuando necesites definir capacidades o contratos comunes.

## Ejemplo completo

!!! example "Sistema de documentos"

    ```php
    interface Exportable
    {
        public function exportar(): string;
    }

    abstract class Documento
    {
        public function __construct(
            protected string $titulo
        ) {}
    }

    class Informe extends Documento implements Exportable
    {
        public function exportar(): string
        {
            return "Exportando informe: {$this->titulo}";
        }
    }
    ```

## Buenas prácticas

!!! tip "Recomendaciones"

    - Utiliza clases abstractas para compartir comportamiento.
    - Utiliza interfaces para definir contratos.
    - Mantén las interfaces pequeñas y cohesionadas.
    - Diseña pensando en el polimorfismo.

## Resumen

Hemos aprendido a:

- Crear clases abstractas.
- Definir métodos abstractos.
- Implementar interfaces.
- Utilizar varias interfaces en una misma clase.
- Diferenciar cuándo utilizar cada mecanismo.

!!! note "Próximo paso"

    En el siguiente tema estudiaremos los miembros estáticos y las constantes de clase.

## Actividades propuestas

### Actividad 9. Sistema de pagos

Diseña una clase abstracta `MetodoPago` y las clases `Tarjeta`, `PayPal` y `Bizum`.

### Actividad 10. Exportación de informes

Diseña una interfaz `Exportable` e impleméntala en varias clases diferentes.
