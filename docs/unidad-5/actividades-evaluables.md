# Actividades evaluables

## Presentación

Con estas actividades pondrás en práctica todos los conocimientos adquiridos a lo largo de la unidad.

Las tareas propuestas permiten trabajar de forma integrada los contenidos relacionados con:

- Instalación y configuración de Symfony.
- Controladores.
- Sistema de rutas.
- Parámetros dinámicos.
- Plantillas Twig.
- Herencia de plantillas.
- Formularios.
- Sesiones.
- Mensajes Flash.

Cada tarea aborda una parte diferente del framework y permite consolidar las competencias necesarias para el desarrollo de aplicaciones web modernas.

!!! info "Importante"

    Lee detenidamente cada tarea antes de comenzar su desarrollo. Algunas tareas reutilizan conocimientos adquiridos en actividades anteriores.

---
<hr style="border: 4px solid #19d2cfff;">

# Tarea 1. Instalación y puesta en marcha de Symfony

## Objetivos

Con esta actividad demostrarás que eres capaz de:

- Instalar proyectos Symfony mediante Composer.
- Utilizar Symfony CLI.
- Ejecutar el servidor de desarrollo integrado.
- Verificar el correcto funcionamiento de Symfony desde el navegador.
- Reconocer la estructura básica de un proyecto Symfony.

---

## Enunciado

Crea un vídeo donde se visualicen claramente las siguientes tareas realizadas en tu equipo:

1. Instalación de Symfony utilizando Composer.
2. Instalación de Symfony CLI.
3. Ejecución del servidor local de Symfony.
4. Comprobación desde el navegador del correcto funcionamiento de Symfony y de la versión instalada.
5. Visualización de la estructura de directorios generada por Symfony.

---

## Requisitos técnicos

Durante la grabación deberá aparecer:

- La terminal utilizada.
- Los comandos ejecutados.
- Los resultados obtenidos.
- El navegador mostrando la aplicación Symfony en funcionamiento.

Los pasos deberán realizarse en el orden indicado.

---

## Formato de entrega

- Un único vídeo en formato MP4.
- Resolución mínima recomendada: 720p.
- Explicación con tu propia voz de los pasos ejecutados.
- La grabación debe permitir identificar claramente cada una de las tareas solicitadas.

---

!!! tip "Consejo"

    Antes de grabar el vídeo realiza una prueba completa del proceso para asegurarte de que todas las herramientas funcionan correctamente.

---
<hr style="border: 4px solid #19d2cfff;">

# Tarea 2. Desarrollo de un controlador de gestión de tareas

## Objetivos

Con esta actividad demostrarás que eres capaz de:

- Crear controladores Symfony.
- Definir rutas con parámetros.
- Utilizar arrays para almacenar información.
- Procesar datos recibidos mediante la URL.
- Generar respuestas dinámicas.
- Aplicar estructuras de control en PHP.

---

## Enunciado

Crea un controlador denominado:

```text
TareaController
```

El controlador recibirá un nombre como parámetro mediante la URL y deberá realizar las siguientes acciones:

1. Verificar si el nombre recibido pertenece a una lista de usuarios autorizados.
2. Si el usuario está autorizado, mostrar la lista de tareas asignadas a dicho usuario.
3. Si el usuario no está autorizado, mostrar un mensaje de acceso denegado.

No es necesario utilizar plantillas Twig.

La respuesta puede generarse directamente desde el controlador mediante un objeto `Response`.

---

## Usuarios autorizados

La aplicación deberá incluir, al menos:

```text
Pedro
Laura
Sofía
```

---

## Ruta

La información deberá recibirse mediante una ruta similar a:

```text
/tareas/{nombre}
```

---

## Entrega

Se deberá entregar exclusivamente el archivo:

```text
TareaController.php
```

---

!!! warning "Importante"

    No está permitido utilizar plantillas Twig ni bases de datos. La información deberá gestionarse mediante arrays definidos dentro del controlador.

---
<hr style="border: 4px solid #19d2cfff;">

# Tarea 3. Visualización de tareas mediante Twig

## Objetivos

Con esta actividad demostrarás que eres capaz de:

- Utilizar Twig para generar vistas dinámicas.
- Separar la lógica de negocio de la presentación.
- Enviar información desde un controlador a una plantilla.
- Trabajar con variables y estructuras de datos en Twig.

---

## Enunciado

Partiendo de la tarea anterior:

- Modifica el controlador `TareaController`.
- Mantén la misma funcionalidad.
- Utiliza una plantilla Twig para mostrar la información.

El controlador deberá:

1. Recibir el nombre de usuario mediante un parámetro de ruta.
2. Verificar si el usuario pertenece a la lista de autorizados.
3. Obtener las tareas correspondientes.
4. Enviar la información a una plantilla Twig.

---

## Plantilla Twig

La plantilla deberá mostrar:

- El nombre del usuario.
- La lista de tareas asignadas.
- O el mensaje de acceso denegado cuando corresponda.

---

## Archivos a entregar

Deberás entregar:

```text
TareaController.php
```

```text
tareas.html.twig
```

Opcionalmente:

```text
estilos.css
```

---

!!! tip "Consejo"

    Aprovecha Twig para separar completamente la lógica de negocio de la presentación de los datos.

---

<hr style="border: 4px solid #19d2cfff;">
# Tarea 4. Formularios y sesiones en Symfony

