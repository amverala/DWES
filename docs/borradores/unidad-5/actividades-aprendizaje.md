# Actividades de aprendizaje

## Introducción

A lo largo de esta unidad has aprendido a trabajar con Symfony, uno de los frameworks PHP más utilizados en el desarrollo profesional de aplicaciones web.

Has conocido su estructura, configurado proyectos, creado controladores, definido rutas, utilizado plantillas Twig y desarrollado formularios para interactuar con los usuarios.

El objetivo de las siguientes actividades es consolidar estos conocimientos mediante ejercicios prácticos progresivos que te permitan aplicar los conceptos estudiados antes de realizar la actividad evaluable.

!!! info "Recomendación"

    Realiza las actividades en el orden propuesto. Cada ejercicio reutiliza conocimientos adquiridos en los anteriores y te ayudará a construir una comprensión sólida del funcionamiento de Symfony.

---

# Actividades de repaso

## Actividad 1. Verificando el entorno Symfony

!!! example "Actividad 1"

    **Objetivo**

    Comprobar que el entorno de desarrollo está correctamente configurado.

    **Tareas**

    1. Abre una terminal.
    2. Comprueba la versión de PHP.
    3. Comprueba la versión de Composer.
    4. Comprueba la versión de Symfony CLI.

    **Comandos**

    ```bash
    php -v
    ```

    ```bash
    composer --version
    ```

    ```bash
    symfony --version
    ```

    **Solución**

    Debes obtener información de versión para las tres herramientas.

    Si alguno de los comandos no responde correctamente, será necesario revisar la instalación correspondiente.

---

## Actividad 2. Explorando un proyecto Symfony

!!! example "Actividad 2"

    **Objetivo**

    Identificar los principales directorios de una aplicación Symfony.

    **Tareas**

    Observa el proyecto generado mediante Symfony CLI y completa la siguiente tabla:

    | Elemento | Función |
    |-----------|----------|
    | src | |
    | templates | |
    | config | |
    | public | |
    | vendor | |

    **Solución**

    | Elemento | Función |
    |-----------|----------|
    | src | Código fuente de la aplicación |
    | templates | Plantillas Twig |
    | config | Configuración del framework |
    | public | Punto de entrada público |
    | vendor | Dependencias gestionadas por Composer |

---

# Actividades sobre controladores y rutas

## Actividad 3. Creación de rutas básicas

!!! example "Actividad 3"

    **Objetivo**

    Crear rutas y controladores sencillos.

    **Tareas**

    Define las siguientes rutas:

    - `/`
    - `/empresa`
    - `/contacto`

    Cada una debe mostrar un mensaje diferente.

    **Solución**

    ```php
    #[Route('/')]
    public function inicio(): Response
    {
        return new Response('Página principal');
    }

    #[Route('/empresa')]
    public function empresa(): Response
    {
        return new Response('Página de empresa');
    }

    #[Route('/contacto')]
    public function contacto(): Response
    {
        return new Response('Página de contacto');
    }
    ```

---

## Actividad 4. Utilizando parámetros

!!! example "Actividad 4"

    **Objetivo**

    Capturar datos enviados mediante la URL.

    **Tareas**

    Crea una ruta:

    ```text
    /usuario/{nombre}
    ```

    que muestre un saludo personalizado.

    **Solución**

    ```php
    #[Route('/usuario/{nombre}')]
    public function usuario(
        string $nombre
    ): Response
    {
        return new Response(
            "Hola $nombre"
        );
    }
    ```

---

## Actividad 5. Parámetros múltiples

!!! example "Actividad 5"

    **Objetivo**

    Trabajar con varios parámetros.

    **Tareas**

    Define una ruta:

    ```text
    /producto/{id}/{nombre}
    ```

    **Resultado esperado**

    ```text
    Producto 15 - teclado
    ```

    para:

    ```text
    /producto/15/teclado
    ```

    **Solución**

    ```php
    #[Route('/producto/{id}/{nombre}')]
    public function producto(
        int $id,
        string $nombre
    ): Response
    {
        return new Response(
            "Producto $id - $nombre"
        );
    }
    ```

---

# Actividades sobre Twig

## Actividad 6. Primera plantilla Twig

!!! example "Actividad 6"

    **Objetivo**

    Crear una vista mediante Twig.

    **Tareas**

    Crea el archivo:

    ```text
    templates/inicio.html.twig
    ```

    con el contenido:

    ```twig
    <h1>Bienvenido a Symfony</h1>
    ```

    Modifica el controlador para renderizar dicha plantilla.

    **Solución**

    ```php
    return $this->render(
        'inicio.html.twig'
    );
    ```

---

## Actividad 7. Envío de variables a Twig

