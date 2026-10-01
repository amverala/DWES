# Herencia

## Reutilizando código

Uno de los principales objetivos de la programación orientada a objetos es evitar la duplicación de código.

Imagina que estamos desarrollando una aplicación de gestión académica y necesitamos representar distintos tipos de usuarios:

- Alumnos.
- Profesores.
- Administradores.

Todos ellos comparten cierta información común, como el nombre o el correo electrónico. Sin embargo, cada tipo de usuario también dispone de características propias.

!!! info "Idea clave"
    La herencia permite reutilizar código común y especializar el comportamiento de las clases derivadas.

---

## ¿Qué es la herencia?

La herencia permite crear una nueva clase a partir de otra ya existente.

- La clase original recibe el nombre de **clase padre** o **superclase**.
- La nueva clase recibe el nombre de **clase hija** o **subclase**.

La clase hija hereda las propiedades y métodos accesibles de la clase padre y puede añadir nuevas funcionalidades o modificar comportamientos existentes.

!!! tip "Relación correcta"
    Utiliza herencia cuando exista una relación del tipo «es un». Por ejemplo, un Alumno es un Usuario.

---

## La palabra reservada extends

La herencia se implementa mediante la palabra reservada `extends`.

!!! example "Primer ejemplo de herencia"

    ```php
    class Usuario
    {
        public string $nombre;
    }

    class Alumno extends Usuario
    {
    }
    ```

En este ejemplo, la clase `Alumno` hereda la propiedad `nombre` definida en `Usuario`.

---

## Accediendo a los elementos heredados

Una clase hija puede utilizar las propiedades y métodos heredados de la clase padre.

!!! example "Utilización de una propiedad heredada"

    ```php
    $alumno = new Alumno();
    $alumno->nombre = 'Ana';

    echo $alumno->nombre;
    ```

Resultado:

```text
Ana
```

---

## Añadiendo nuevos elementos

Las clases hijas pueden incorporar nuevas propiedades y métodos.

!!! example "Ampliando una clase heredada"

    ```php
    class Usuario
    {
        public string $nombre;
    }

    class Alumno extends Usuario
    {
        public string $curso;
    }
    ```

Ahora un objeto de tipo `Alumno` dispone tanto de la propiedad heredada `nombre` como de la propiedad propia `curso`.

---

## Heredando métodos

La herencia también permite reutilizar métodos.

!!! example "Métodos heredados"

    ```php
    class Usuario
    {
        public function saludar(): void
        {
            echo 'Bienvenido al sistema';
        }
    }

    class Alumno extends Usuario
    {
    }

    $alumno = new Alumno();
    $alumno->saludar();
    ```

---

## Sobrescritura de métodos

Una clase hija puede redefinir el comportamiento de un método heredado. Este proceso recibe el nombre de **sobrescritura**.

!!! example "Modificando el comportamiento heredado"

    ```php
    class Usuario
    {
        public function saludar(): void
        {
            echo 'Bienvenido';
        }
    }

    class Alumno extends Usuario
    {
        public function saludar(): void
        {
            echo 'Bienvenido al área de estudiantes';
        }
    }
    ```

!!! warning "Importante"
    La nueva definición debe respetar la firma del método heredado para evitar problemas de compatibilidad.

---

## Utilizando parent

En ocasiones resulta útil reutilizar parcialmente la implementación de la clase padre.

!!! example "Llamando a un método de la clase padre"

    ```php
    class Usuario
    {
        public function saludar(): void
        {
            echo 'Bienvenido';
        }
    }

    class Alumno extends Usuario
    {
        public function saludar(): void
        {
            parent::saludar();
            echo ' al área de estudiantes';
        }
    }
    ```

Resultado:

```text
Bienvenido al área de estudiantes
```

---

## Herencia y constructores

Si una clase hija define su propio constructor, deberá llamar explícitamente al constructor de la clase padre cuando necesite inicializar sus propiedades.

!!! example "Constructores heredados"

    ```php
    class Usuario
    {
        public function __construct(
            protected string $nombre
        ) {}
    }

    class Alumno extends Usuario
    {
        public function __construct(
            string $nombre,
            protected string $curso
        ) {
            parent::__construct($nombre);
        }
    }
    ```

---

## El modificador protected

Cuando trabajamos con herencia suele resultar más útil utilizar `protected` que `private`.

!!! example "Propiedad protegida"

    ```php
    class Usuario
    {
        protected string $nombre;
    }
    ```

Las propiedades protegidas:

- Son accesibles desde la clase donde se definen.
- Son accesibles desde las clases hijas.
- No son accesibles desde el exterior.

!!! tip "Buena práctica"
    Utiliza `private` por defecto y `protected` únicamente cuando una clase hija necesite acceder al atributo.

---

## Ejemplo completo

!!! example "Jerarquía de usuarios"

    ```php
    class Usuario
    {
        public function __construct(
            protected string $nombre
        ) {}

        public function mostrarDatos(): void
        {
            echo "Nombre: {$this->nombre}";
        }
    }

    class Profesor extends Usuario
    {
        public function __construct(
            string $nombre,
            protected string $departamento
        ) {
            parent::__construct($nombre);
        }

        public function mostrarDatos(): void
        {
            parent::mostrarDatos();
            echo "<br>Departamento: {$this->departamento}";
        }
    }

    $profesor = new Profesor(
        'María Pérez',
        'Informática'
    );

    $profesor->mostrarDatos();
    ```

Resultado:

```text
Nombre: María Pérez
Departamento: Informática
```

---

## Buenas prácticas

!!! tip "Recomendaciones"

    - Utiliza la herencia únicamente cuando exista una verdadera relación de especialización.
    - Evita jerarquías de clases demasiado profundas.
    - Reutiliza en la clase padre únicamente aquello que sea común a todas las clases hijas.
    - Utiliza `protected` cuando las clases derivadas necesiten acceder a determinados atributos.
    - Sobrescribe métodos únicamente cuando sea necesario modificar su comportamiento.

---

## Resumen

En este apartado hemos aprendido a:

- Crear clases hijas mediante `extends`.
- Reutilizar propiedades y métodos heredados.
- Sobrescribir métodos.
- Utilizar `parent`.
- Trabajar con constructores heredados.
- Utilizar el modificador `protected`.

---

## Actividad propuesta

### Actividad 4. Personal de un centro educativo

Desarrolla una jerarquía de clases formada por:

- `Persona`.
- `Alumno`.
- `Profesor`.

Requisitos:

- `Persona` deberá almacenar el nombre y el correo electrónico.
- `Alumno` deberá añadir el curso.
- `Profesor` deberá añadir el departamento.
- Todas las clases deberán disponer de un método `mostrarDatos()`.
- Las clases hijas deberán reutilizar el constructor de la clase padre mediante `parent::__construct()`.

!!! note "Reflexiona"
    Identifica qué propiedades deberían declararse como `protected` y cuáles podrían mantenerse privadas.
