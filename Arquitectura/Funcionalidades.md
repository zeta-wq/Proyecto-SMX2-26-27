# Tabla de funcionalidades — ZetaVision ZVision V1

| ID | Prioridad | Objetivo | Funcionalidad | Disparador | Fecha | Estado |
|----|-----------|----------|---------------|------------|-------|--------|
| 1 | Alta | Control por voz manos libres | Captura de voz con micrófono integrado y activación por palabra clave. | Decir la palabra de activación o pulsar el botón de la patilla. | 01/04/2027 | Activo |
| 2 | Alta | Respuestas por audio sin pantalla | Respuesta por audio a través del altavoz de las gafas. | Fin del procesamiento de la consulta por la IA. | 15/04/2027 | Pendiente |
| 3 | Alta | Una IA integrada | Asistente de IA que interpreta la consulta y genera la respuesta (modelo qwen3.5:8b). | Consulta de voz ya transcrita. | 31/04/2027 | Activo |
| 4 | Alta | Privacidad total de las conversaciones | Procesamiento local de la IA, sin enviar audio a servicios externos. | Cualquier consulta al asistente. | 15/03/2027 | Pendiente |
| 5 | Media | Visión integrada para que la IA vea lo que ves | Cámara frontal con captura de foto y vídeo. | Comando de voz «mira» o botón de captura. | 28/03/2027 | Pendiente |
| 6 | Media | Grabación transparente para el entorno | Indicador LED junto a la cámara que se enciende al grabar. | Inicio de una captura de foto o vídeo. | 28/02/2027 | Pendiente |
| 7 | Media | Información básica a la vista | Pantalla HUD sobre la lente con estado (escuchando, grabando, respuesta breve). | Cambio de estado del sistema. | 31/03/2027 | Pendiente |
| 8 | Media | Autonomía para una jornada completa | Gestión de energía y medición real de la autonomía. | Pruebas de batería con el prototipo montado. | 15/01/2027 | Pendiente |
| 9 | Media | Diseño cómodo y ligero | Diseño de montura con módulo electrónico compacto en la patilla (referencia 21 mm). | Revisión del diseño 3D y prueba del prototipo. | 15/12/2026 | Activo |
| 10 | Baja | Presentar el producto en la web | Web de presentación con modelo 3D y animación por scroll. | Visita a la web y desplazamiento de la página. | 30/11/2026 | Activo |
| 11 | Baja | Personalización del color en la compra | Tienda con tres acabados (Negro azabache, Azul Zeta, Gris hielo); de momento es solo una demostración. | Clic en «Comprar» en la tienda. | 15/05/2027 | Pendiente |
| 12 | Baja | Cuentas de usuario propias | Acceso de usuario con login real y servidor. | Envío del formulario de «Acceder». | 31/05/2027 | Pendiente |
| 13 | Baja | Documentación técnica accesible | Documentación técnica del proyecto en la sección Docs. | Clic en «Docs» en el menú. | 30/05/2027 | Activo |

# Tabla de funcionalidades — Página Web ZetaVision

| ID | Prioridad | Objetivo | Funcionalidad | Disparador | Fecha | Estado |
|----|-----------|----------|---------------|------------|-------|--------|
| 1 | Alta | Producto visible en 3D desde el primer segundo | Modelo 3D de las gafas (three.js) en el hero de la página de inicio. | Carga de la página `#inicio`. | 06/11/2026 | Activo |
| 2 | Alta | Gafas visibles desde todos los ángulos | Animación del modelo 3D ligada al scroll, con poses clave por sección y suavizado. | Desplazamiento (scroll) del usuario. | 06/11/2026 | Activo |
| 3 | Alta | Introducción en vídeo de impacto | Vídeo de 15 s controlado por el scroll (scroll-scrub) que da paso al modelo 3D. | Scroll en la sección de introducción. | 06/11/2026 | Activo |
| 4 | Alta | Características explicadas parte a parte | Sección Características con cinco botones (Micrófono, Audio, Medidas, IA, Autonomía) que giran el modelo hacia cada parte. | Clic en uno de los cinco botones. | 06/11/2026 | Activo |
| 5 | Media | Mostrar el interior de las gafas | Vista despiezada (Anatomía) con cinco piezas que se separan según el scroll. | Scroll en la sección Anatomía. | 06/11/2026 | Activo |
| 6 | Media | Piezas identificadas sobre el modelo | Puntos de interés (hotspots) que se muestran solo si la pieza mira a la cámara. | Giro del modelo hacia la pieza. | 06/11/2026 | Activo |
| 7 | Media | Navegación fluida sin recargas | Navegación por vistas (Inicio, Docs, Tienda, Acceder) con enrutado por hash y cortinilla de transición. | Clic en el menú o cambio del hash de la URL. | 06/11/2026 | Activo |
| 8 | Media | Dar a conocer el proyecto y su equipo | Secciones Qué hacemos, Sobre nosotros, Proceso y estadísticas de producto. | Scroll en la página de inicio. | 06/11/2026 | Activo |
| 9 | Media | Documentación técnica accesible | Vista Docs con pestañas y resaltado de la sección activa. | Clic en «Docs». | 30/05/2027 | Activo |
| 10 | Media | Web adaptada al móvil | Diseño responsive con ajustes propios para pantallas pequeñas. | Acceso desde un dispositivo móvil. | 31/01/2027 | Pendiente |
| 11 | Media | Personalizar el color antes de comprar | Tienda con modelo 3D arrastrable y tres acabados (Negro azabache, Azul Zeta, Gris hielo). | Arrastrar el modelo o elegir un acabado. | 06/11/2026 | Activo |
| 12 | Baja | Compra online de las gafas | Compra real con carrito y pasarela de pago (hoy solo hay una demostración y un aviso de prototipo). | Clic en «Comprar». | 15/05/2027 | Pendiente |
| 13 | Baja | Cuentas de usuario propias | Login y registro con servidor y base de datos (hoy es una demostración sin backend). | Envío del formulario de «Acceder». | 31/05/2027 | Pendiente |
| 14 | Baja | Confirmación visual de las acciones | Avisos emergentes (toasts) en tienda y login. | Acción del usuario en tienda o login. | 06/11/2026 | Activo |
| 15 | Baja | Primera impresión cuidada | Preloader con contador y logotipo Z animado. | Carga inicial de la página. | 06/11/2026 | Activo |
| 16 | Baja | Mostrar el producto real | Sustituir las gafas procedurales por el modelo 3D real (.glb) y regenerar el vídeo. | Entrega del modelo hecho en Blender. | 28/02/2027 | Pendiente |
