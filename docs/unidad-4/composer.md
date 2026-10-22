# Composer

## ¿Qué es Composer?

Composer es el gestor de dependencias estándar de PHP.

Su función principal es instalar, actualizar y gestionar las librerías que necesita un proyecto. Gracias a Composer podemos reutilizar código desarrollado por otros programadores sin tener que descargar y configurar manualmente cada componente.

!!! info "Definición"
    Composer es una herramienta que permite gestionar las dependencias de un proyecto PHP de forma automática.

Actualmente prácticamente todos los frameworks PHP modernos utilizan Composer, incluyendo Symfony, Laravel, CodeIgniter y Slim.

---

## ¿Por qué utilizar Composer?

Sin Composer tendríamos que:

- Buscar manualmente las librerías.
- Descargarlas desde Internet.
- Copiarlas a nuestro proyecto.
- Resolver conflictos de versiones.
- Actualizar los paquetes manualmente.

Con Composer todo este proceso se realiza mediante comandos sencillos.

!!! tip "Ventaja principal"
    Composer automatiza la instalación y actualización de librerías.

---

## Instalación de Composer


### Instalar Composer en Ubuntu

Actualizar los repositorios:

```bash
sudo apt update
```

Instalar Composer:

```bash
sudo apt install composer
```

### Comprobar la instalación

Verificar que PHP está instalado:

```bash
php --version
```

Verificar que Composer se ha instalado correctamente:

```bash
composer --version
```

---

## Creación de un proyecto Composer

```bash
composer init
```

Se generará el archivo:

```text
composer.json
```

---

## Primer ejemplo práctico

```bash
mkdir proyecto-composer
cd proyecto-composer
composer init
```

---

## Buscar paquetes

```text
https://packagist.org
```

Ejemplos:

- Monolog
- PHPMailer
- Dompdf
- Guzzle

---

## Instalar una dependencia

```bash
composer require monolog/monolog
```

---

## ¿Qué archivos se crean?

```text
proyecto-composer/
│
├── composer.json
├── composer.lock
└── vendor/
```

=== "composer.json"

    Contiene la configuración principal del proyecto.

    - Información del proyecto.
    - Dependencias requeridas.
    - Configuración de autoload.

=== "composer.lock"

    Almacena las versiones exactas de todas las dependencias instaladas.

    Gracias a este archivo todos los desarrolladores trabajan con las mismas versiones.

=== "vendor"

    Contiene todas las librerías instaladas por Composer.

    También incluye:

    ```text
    vendor/autoload.php
    ```

    Esta carpeta se genera automáticamente y no debe modificarse manualmente.

!!! note "Importante"
    Los archivos `composer.json` y `composer.lock` suelen incluirse en Git. La carpeta `vendor` normalmente se regenera mediante Composer.

---

### Como ejemplo de uso de Composer, vamos a instalar **Monolog**.

### ¿Para qué sirve Monolog?

Monolog es una biblioteca de PHP que permite registrar eventos, advertencias y errores de una aplicación en archivos u otros sistemas de almacenamiento.

Se utiliza para:

- Registrar errores que ocurren durante la ejecución de la aplicación.
- Guardar advertencias y mensajes informativos.
- Facilitar la depuración y el mantenimiento del código.
- Llevar un historial de eventos importantes.
- Monitorizar aplicaciones en entornos de producción.

Por ejemplo, en lugar de mostrar un error por pantalla:

```php
echo "Error al conectar con la base de datos";
```

podemos registrarlo en un archivo de log:

```php
$log->error('Error al conectar con la base de datos');
```

De esta forma, el error queda almacenado y puede revisarse posteriormente sin afectar a los usuarios de la aplicación.

Monolog es una de las bibliotecas de logging más utilizadas en PHP y está integrada por defecto en Symfony.
## Instalando Monolog paso a paso

```bash
composer require monolog/monolog
```

```php
<?php

require 'vendor/autoload.php';

use Monolog\Logger;
use Monolog\Handler\StreamHandler;

$log = new Logger('app');
$log->pushHandler(new StreamHandler('app.log'));

$log->warning('Mensaje de prueba');
$log->error('Error de ejemplo');
```

```bash
php index.php
```

### Explicación del código

```php
require 'vendor/autoload.php';
```

Carga automáticamente las clases instaladas mediante Composer. Gracias a este archivo no es necesario incluir manualmente los ficheros de Monolog.

```php
use Monolog\Logger;
use Monolog\Handler\StreamHandler;
```

Importa las clases que vamos a utilizar:

- `Logger`: permite crear y gestionar registros de eventos (logs).
- `StreamHandler`: indica dónde se almacenarán esos registros.

```php
$log = new Logger('app');
```

Crea un objeto logger llamado `app`. Este nombre identificará el origen de los mensajes registrados.

```php
$log->pushHandler(new StreamHandler('app.log'));
```

Añade un manejador (*handler*) que guardará los mensajes en el archivo `app.log`.

```php
$log->warning('Mensaje de prueba');
```

Registra un mensaje de nivel **WARNING** (advertencia). Se utiliza para indicar situaciones que no son errores graves, pero que requieren atención.

```php
$log->error('Error de ejemplo');
```

Registra un mensaje de nivel **ERROR**. Se utiliza para indicar errores que afectan al funcionamiento de la aplicación.

Finalmente, al ejecutar:

```bash
php index.php
```

Monolog crea (o actualiza) el archivo:

```text
app.log
```
y almacena en él los mensajes generados por la aplicación.
---

## Eliminar una dependencia

```bash
composer remove monolog/monolog
```

---

## Actualizar dependencias

```bash
composer update
```

---

## Instalar dependencias de un proyecto existente

Si descargamos o clonamos un proyecto que ya dispone de un archivo `composer.json`, podemos instalar todas sus dependencias mediante:

```bash
composer install
```

Este comando lee la configuración del proyecto y descarga automáticamente las bibliotecas necesarias para que la aplicación funcione correctamente.

Además, crea la carpeta:

```text
vendor/
```

que contiene las dependencias instaladas, y genera los archivos necesarios para que puedan utilizarse desde el código PHP.

Este es uno de los comandos más utilizados en Composer, ya que permite preparar un proyecto existente para su ejecución sin tener que instalar manualmente cada dependencia.

## Comandos más utilizados

| Comando | Descripción |
|----------|-------------|
| `composer --version` | Mostrar versión |
| `composer init` | Crear proyecto |
| `composer require paquete` | Instalar dependencia |
| `composer remove paquete` | Eliminar dependencia |
| `composer update` | Actualizar dependencias |
| `composer install` | Instalar dependencias |

---

## Buenas prácticas

!!! tip "Recomendaciones"

    - No modifiques la carpeta `vendor`.
    - Utiliza Composer para instalar librerías.
    - Mantén actualizado `composer.lock`.

---

## Resumen

- Composer es el gestor de dependencias estándar de PHP.
- Permite instalar y actualizar librerías automáticamente.
- Utiliza `composer.json`, `composer.lock` y `vendor`.

!!! success "Has completado este apartado"
    Ya sabes utilizar los comandos básicos de Composer.
