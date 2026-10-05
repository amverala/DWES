# Constructores y encapsulación

## El problema de la inicialización de objetos

En el apartado anterior hemos aprendido a crear objetos y asignar valores a sus propiedades.

!!! example "Asignación manual de propiedades"

    ```php
    $alumno = new Alumno();

    $alumno->nombre = 'Ana';
    $alumno->edad = 20;
    ```

Este enfoque es sencillo, pero presenta algunos inconvenientes.

Por ejemplo, ¿qué ocurre si olvidamos asignar alguno de los valores necesarios?

```php
$alumno = new Alumno();

$alumno->nombre = 'Ana';
```

Si posteriormente intentamos acceder a la propiedad `edad`, podemos encontrarnos con errores.

!!! warning "Error frecuente"

    En PHP 8.2, acceder a una propiedad tipada que no ha sido inicializada provoca un error de ejecución.

Por este motivo resulta conveniente que los objetos se creen completamente inicializados desde el primer momento.

---

## El método constructor

Un constructor es un método especial que se ejecuta automáticamente cuando se crea un objeto.

En PHP los constructores se definen mediante el método mágico `__construct()`.

!!! info "Idea clave"

    El constructor permite garantizar que un objeto dispone de toda la información necesaria desde el instante en que es creado.

---

## Definiendo un constructor

!!! example "Constructor básico"

    ```php
    class Alumno
    {
        public string $nombre;
        public int $edad;

        public function __construct(
            string $nombre,
            int $edad
        ) {
            $this->nombre = $nombre;
            $this->edad = $edad;
        }
    }
    ```

Creación del objeto:

```php
$alumno = new Alumno(
    'Ana',
    20
);
```

Ahora es imposible crear un alumno sin proporcionar los datos requeridos.

---

## Utilizando varios objetos

Cada objeto conserva su propio estado.

!!! example "Varios objetos"

    ```php
    $alumno1 = new Alumno('Ana', 20);
    $alumno2 = new Alumno('Pedro', 22);

    echo $alumno1->nombre;
    echo $alumno2->nombre;
    ```

Resultado:

```text
Ana
Pedro
```

---

## Promoción de propiedades

Desde PHP 8 es posible declarar e inicializar propiedades directamente en el constructor.

Esta característica recibe el nombre de **promoción de propiedades**.

!!! info "PHP 8.2"

    La promoción de propiedades es una de las características más utilizadas en el desarrollo moderno con PHP.

---

## Constructor con promoción de propiedades

!!! example "Sintaxis moderna"

    ```php
    class Alumno
    {
        public function __construct(
            public string $nombre,
            public int $edad
        ) {
        }
    }
    ```

La funcionalidad es exactamente la misma que en el ejemplo anterior.

Sin embargo, la cantidad de código es mucho menor.

---

## Constructores con valores por defecto

Los parámetros del constructor pueden disponer de valores por defecto.

!!! example "Valor por defecto"

    ```php
    class Alumno
    {
        public function __construct(
            public string $nombre,
            public string $curso = '2º DAW'
        ) {
        }
    }
    ```

Uso:

```php
$alumno = new Alumno('Laura');
```

En este caso, el curso tomará automáticamente el valor:

```text
2º DAW
```

---

## El método destructor

Además del constructor, PHP proporciona un método especial denominado destructor.

El destructor se ejecuta cuando el objeto deja de utilizarse y va a ser eliminado de memoria.

!!! example "Destructor"

    ```php
    class Alumno
    {
        public function __destruct()
        {
            echo 'Objeto destruido';
        }
    }
    ```

!!! note "En aplicaciones reales"

    Los destructores se utilizan con poca frecuencia en aplicaciones web modernas, aunque es importante conocer su existencia.

---

## Buenas prácticas con constructores

!!! tip "Recomendaciones"

    - Inicializa siempre los objetos mediante constructores.
    - Utiliza tipos en los parámetros.
    - Aprovecha la promoción de propiedades cuando resulte apropiado.
    - Evita crear objetos parcialmente configurados.
    - Mantén los constructores simples y fáciles de entender.

---

# Encapsulación

Hasta ahora hemos utilizado propiedades públicas para almacenar información dentro de los objetos.

!!! example "Propiedades públicas"

    ```php
    class CuentaBancaria
    {
        public float $saldo = 0;
    }
    ```

Aunque este enfoque resulta sencillo, presenta un problema importante.

Cualquier parte del programa puede modificar directamente el valor almacenado.

```php
$cuenta = new CuentaBancaria();

$cuenta->saldo = -5000;
```

Desde el punto de vista técnico el código es correcto, pero no parece razonable permitir un saldo negativo de forma arbitraria.

Necesitamos una forma de proteger la información interna de nuestros objetos.

---

## ¿Qué es la encapsulación?

La encapsulación es uno de los principios fundamentales de la programación orientada a objetos.

Consiste en ocultar los detalles internos de una clase y controlar cómo pueden consultarse o modificarse sus datos.

