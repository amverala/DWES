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

```bash
composer --version
```

```bash
php --version
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

```bash
composer install
```

---

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
