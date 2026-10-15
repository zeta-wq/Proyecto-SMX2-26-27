# Estructura Web

### ESTRUCTURA JERÁRQUICA

```text
Homepage
 ├── Software
 ├── Tienda
 │   ├── Inicio de sesión
 |   |   ├── Registro
 │   ├── Producto
 │   └── Software
 ├── Documentación
 └── Acerca de nosotros
```
<hr>

### Inventario

```text
| Página        |    Tipo   | Contenido Principal    | Prioridad |
|---------------|-----------|------------------------|-----------|
| Homepage      | Estática  | Presentación proucto   | Alta      |
| Tienda        | Categoría | Lista de Productos     | Alta      |
| Software      | Subpágina | Descarga de Programa   | Alta      |
| Productos     | Subpágina | Compra Productos       | Media     |
| Documentación | Subdominio| Guia de Usuario        | Media     |
| Acerca de     | Estática  | Información Extra      | Baja      |
```
<hr>

### Diagrama de navegación

<img src="../imagenes/diagrama_de_navegación_zetavision.png" alt="Página Principal" width="600" style="border: 2px solid #ff0000; border-radius: 8px; padding: 4px;" />