!!! info "Idea clave"

    La encapsulación protege la información interna de los objetos y evita modificaciones no controladas.

Gracias a este mecanismo podemos:

- Validar los datos.
- Evitar estados inválidos.
- Reducir errores.
- Hacer el código más mantenible.

---

## Propiedades privadas

Para ocultar información utilizamos el modificador `private`.

!!! example "Propiedad privada"

    ```php
    class CuentaBancaria
    {
        private float $saldo = 0;
    }
    ```

A partir de este momento la propiedad únicamente será accesible desde la propia clase.

El siguiente código generará un error:

```php
$cuenta = new CuentaBancaria();

$cuenta->saldo = 1000;
```

!!! warning "Error frecuente"

    Una propiedad privada no puede utilizarse directamente desde el exterior de la clase.

---

## Accediendo a propiedades privadas

Si una propiedad es privada, ¿cómo podemos consultar o modificar su valor?

La solución consiste en utilizar métodos específicos para acceder a ella.

Estos métodos reciben tradicionalmente los nombres de:

- Getter.
- Setter.

---

## Getters

Un getter es un método que devuelve el valor de una propiedad.

!!! example "Método getter"

    ```php
    class CuentaBancaria
    {
        private float $saldo = 0;

        public function getSaldo(): float
        {
            return $this->saldo;
        }
    }
    ```

---

## Setters

Un setter es un método que permite modificar el valor de una propiedad.

!!! example "Método setter"

    ```php
    public function setSaldo(float $saldo): void
    {
        $this->saldo = $saldo;
    }
    ```

---

## Validando información

La principal ventaja de los setters es que permiten realizar comprobaciones antes de guardar los datos.

!!! example "Validación básica"

    ```php
    public function setSaldo(float $saldo): void
    {
        if ($saldo >= 0) {
            $this->saldo = $saldo;
        }
    }
    ```

!!! tip "Buena práctica"

    Siempre que una propiedad tenga restricciones o reglas de negocio, conviene aplicar validaciones antes de modificar su valor.

---

## Constructores y encapsulación

Los constructores y la encapsulación suelen utilizarse conjuntamente.

!!! info "Relación entre ambos conceptos"

    El constructor garantiza que el objeto se crea correctamente y la encapsulación garantiza que continúa siendo válido durante toda su vida útil.

---

## Ejemplo completo

!!! example "Clase CuentaBancaria"

    ```php
    class CuentaBancaria
    {
        private float $saldo;

        public function __construct(
            float $saldoInicial
        ) {
            $this->saldo = max(0, $saldoInicial);
        }

        public function getSaldo(): float
        {
            return $this->saldo;
        }

        public function ingresar(float $cantidad): void
        {
            if ($cantidad > 0) {
                $this->saldo += $cantidad;
            }
        }

        public function retirar(float $cantidad): void
        {
            if (
                $cantidad > 0 &&
                $cantidad <= $this->saldo
            ) {
                $this->saldo -= $cantidad;
            }
        }
    }
    ```

Uso:

```php
$cuenta = new CuentaBancaria(1000);

$cuenta->ingresar(200);
$cuenta->retirar(100);

echo $cuenta->getSaldo();
```

Resultado:

```text
1100
```

---

## Ventajas de la encapsulación

- Protege los datos internos.
- Permite validar información.
- Evita estados inconsistentes.
- Facilita el mantenimiento.
- Reduce la probabilidad de errores.

!!! note "Observación"

    En aplicaciones profesionales es habitual que la mayoría de propiedades se declaren como `private`.

---

## Buenas prácticas

!!! tip "Recomendaciones"

    - Utiliza propiedades privadas por defecto.
    - Expón únicamente la funcionalidad necesaria.
    - Valida siempre la información recibida.
    - Evita setters cuando no aporten valor.
    - Mantén los constructores simples.
    - Utiliza tipos en propiedades, parámetros y retornos.

---

## Resumen

En este apartado hemos aprendido a:

- Utilizar constructores para inicializar objetos.
- Aprovechar la promoción de propiedades de PHP 8.
- Comprender el funcionamiento de los destructores.
- Aplicar el principio de encapsulación.
- Utilizar getters y setters.
- Validar información antes de almacenarla.

!!! note "Próximo paso"

    En el siguiente tema estudiaremos la herencia y la reutilización de código.

---

## Actividad propuesta

### Actividad 3. Gestión de productos

Desarrolla una clase llamada `Producto` que cumpla los siguientes requisitos:

- Debe almacenar el nombre del producto.
- Debe almacenar su precio.
- Los datos deberán inicializarse mediante un constructor.
- El precio no podrá ser negativo.
- Debe existir un método para modificar el precio.
- Debe existir un método para consultar el precio.

### Ejemplo de uso esperado

```php
$producto = new Producto(
    'Portátil',
    899.99
);

echo $producto->getPrecio();
```

!!! tip "Reflexiona"

    ¿Qué ventajas ofrece una propiedad privada frente a una propiedad pública en este caso?