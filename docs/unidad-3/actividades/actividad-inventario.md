# Actividad entregable 2 · Sistema de gestión de inventario

!!! abstract "Objetivo"

    Desarrollar una aplicación orientada a objetos capaz de gestionar un inventario de productos aplicando los conceptos estudiados durante la unidad.

!!! info "Conceptos trabajados"

    - Encapsulación.
    - Herencia.
    - Polimorfismo.
    - Clases abstractas.
    - Interfaces.
    - Namespaces.
    - Gestión de colecciones de objetos.
    - Organización de proyectos PHP.
    - Integración de PHP, HTML y CSS.

---

## Enunciado

Desarrolla un sistema que gestione un inventario de productos utilizando clases abstractas, interfaces, herencia y espacios de nombres.

---

## Interfaz Precioable

Crea una interfaz llamada:

```php
Precioable
```

dentro del namespace:

```php
Inventario\Interfaces
```

### Método

La interfaz deberá contener el siguiente método:

```php
getPrecio()
```

Este método deberá devolver el precio del producto.

---

## Clase abstracta Producto

Crea una clase abstracta llamada:

```php
Producto
```

dentro del namespace:

```php
Inventario\Modelos
```

La clase deberá implementar la interfaz:

```php
Precioable
```

### Propiedades

La clase deberá almacenar:

- nombre
- descripcion
- cantidad

### Métodos

Implementa los siguientes métodos:

- `__construct($nombre, $descripcion, $cantidad)`
- `getNombre()`
- `getDescripcion()`
- `getCantidad()`
- `setCantidad($cantidad)`

### Método abstracto

La clase deberá declarar el método:

```php
getPrecio()
```

que será implementado por las clases derivadas.

---

## Clases derivadas

### Libro

Crea una clase llamada:

```php
Libro
```

que herede de:

```php
Producto
```

Añade una propiedad para almacenar el precio del libro e implementa el método:

```php
getPrecio()
```

### Revista

Crea una clase llamada:

```php
Revista
```

que herede de:

```php
Producto
```

Añade una propiedad para almacenar el precio de la revista e implementa el método:

```php
getPrecio()
```

---

## Clase Inventario

Crea una clase llamada:

```php
Inventario
```

dentro del namespace:

```php
Inventario\Gestion
```

Esta clase será la encargada de gestionar una colección de productos.

### Propiedad

La clase deberá disponer de un array que almacene los productos del inventario.

### Métodos obligatorios

#### agregarProducto()

Añade un producto al inventario.

#### eliminarProducto()

Elimina un producto utilizando su nombre y devuelve un mensaje indicando si la operación se ha realizado correctamente.

#### listarProductos()

Muestra todos los productos almacenados en el inventario indicando:

- Nombre.
- Descripción.
- Precio.
- Cantidad.

!!! info "Importante"

    Este método deberá funcionar independientemente del tipo concreto de producto almacenado.

#### buscarProducto()

Busca un producto utilizando su nombre.

---

## Script principal (index.php)

Crea un archivo:

```text
index.php
```

que:

1. Incluya todas las clases y la interfaz utilizando los namespaces correspondientes.
2. Cree varios libros y revistas.
3. Añada los productos al inventario.
4. Muestre la lista completa de productos.
5. Busque productos por nombre.
6. Elimine productos del inventario.
7. Muestre el inventario actualizado.

---

## Ejemplo de funcionamiento

La aplicación deberá permitir:

- Registrar productos.
- Consultar el inventario.
- Buscar productos concretos.
- Eliminar productos.
- Visualizar los cambios realizados.

---

## Diseño visual

Añade código HTML y CSS para mejorar la presentación de la aplicación.

### Requisitos

- El CSS deberá encontrarse en un archivo externo.
- La información deberá mostrarse de forma clara y ordenada.
- Se valorará positivamente la presentación visual del inventario.

!!! tip "Sugerencia"

    Puedes utilizar tablas o tarjetas para mostrar los productos.

---

## Organización del proyecto

```text
Inventario/
│
├── Interfaces/
│   └── Precioable.php
│
├── Modelos/
│   ├── Producto.php
│   ├── Libro.php
│   └── Revista.php
│
├── Gestion/
│   └── Inventario.php
│
├── css/
│   └── estilos.css
│
└── index.php
```

---

## Entrega

La entrega deberá incluir:

- Todos los archivos PHP necesarios.
- Hoja de estilos CSS externa.
- Capturas de pantalla mostrando el resultado.

---

## Lista de comprobación

- [ ] Has creado la interfaz Precioable.
- [ ] Has creado la clase abstracta Producto.
- [ ] Libro hereda de Producto.
- [ ] Revista hereda de Producto.
- [ ] El inventario permite añadir productos.
- [ ] El inventario permite buscar productos.
- [ ] El inventario permite eliminar productos.
- [ ] Se utilizan correctamente los namespaces.
- [ ] El CSS se encuentra en un archivo externo.
- [ ] El proyecto funciona correctamente.

!!! warning "Importante"

    La actividad deberá desarrollarse utilizando PHP 8.2 y seguir las buenas prácticas trabajadas durante la unidad.