## Objetivos

Con esta actividad demostrarás que eres capaz de:

- Crear formularios utilizando FormBuilder.
- Utilizar clases de formulario externas al controlador.
- Validar información.
- Gestionar sesiones.
- Utilizar mensajes Flash.
- Trabajar con redirecciones.

---

## Enunciado

Desarrolla una aplicación Symfony que permita a un usuario iniciar sesión mediante un nombre de usuario y mantener dicha información almacenada en una sesión.

---

## Requisitos funcionales

### 1. Formulario de inicio de sesión

Crear un formulario utilizando FormBuilder definido en una clase independiente del controlador.

El formulario deberá contener:

- Nombre de usuario.
- Botón de envío.

---

### 2. Validación del formulario

El nombre de usuario será obligatorio.

No podrá enviarse vacío.

---

### 3. Almacenamiento en sesión

Una vez validado el formulario:

- El nombre del usuario se almacenará en la sesión.
- Permanecerá disponible durante la navegación.

---

### 4. Mensajes Flash

La aplicación deberá mostrar mensajes Flash para:

- Inicio de sesión correcto.
- Error de validación.
- Cierre de sesión.

---

### 5. Página de bienvenida

La aplicación dispondrá de una página que salude al usuario almacenado en sesión.

Si no existe sesión activa deberá redirigir automáticamente a la página de inicio.

---

### 6. Cierre de sesión

La aplicación deberá incluir un mecanismo para cerrar sesión.

La acción deberá:

- Eliminar el usuario de la sesión.
- Mostrar un mensaje Flash.
- Redirigir al formulario de acceso.

---

## Entrega

Se deberá entregar:

- Carpeta completa del proyecto Symfony.
- Vídeo explicativo.

---

## Vídeo obligatorio

El vídeo deberá incluir:

- Presentación general de la aplicación.
- Explicación del controlador.
- Explicación del formulario.
- Explicación de las plantillas.
- Gestión de sesiones.
- Mensajes Flash.
- Demostración completa del funcionamiento.

---

<hr style="border: 4px solid #19d2cfff;">
# Tarea 5. Herencia de plantillas con Twig

## Objetivos

Con esta actividad demostrarás que eres capaz de:

- Utilizar herencia de plantillas Twig.
- Crear una plantilla base reutilizable.
- Implementar formularios mediante clases Type.
- Aplicar estilos CSS.
- Organizar correctamente una aplicación Symfony.

---

## Enunciado

Desarrolla una aplicación web Symfony que implemente herencia de plantillas utilizando Twig.

La aplicación deberá disponer de:

- Página de inicio.
- Página de contacto.
- Plantilla base.
- Formulario de contacto.
- Hoja de estilos CSS.

---

## Plantilla base

Crear:

```text
base.html.twig
```

La plantilla deberá incluir:

### Cabecera

- Título de la aplicación.
- Menú de navegación.

### Menú

- Enlace a la página principal.
- Enlace a la página de contacto.

### Cuerpo

Definir un bloque:

```twig
{% block body %}
```

### Pie de página

Mostrar un mensaje de copyright.

---

## Página de inicio

Crear:

```text
inicio.html.twig
```

La plantilla deberá:

- Extender la plantilla base.
- Mostrar un mensaje de bienvenida.
- Mostrar una breve descripción de la aplicación.

---

## Página de contacto

Crear:

```text
contacto.html.twig
```

La plantilla deberá:

- Extender la plantilla base.
- Mostrar un formulario de contacto.

---

## Formulario

El formulario deberá implementarse mediante una clase Type independiente.

Campos mínimos:

- Nombre.
- Correo electrónico.
- Mensaje.

---

## Controlador

Crear:

```text
DefaultController
```

Definir las rutas:

```text
/
```

```text
/contacto
```

---

## CSS

Crear:

```text
public/css/styles.css
```

Definir estilos para:

- Cabecera.
- Menú.
- Cuerpo.
- Formularios.
- Botones.
- Pie de página.

La plantilla base deberá cargar la hoja de estilos mediante:

```twig
{{ asset('css/styles.css') }}
```

---

## Servidor

Configura y ejecuta el servidor de desarrollo Symfony.

Comprueba el correcto funcionamiento de:

```text
/
```

y

```text
/contacto
```

---

## Entrega

Se deberá entregar:

- Carpeta completa del proyecto Symfony.
- Vídeo explicativo.

---

## Contenido obligatorio del vídeo

### Explicación funcional

Descripción general de la aplicación.

### Explicación técnica

Se deberán comentar:

- Controladores.
- Formularios.
- Plantillas Twig.
- CSS.

### Demostración práctica

Mostrar:

- La página principal.
- La navegación.
- El formulario.
- La aplicación de estilos.

---

!!! tip "Consejo"

    Construye primero la plantilla base y verifica que funciona correctamente antes de desarrollar las páginas que la extienden.

---


!!! warning "Importante"

    Comprueba que todos los proyectos funcionan correctamente antes de realizar la entrega.

!!! success "Fin de la unidad"

    Has completado la Unidad 5 dedicada al desarrollo de aplicaciones con Symfony. A lo largo de la unidad has trabajado con controladores, rutas, Twig, formularios, sesiones y herencia de plantillas, adquiriendo las bases necesarias para desarrollar aplicaciones web modernas con este framework.