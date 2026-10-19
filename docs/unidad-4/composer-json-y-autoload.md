# Composer.json y autoload

## Introducción

En el apartado anterior hemos aprendido a utilizar Composer para instalar dependencias en nuestros proyectos PHP.

Sin embargo, Composer hace mucho más que descargar librerías. También se encarga de gestionar la configuración del proyecto y de automatizar la carga de clases mediante el sistema de **autoload**.

En este apartado estudiaremos:

- El archivo `composer.json`.
- El archivo `composer.lock`.
- El sistema de carga automática de clases.
- La relación entre Composer y los espacios de nombres (namespaces).

---

## El archivo composer.json

Cuando ejecutamos:

```bash
composer init
```

Composer genera un archivo denominado:

```text
composer.json
```

Este archivo contiene la información principal del proyecto.

Ejemplo:

```json
{
    "name": "dwes/proyecto-demo",
    "description": "Proyecto de ejemplo",
    "require": {
        "monolog/monolog": "^3.0"
    }
}
```

!!! info "Idea clave"
    Composer utiliza el archivo `composer.json` para conocer qué dependencias necesita instalar y cómo debe configurarse el proyecto.

---

## Estructura básica de composer.json

=== "name"

    Identifica de forma única el proyecto.

=== "description"

    Describe brevemente el proyecto.

=== "require"

    Contiene las dependencias necesarias.

=== "autoload"

    Permite configurar la carga automática de clases.

---

## Instalación de dependencias

Cuando ejecutamos:

```bash
composer require monolog/monolog
```

Composer modifica automáticamente el archivo `composer.json`.

!!! note "Observa"
    Normalmente no es necesario editar el apartado `require` manualmente.

---

## ¿Qué es composer.lock?

Además de `composer.json`, Composer genera otro archivo:

```text
composer.lock
```

Este archivo almacena las versiones exactas de las dependencias instaladas.

!!! tip "Buenas prácticas"
    En proyectos colaborativos se recomienda incluir siempre el archivo `composer.lock` en el repositorio Git.

---

## Composer y el sistema autoload

Antes de Composer era habitual cargar clases manualmente:

```php
require_once 'Usuario.php';
require_once 'Producto.php';
require_once 'Pedido.php';
```

Composer resuelve este problema mediante el sistema **autoload**.

---

## El archivo vendor/autoload.php

Cuando instalamos dependencias aparece automáticamente:

```text
vendor/autoload.php
```

Su función es localizar y cargar automáticamente las clases necesarias.

```php
require 'vendor/autoload.php';
```

---

## ¿Cómo funciona el autoload?

```mermaid
flowchart LR
A[Aplicación PHP] --> B[vendor/autoload.php]
B --> C[Composer]
C --> D[Localiza la clase]
D --> E[Carga automáticamente el archivo]
```

---

## Composer y los namespaces

Composer utiliza los espacios de nombres estudiados en la unidad anterior para localizar automáticamente las clases.

Ejemplo:

```php
namespace App\Modelo;

class Usuario
{
}
```

Configuración:

```json
{
    "autoload": {
        "psr-4": {
            "App\\": "src/"
        }
    }
}
```

---

## Generar el autoload

```bash
composer dump-autoload
```

!!! warning "Importante"
    Si añades nuevas clases o modificas la configuración de namespaces, puede ser necesario ejecutar nuevamente este comando.

---

## Ejemplo completo

### Clase Usuario

```php
<?php

namespace App;

class Usuario
{
    public function saludar()
    {
        return "Hola";
    }
}
```

### Utilización

```php
<?php

require 'vendor/autoload.php';

$usuario = new App\Usuario();

echo $usuario->saludar();
```

Resultado:

```text
Hola
```

---

## Resumen

- `composer.json` contiene la configuración del proyecto.
- `require` almacena las dependencias necesarias.
- `composer.lock` guarda las versiones exactas instaladas.
- `vendor/autoload.php` permite cargar clases automáticamente.
- Composer utiliza namespaces para localizar las clases.
- `composer dump-autoload` regenera la configuración de autoload.

!!! success "Has completado este apartado"
    Ya conoces los elementos fundamentales que utilizan los proyectos PHP modernos para gestionar dependencias y cargar clases automáticamente.
