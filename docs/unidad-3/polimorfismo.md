# Polimorfismo

## ¿Qué es el polimorfismo?

Tras estudiar la herencia, hemos visto que varias clases pueden compartir una misma estructura y reutilizar código común.

!!! info "Idea clave"

    El polimorfismo permite utilizar objetos de distintas clases a través de una referencia común, ejecutando en cada caso la implementación correspondiente.

Gracias al polimorfismo podemos escribir código más flexible, reutilizable y fácil de mantener.

---

## Polimorfismo y herencia

Para que exista polimorfismo normalmente necesitamos una relación de herencia.

```text
Animal
│
├── Perro
├── Gato
└── Pajaro
```

## Sobrescritura de métodos

!!! example "Jerarquía de animales"

    ```php
    class Animal
    {
        public function emitirSonido(): void
        {
            echo 'Sonido genérico';
        }
    }

    class Perro extends Animal
    {
        public function emitirSonido(): void
        {
            echo 'Guau';
        }
    }

    class Gato extends Animal
    {
        public function emitirSonido(): void
        {
            echo 'Miau';
        }
    }
    ```

## Utilizando una referencia común

!!! example "Colección de animales"

    ```php
    $animales = [
        new Perro(),
        new Gato()
    ];

    foreach ($animales as $animal) {
        $animal->emitirSonido();
    }
    ```

Resultado:

```text
Guau
Miau
```

!!! info "¿Qué está ocurriendo?"

    PHP ejecuta automáticamente la implementación correspondiente al tipo real del objeto.

---

## Sustitución de objetos

!!! example "Sustitución"

    ```php
    $animal = new Perro();
    $animal->emitirSonido();

    $animal = new Gato();
    $animal->emitirSonido();
    ```

---

## Aplicación en una plataforma educativa

!!! example "Usuarios del sistema"

    ```php
    class Usuario
    {
        public function presentarse(): void
        {
            echo 'Soy un usuario';
        }
    }

    class Alumno extends Usuario
    {
        public function presentarse(): void
        {
            echo 'Soy un alumno';
        }
    }

    class Profesor extends Usuario
    {
        public function presentarse(): void
        {
            echo 'Soy un profesor';
        }
    }
    ```

---

## Casos prácticos de polimorfismo

### Sistema de notificaciones

!!! example "Notificaciones"

    ```php
    class Notificacion
    {
        public function enviar(): void
        {
            echo 'Enviando notificación';
        }
    }

    class Email extends Notificacion
    {
        public function enviar(): void
        {
            echo 'Enviando correo electrónico';
        }
    }

    class SMS extends Notificacion
    {
        public function enviar(): void
        {
            echo 'Enviando SMS';
        }
    }
    ```

### Sistema de pagos

!!! example "Métodos de pago"

    ```php
    class MetodoPago
    {
        public function pagar(float $importe): void
        {
            echo "Pago realizado";
        }
    }

    class Tarjeta extends MetodoPago
    {
        public function pagar(float $importe): void
        {
            echo "Pago con tarjeta: $importe €";
        }
    }

    class Paypal extends MetodoPago
    {
        public function pagar(float $importe): void
        {
            echo "Pago con PayPal: $importe €";
        }
    }
    ```

---

## Eliminando estructuras condicionales

!!! warning "Código difícil de mantener"

    ```php
    if ($tipo === 'perro') {
        echo 'Guau';
    } elseif ($tipo === 'gato') {
        echo 'Miau';
    }
    ```

!!! tip "Buena práctica"

    Cuando aparezcan muchos `if` o `switch` basados en tipos de objetos, el polimorfismo suele ofrecer una solución más flexible.

---

## Errores frecuentes

!!! warning "Confundir herencia con polimorfismo"

    La herencia permite reutilizar código. El polimorfismo permite utilizar distintos objetos mediante una referencia común.

!!! warning "Sobrescribir métodos incorrectamente"

    Al sobrescribir un método se debe respetar su firma para mantener la compatibilidad.

---

## Un ejemplo completo

!!! example "Sistema de vehículos"

    ```php
    class Vehiculo
    {
        public function arrancar(): void
        {
            echo 'Arrancando vehículo';
        }
    }

    class Coche extends Vehiculo
    {
        public function arrancar(): void
        {
            echo 'Arrancando coche';
        }
    }

    class Moto extends Vehiculo
    {
        public function arrancar(): void
        {
            echo 'Arrancando moto';
        }
    }

    $vehiculos = [new Coche(), new Moto()];

    foreach ($vehiculos as $vehiculo) {
        $vehiculo->arrancar();
    }
    ```

---

## Mini proyecto guiado

### Gestión de empleados

```text
Empleado
│
├── Administrativo
├── Profesor
└── Director
```

!!! note "Objetivo"

    El código que recorre la colección no debe preocuparse por el tipo concreto de empleado.

---

## Actividades propuestas

### Actividad 5. Figuras geométricas

Desarrolla la jerarquía:

```text
Figura
│
├── Circulo
├── Rectangulo
└── Triangulo
```

Todas las clases deberán implementar `calcularArea()`.

### Actividad 6. Sistema de transporte

```text
Transporte
│
├── Coche
├── Bicicleta
└── Autobus
```

Implementa el método `desplazarse()` en todas las clases.

### Actividad 7. Instrumentos musicales

```text
Instrumento
│
├── Piano
├── Guitarra
└── Trompeta
```

Implementa el método `tocar()`.

### Actividad 8. Sistema de mensajería

```text
Mensaje
│
├── CorreoElectronico
├── SMS
└── MensajePush
```

Implementa el método `enviar()` sin utilizar estructuras `if` ni `switch`.

---

## Resumen

!!! info "Lo más importante"

    El polimorfismo permite escribir código que trabaja con una interfaz común mientras cada objeto ejecuta su propio comportamiento.

!!! note "Próximo paso"

    En el siguiente apartado estudiaremos las clases abstractas y las interfaces.
