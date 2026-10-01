# Actividad entregable 1 · Sistema de gestión de publicaciones

!!! abstract "Objetivo"

    Desarrollar una aplicación orientada a objetos que permita gestionar distintos tipos de publicaciones aplicando los conceptos estudiados durante la unidad.

!!! info "Conceptos trabajados"

    - Clases y objetos.
    - Constructores.
    - Herencia.
    - Sobrescritura de métodos.
    - Namespaces.
    - Organización de proyectos PHP.
    - Integración de PHP, HTML y CSS.

---

## Enunciado

Crea un proyecto en PHP que contenga los siguientes elementos.

## Crear un espacio de nombres

Crea un espacio de nombres llamado:

```php
Biblioteca
```

para organizar todas las clases que vas a crear.

## Clase base Publicacion

Dentro del espacio de nombres `Biblioteca`, define una clase base llamada `Publicacion`.

### Propiedades

- titulo (cadena de texto)
- autor (cadena de texto)
- anio (entero)

### Métodos

- `__construct($titulo, $autor, $anio)` para inicializar las propiedades.
- `mostrarInfo()` para devolver un string con la información básica de la publicación.

## Clase derivada Libro

Crea una clase llamada `Libro` dentro del namespace `Biblioteca` que extienda la clase `Publicacion`.

- Añade la propiedad `numeroPaginas` (entero).
- Sobrescribe el método `mostrarInfo()` para incluir el número de páginas.

## Clase derivada Revista

Crea una clase llamada `Revista` dentro del namespace `Biblioteca` que extienda la clase `Publicacion`.

- Añade la propiedad `numeroEdicion` (entero).
- Sobrescribe el método `mostrarInfo()` para incluir el número de edición.

## Script principal (index.php)

1. Incluye las clases utilizando el namespace `Biblioteca`.
2. Crea un objeto `Libro` con título, autor, año y número de páginas.
3. Crea un objeto `Revista` con título, autor, año y número de edición.
4. Muestra la información de ambos mediante `mostrarInfo()`.

## Ejemplo de ejecución

Cuando ejecutes el script principal, deberá mostrarse la información de un libro y una revista, incluyendo los detalles específicos de cada uno.

## Diseño visual

Añade código HTML y CSS para mejorar la presentación de la aplicación.

- El CSS deberá encontrarse en un archivo externo.
- La información deberá mostrarse de forma clara y ordenada.

## Organización del proyecto

```text
Biblioteca/
├── Publicacion.php
├── Libro.php
├── Revista.php
├── css/
│   └── estilos.css
└── index.php
```

## Entrega

- Todos los archivos PHP necesarios.
- Hoja de estilos CSS externa.
- Capturas de pantalla mostrando el resultado.

!!! warning "Importante"

    La actividad deberá desarrollarse utilizando PHP 8.2.
