# Introducción al lenguaje PHP

## ¿Qué es PHP?

PHP es un lenguaje de programación diseñado para desarrollar aplicaciones web que se ejecutan en el servidor.

A diferencia de HTML, que únicamente permite definir la estructura y el contenido de una página web, PHP permite crear páginas dinámicas capaces de procesar información, realizar cálculos, acceder a bases de datos o generar contenido personalizado para cada usuario.

Actualmente, PHP es uno de los lenguajes más utilizados en el desarrollo de aplicaciones web y constituye una de las tecnologías fundamentales del desarrollo web en entorno servidor.

---

## ¿Por qué utilizar PHP?

Hasta ahora hemos trabajado con páginas HTML estáticas. En ellas, el contenido mostrado al usuario es siempre el mismo y no depende de ninguna interacción ni de los datos almacenados en el sistema.

Sin embargo, la mayoría de las aplicaciones web actuales necesitan:

- Procesar información introducida por los usuarios.
- Validar datos antes de almacenarlos.
- Gestionar usuarios y contraseñas.
- Consultar y modificar información en bases de datos.
- Generar contenido personalizado.
- Ofrecer respuestas diferentes según el contexto o las acciones realizadas.

Estas funcionalidades requieren la utilización de un lenguaje de programación ejecutado en el servidor.

---

## PHP como lenguaje del lado del servidor

Como vimos en la unidad anterior, las aplicaciones web modernas siguen un modelo cliente-servidor.

Cuando un usuario solicita una página web, el navegador envía una petición al servidor. Si la aplicación contiene código PHP, este se ejecuta en el servidor antes de enviar la respuesta al cliente.

El navegador nunca recibe el código PHP. Únicamente recibe el resultado generado tras la ejecución del programa.

```text
Cliente (navegador)
        │
        ▼
 Petición HTTP
        │
        ▼
Servidor web + PHP
        │
        ▼
Respuesta HTML
        │
        ▼
Cliente (navegador)
```

Gracias a este proceso es posible generar páginas dinámicas adaptadas a cada usuario y a cada situación.

---

## Características principales de PHP

PHP presenta una serie de características que explican su amplia adopción en el desarrollo web:

- Es un lenguaje gratuito y de código abierto.
- Puede ejecutarse en diferentes sistemas operativos.
- Se integra fácilmente con HTML.
- Permite trabajar con múltiples sistemas gestores de bases de datos.
- Posee una amplia comunidad de desarrolladores y abundante documentación.
- Está especialmente orientado al desarrollo de aplicaciones web.

Estas características lo convierten en una herramienta adecuada para iniciarse en la programación en entorno servidor.

---

## Aplicaciones y entornos que utilizan PHP

PHP se emplea en numerosos sitios web, plataformas educativas, gestores de contenidos y aplicaciones empresariales.

Su amplia implantación en el desarrollo web ha contribuido a que se mantenga como una de las tecnologías más utilizadas para la creación de aplicaciones web dinámicas.

A lo largo de este módulo utilizaremos PHP para desarrollar nuestras propias aplicaciones y comprender los fundamentos de la programación en entorno servidor.

---

## Lo que aprenderás en esta unidad

Durante esta unidad aprenderás a:

- Crear programas sencillos utilizando PHP.
- Declarar y utilizar variables.
- Trabajar con distintos tipos de datos.
- Aplicar declaraciones de tipo en parámetros y valores de retorno.
- Utilizar estructuras de control para tomar decisiones.
- Recorrer colecciones de datos mediante la estructura `foreach`.
- Crear funciones reutilizables para organizar el código.

Los conocimientos adquiridos en esta unidad servirán de base para el resto de contenidos del módulo.

---

## Actividad de reflexión

Antes de continuar, piensa en tres aplicaciones web que utilices habitualmente.

Para cada una de ellas intenta responder a las siguientes preguntas:

1. ¿Necesita procesar información proporcionada por el usuario?
2. ¿Crees que utiliza programación en el servidor? ¿Por qué?
3. ¿Qué ventajas aporta utilizar un lenguaje como PHP en ese contexto?

Reflexiona sobre tus respuestas y compáralas con los conceptos presentados en esta introducción.

---

## Antes de continuar

Asegúrate de que el entorno de desarrollo configurado en la unidad anterior funciona correctamente.

En los siguientes apartados comenzarás a crear tus primeros programas en PHP y descubrirás los elementos fundamentales del lenguaje.

¡Es hora de empezar a programar!
