# Informe

### ¿De qué trata nuestra web?

Nuestra página web esta dedicadamente a nuestro producto, ZetaVision, la página web es de tipo tienda online, ofrece un producto al usuario y el usuario inicia sesión para dar los datos de envío.

### ¿Qué funcionalidades ofrecerá a los usuarios?

Se ofrece crear una cuenta o iniciar una si ya han creado una anteriormente, con esta cuenta te dará ventajas a la hora de pedir nuestro productor como por ejemplo:

- Ofertas para productos de la tienda.
- Hacer reseñas del producto.

### ¿Qué elementos importantes hay en tu web que necesitan almacenarse?

Los elemntos que se almacenarán son:

- **Productos:** habrá tanto "varchar" como "int".
- **Pedidos:** habrá "int", "decimales", "datetime" y "varchar".
- **Usuarios:** habrá "in" y "varchar".
- **Direcciones:** habrá "INT" y "varchar".
- **Productos_Pedidos:** habrá solo "INT".

### Información que almacenan

- **Productos:** almacenará un id con el nombre de los productos junto a la descripción, precio y su categoría.
- **Pedidos:** almacenará tres id, uno de pedido, de usuario y de dirección. Junto a ellos estará la fecha prevista, la de entrega y el estado del pedido.
- **Usuarios:** almacenará un id, un nombre, apellido y su correo más la contraseña hasheada.
- **Direcciones:** almacenará los id de dirección y de usuario junto a la ciudad, a la calle, portal, planta, puerta y CP.
- **Productos_Pedidos:** almacenará los id productos_pedido, el de pedido y el de producto y luego la cantidad del producto.
 
### ¿Por qué necesitas guardarla en la base de datos?

Porque quiero automatizar la introducción de los datos para la compra y el envío de productos y la presentación de su información.

### Atributos

- **Productos:**
  - Nombre del producto: VARCHAR
  - La categoría: VARCHAR
  - La descripción: TEXT
  - ID producto: INT
  - Precio: DECIMAL
    
- **Pedidos:**
  - ID pedido: INT
  - ID usuario: INT
  - ID dirección: INT
  - Fecha entrega: DATETIME
  - Fecha prevista: DATE
  - Estado del pedido: ENUM ("En proceso", "En reparto", "Entregado")
  
- **Usuarios:**
  - ID de usuario: INT
  - Nombre: VARCHAR
  - Apellido: VARCHAR
  - Correo: VARCHAR
  - Contraseña: VARCHAR

- **Direcciones:**
   - ID de dirección: INT
   - ID de usuario: INT
   - Portal: INT
   - Puerta: INT
   - Ciudad: VARCHAR
   - Calle: VARCHAR
   - Planta: VARCHAR
   - CP: VARCHAR
     
- **Productos_Pedidos:** Aquí será solo "INT", porque son los ID y la cantidad de un producto.
  - ID productos_pedidos: INT
  - ID del pedido: INT
  - ID del producto: INT
  - Cantidad del producto: INT
    
## Relaciones entre las entidades

Para relacionar las entidades utilizamos el Modelo Entidad-Relación (MER), que es el vinculo que tienen los datos entre si, están los 1:1 que son de un dato a un dato como persona:apellido, ya que una persona no puede tener dos primeros apellidos. O de 1:N/N:1 que es de muchos a uno o uno a muchos, el ejemplo sería un usuario:pedidos, un único usuario puede tener más de un pedido. Y la ultima son los N:M de muchos a muchos, como pedidos:productos, un mismo producto puede estar en muchos pedidos diferentes. Y todo esto se conecta con las llaves en SQL.


## Simulación de Datos

Hemos rellenado la tabla usuarios con información de compañeros con un "INSERT"
```TEXT
INSERT INTO usuarios (nombre, apellido, correo, psswrd)
VALUES ("Eidan", "Jama", "eidanjama@gmail.com", "gj5h8LP*^PO"),

INSERT INTO direcciones (id_cliente, ciudad, calle, portal, planta, puerta, cp)
VALUES (1, "Cornella", "Av. Salvador Allende", 1, "Bajo", 2, 08940),

INSERT INTO productos (nombre, precio, descripcion, categoria)
VALUES ("ZVision v1", 88.67, "Las gafas inteligentes con audio, cámara y micrófono son dispositivos corporales (wearables) que integran funciones de un smartphone directamente en una montura de lentes tradicional.", "Informática"),

INSERT INTO pedidos (id_usuario, direccion, fecha_entrega, estado)
VALUES (1, 1, "", "En proceso"),

INSERT INTO productos_pedidos (id_pedid, id_produc, cantidad)
VALUES (1, 2, 1),

```

## Reflexion

Las partes mas difíciles han sido al momento de crear las llaves y entender como funcionan y como escribirlas correctamente en sql. Problemas pendientes son las contraseñas hasheadas y automatizar los ID de los productos, direcciones, usuarios, pedidos en las otras tablas sin nosotros tener que poner el valor en la consulta.
