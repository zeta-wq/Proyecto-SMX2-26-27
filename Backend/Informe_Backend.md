# Informe

### ¿De qué trata nuestra web?

Nuestra página web esta dedicadamente a nuestro producto, ZetaVision, la página web es de tipo tienda online, ofrece un producto al usuario y el usuario inicia sesión para coger los datos de envío.

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

  #### Información que alamcenan

  - **Productos:** almacenará un id con el nombre de los productos junto a la descripción, precio y su categoría.
  - **Pedidos:** almacenará tres id, uno de pedido, de usuario y de dirección junto a la fecha prevista y la de entrega y el estado del pedido.
  - **Usuarios:** almacenará un id, un nombre, apellido con su correo más la contraseña hasheada.
  - **Direcciones:** almacenará los id de dirección y de usuario junto a la ciudad, a la calle, portal, planta, puerta y CP.
  - **Productos_Pedidos:** almacenará los id productos_pedido, el de pedido y el de producto y luego la cantidad del producto.
 
  #### ¿Por qué necesitas guardarla en la base de datos?

Guardar en la base de datos toda esta información es esencial para automatizar la introducción de los datos y la búsqueda de los mismos massivamente.
