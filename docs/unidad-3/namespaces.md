# Namespaces

## El problema de los nombres duplicados

A medida que una aplicación crece, aumenta también el número de clases que forman parte del proyecto.

Imagina que estamos desarrollando una aplicación de gestión académica y una biblioteca externa incluye también una clase llamada `Usuario`.

```text
Proyecto propio
│
└── Usuario

Biblioteca externa
│
└── Usuario
```

!!! warning "Problema"

    Dos clases con el mismo nombre no pueden coexistir en el mismo espacio global.

Para resolver este problema utilizamos los espacios de nombres o **Namespaces**.

---

## ¿Qué es un namespace?

!!! info "Idea clave"

    Los namespaces permiten organizar el código y evitar conflictos entre clases con el mismo nombre.

!!! info "PHP 8.2"

    Los namespaces forman parte del lenguaje desde PHP 5.3 y continúan siendo el mecanismo estándar para organizar aplicaciones en PHP 8.2.

## Declarando un namespace

!!! example "Namespace sencillo"

    ```php
    namespace App;

    class Usuario
    {
    }
    ```

El nombre completo de la clase será:

```text
App\Usuario
```

---

## Namespaces jerárquicos

!!! example "Jerarquía de namespaces"

    ```php
    namespace App\Modelo;

    class Alumno
    {
    }
    ```

Nombre completo:

```text
App\Modelo\Alumno
```

---

## Utilizando una clase con namespace

!!! example "Nombre completamente cualificado"

    ```php
    $alumno = new App\Modelo\Alumno();
    ```

Para simplificar el código utilizamos `use`.

## Importación mediante use

!!! example "Importando clases"

    ```php
    use App\Modelo\Alumno;

    $alumno = new Alumno();
    ```

## Importando varias clases

!!! example "Múltiples importaciones"

    ```php
    use App\Modelo\Alumno;
    use App\Modelo\Profesor;
    use App\Modelo\Modulo;
    ```

## Alias de namespaces

!!! example "Uso de alias"

    ```php
    use App\Modelo\Usuario;
    use Biblioteca\Auth\Usuario as UsuarioAuth;
    ```

## Namespace actual

!!! example "Constante mágica"

    ```php
    echo __NAMESPACE__;
    ```

---

## Organización habitual de un proyecto

!!! note "Motivación"

    En proyectos con decenas o cientos de clases, los namespaces son imprescindibles para mantener una estructura ordenada.

!!! example "Organización típica"

    ```text
    App
    │
    ├── Modelo
    ├── Controlador
    ├── Servicio
    └── Utilidades
    ```

## Relación entre namespaces y archivos

!!! example "Estructura de carpetas"

    ```text
    src/
    └── Modelo/
        └── Alumno.php
    ```

    ```php
    namespace App\Modelo;
    ```

!!! tip "Buena práctica"

    Mantén sincronizados los namespaces y la estructura de carpetas.

---

## Ejemplo completo

!!! example "Clase Alumno"

    ```php
    namespace App\Modelo;

    class Alumno
    {
        public function saludar(): void
        {
            echo 'Hola';
        }
    }
    ```

!!! example "Uso desde index.php"

    ```php
    use App\Modelo\Alumno;

    $alumno = new Alumno();
    $alumno->saludar();
    ```

---

## Errores frecuentes

!!! warning "Olvidar use"

    PHP no podrá localizar correctamente una clase si no se importa el namespace adecuado.

!!! warning "Estructura incoherente"

    Mantén alineados namespaces y carpetas para facilitar el mantenimiento.

---

## Buenas prácticas

!!! tip "Recomendaciones"

    - Utiliza namespaces para organizar el código.
    - Mantén nombres descriptivos.
    - Usa `use` para simplificar referencias.
    - Utiliza alias cuando existan conflictos.

---

## Resumen

En este apartado hemos aprendido a:

- Declarar espacios de nombres.
- Importar clases mediante `use`.
- Utilizar alias.
- Organizar proyectos PHP de forma profesional.

!!! info "Conexión con la unidad"

    Gracias a los namespaces podemos organizar todas las clases desarrolladas durante la unidad y evitar conflictos de nombres.

---

## Actividades propuestas

### Actividad 14. Organización de modelos

Crea las clases `Alumno` y `Profesor` en el namespace `App\Modelo`.

### Actividad 15. Sistema académico modular

Diseña los namespaces:

```text
App
├── Modelo
├── Servicio
└── Utilidades
```

### Actividad 16. Resolviendo conflictos

Crea dos clases llamadas `Usuario` en namespaces diferentes y utiliza alias para trabajar con ambas.