!!! example "Actividad 7"

    **Objetivo**

    Mostrar información dinámica.

    **Tareas**

    Envía una variable llamada:

    ```php
    curso
    ```

    con el valor:

    ```text
    DWES
    ```

    y muéstrala en una plantilla.

    **Solución**

    Controlador:

    ```php
    return $this->render(
        'curso.html.twig',
        [
            'curso' => 'DWES'
        ]
    );
    ```

    Plantilla:

    ```twig
    {{ curso }}
    ```

---

## Actividad 8. Bucles en Twig

!!! example "Actividad 8"

    **Objetivo**

    Generar contenido dinámico.

    **Tareas**

    Muestra una lista de módulos utilizando un bucle `for`.

    **Solución**

    ```twig
    <ul>
    {% for modulo in modulos %}
        <li>{{ modulo }}</li>
    {% endfor %}
    </ul>
    ```

---

# Actividades sobre formularios

## Actividad 9. Creación de un formulario básico

!!! example "Actividad 9"

    **Objetivo**

    Crear un formulario Symfony.

    **Tareas**

    Añade un campo de texto denominado:

    ```text
    nombre
    ```

    y muéstralo en una plantilla.

    **Solución**

    ```php
    $form = $this->createFormBuilder()
        ->add('nombre')
        ->getForm();
    ```

    ```twig
    {{ form(formulario) }}
    ```

---

## Actividad 10. Procesando datos enviados

!!! example "Actividad 10"

    **Objetivo**

    Recuperar los datos enviados mediante un formulario.

    **Tareas**

    Utiliza:

    ```php
    handleRequest()
    ```

    para procesar la petición.

    **Solución**

    ```php
    $form->handleRequest($request);

    if (
        $form->isSubmitted() &&
        $form->isValid()
    ) {
        $datos = $form->getData();
    }
    ```

---

# Actividades de ampliación

## Actividad 11. Página de bienvenida personalizada

!!! example "Actividad 11"

    **Objetivo**

    Combinar rutas y Twig.

    **Tareas**

    Crea una ruta:

    ```text
    /bienvenida/{nombre}
    ```

    y muestra un mensaje personalizado utilizando Twig.

    **Pista**

    Utiliza un parámetro de ruta y envíalo a la plantilla mediante `render()`.

---

## Actividad 12. Menú reutilizable

!!! example "Actividad 12"

    **Objetivo**

    Utilizar la función `include()`.

    **Tareas**

    Crea una plantilla:

    ```text
    menu.html.twig
    ```

    e inclúyela en varias vistas.

    **Solución orientativa**

    ```twig
    {{ include('menu.html.twig') }}
    ```

---

# Mini proyecto integrador

## Aplicación de gestión de alumnos

!!! example "Proyecto integrador"

    **Situación**

    Una academia desea disponer de una aplicación web básica para mostrar información de sus alumnos.

    **Objetivos**

    Desarrollar una pequeña aplicación Symfony que integre todos los conocimientos estudiados en esta unidad.

    **Requisitos mínimos**

    1. Crear una página de inicio.
    2. Definir una ruta dinámica:

       ```text
       /alumno/{nombre}
       ```

    3. Mostrar la información mediante Twig.
    4. Crear una plantilla base utilizando `extends`.
    5. Añadir un menú común mediante `include`.
    6. Implementar un formulario de alta de alumno con los campos:

       - Nombre
       - Correo electrónico
       - Curso

    7. Mostrar una página de confirmación tras el envío.

---

### Estructura sugerida

```text
src/
└── Controller/
    └── AlumnoController.php

templates/
├── base.html.twig
├── menu.html.twig
├── inicio.html.twig
├── alumno.html.twig
└── formulario.html.twig
```

---

### Ampliaciones opcionales

- Añadir validación de los datos introducidos.
- Mostrar mensajes de error personalizados.
- Crear varias rutas para diferentes cursos.
- Aplicar estilos CSS mediante Bootstrap.

---

### Competencias trabajadas

Durante este proyecto pondrás en práctica:

- Creación de proyectos Symfony.
- Controladores.
- Sistema de rutas.
- Parámetros dinámicos.
- Twig.
- Herencia de plantillas.
- Inclusión de fragmentos.
- Formularios.
- Procesamiento de datos.

!!! success "Actividad completada"

    Si has conseguido desarrollar este proyecto serás capaz de construir pequeñas aplicaciones web completas utilizando Symfony y estarás preparado para afrontar la actividad evaluable de la unidad.

---

## Autoevaluación

Antes de pasar a la actividad evaluable comprueba que eres capaz de:

- Crear un proyecto Symfony.
- Configurar el entorno de desarrollo.
- Definir rutas.
- Capturar parámetros desde la URL.
- Crear controladores.
- Generar respuestas HTTP.
- Utilizar plantillas Twig.
- Crear plantillas base.
- Incluir fragmentos reutilizables.
- Crear formularios.
- Procesar datos enviados por el usuario.

Si puedes responder afirmativamente a todos estos puntos, has alcanzado los objetivos fundamentales de la Unidad 5.