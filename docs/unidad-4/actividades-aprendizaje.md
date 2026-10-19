# Actividades de aprendizaje

!!! info "📝 Actividad 1. Frameworks PHP"

    Investiga los siguientes frameworks PHP:

    - Laravel
    - Symfony
    - CodeIgniter
    - Slim

    Completa una tabla comparativa indicando sus características principales y sus casos de uso.

---

!!! question "🔍 Actividad 2. Dependencias"

    Analiza las siguientes situaciones e indica si sería recomendable utilizar una dependencia externa o desarrollar la funcionalidad desde cero:

    1. Envío de correos electrónicos.
    2. Generación de documentos PDF.
    3. Registro de eventos y errores.
    4. Generación de códigos QR.
    5. Conexión con una API de pagos.

    Justifica tus respuestas.

---

!!! tip "🌐 Actividad 3. Explorando Packagist"

    Accede a:

    ```text
    https://packagist.org
    ```

    Busca tres paquetes PHP de utilidad para aplicaciones web.

    Para cada uno de ellos indica:

    - Nombre del paquete.
    - Función principal.
    - Número aproximado de descargas.
    - Ejemplo de uso.

---

## **✅ Cuestionario de autoevaluación**

### Pregunta 1

¿Qué es un framework?

- a) Un lenguaje de programación
- b) Una herramienta que proporciona una estructura para desarrollar aplicaciones
- c) Un servidor web
- d) Una base de datos

??? success "Ver respuesta"

    ✅ Respuesta correcta: **b)** Una herramienta que proporciona una estructura para desarrollar aplicaciones.

### Pregunta 2

¿Cuál es el framework que utilizaremos en las próximas unidades?

- a) Laravel
- b) Slim
- c) Symfony
- d) CodeIgniter

??? success "Ver respuesta"

    ✅ Respuesta correcta: **c)** Symfony.

### Pregunta 3

¿Qué es una dependencia?

- a) Un archivo PHP obligatorio
- b) Un componente externo utilizado por una aplicación
- c) Un servidor de bases de datos
- d) Un framework

??? success "Ver respuesta"

    ✅ Respuesta correcta: **b)** Un componente externo utilizado por una aplicación.

### Pregunta 4

¿Qué herramienta se utiliza habitualmente para gestionar dependencias en PHP?

- a) npm
- b) Maven
- c) Composer
- d) pip

??? success "Ver respuesta"

    ✅ Respuesta correcta: **c)** Composer.

### Pregunta 5

¿Qué carpeta contiene las dependencias instaladas?

- a) libs
- b) dependencies
- c) vendor
- d) packages

??? success "Ver respuesta"

    ✅ Respuesta correcta: **c)** vendor.

---

!!! success "💻 Práctica guiada · Mi primer proyecto con Composer"

    ### Objetivo

    Crear una aplicación PHP capaz de utilizar una librería instalada mediante Composer.

    **Paso 1**

    ```bash
    mkdir practica-composer
    cd practica-composer
    composer init
    ```

    **Paso 2**

    ```bash
    composer require monolog/monolog
    ```

    **Paso 3**

    Crear el archivo `index.php` y comprobar que se genera el archivo `app.log`.

---

## **🎉 Fin de las actividades de aprendizaje**

Has completado las actividades de práctica y autoevaluación de la unidad.
