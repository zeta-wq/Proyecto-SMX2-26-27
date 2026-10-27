# ZetaVision (ZVision V1) — Proceso de Diseño UI/UX y Sistema de Interfaz

Bienvenido/a al repositorio oficial de diseño UI/UX para el proyecto **ZetaVision**. En este documento detallamos las decisiones de diseño, la arquitectura de la interfaz y la metodología aplicada para construir la experiencia web de presentación, venta y documentación técnica de nuestras gafas inteligentes de asistencia **ZVision V1**.

---

## 1. Principios Fundamentales del Diseño Visual

En el diseño de ZetaVision buscamos transmitir sofisticación tecnológica, elegancia y funcionalidad clara desde el primer segundo.

### 1.1. Jerarquía Visual
Hemos diseñado las vistas guiando de manera intencionada la atención del usuario:
* **Landing Page & Tienda:** La mirada del usuario entra directamente a través del *Hero Section*, donde colocamos el render 3D de las gafas *ZVision V1* sobre un pedestal de tono neutro. El titular principal (`PRESENTAMOS ZVISION V1`) utiliza un tamaño de fuente predominante para asentar la propuesta de valor inmediatamente.
* **Sección de Documentación:** Implementamos una jerarquía tipográfica estricta con titulares numerados (`01 PRIMEROS PASOS`, `02 CÓMO UTILIZAR LAS ZVISION V1`) que dividen el bloque denso de texto en pasos secuenciales legibles.

### 1.2. Equilibrio y Proporción
Buscamos un equilibrio visual limpio para no recargar la interfaz:
* **Disposición Asimétrica Controlada:** En el bloque de características de la landing page, ubicamos la botonera de especificaciones (*Micrófono, Audio, Medidas, IA, Autonomía*) alineada en la columna izquierda, la cual se compensa visualmente con el contenedor de la imagen del producto a la derecha.

### 1.3. Contraste
* Utilizamos un contraste de alto nivel entre el texto oscuro y los fondos grisáceos/blancos.
* Para los elementos de llamada a la acción (*CTA*) primarios como `COMPRAR`, `ACCEDER` o las etiquetas seleccionadas, elegimos un azul marino profundo sobre fondos claros, asegurando que el elemento interactivo destaque sobre el resto de la interfaz.

### 1.4. Consistencia
* **Navegación Unificada:** La barra de navegación superior (*Header*) y el pie de página (*Footer*) mantienen la misma posición, padding y componentes en todas las rutas del sitio (`Home`, `Login`, `Registro`, `Tienda` y `Docs`).
* **Estilo de Componentes:** Todos los botones de la plataforma comparten el mismo radio de borde, peso tipográfico y comportamiento de respuesta.

---

## 2. Estructura y Layout

### 2.1. Sistemas de Rejilla (*Grid System*)
* Empleamos un sistema de rejilla fluido de **12 columnas** para la maquetación en pantallas de escritorio.
* En secciones concretas como el inicio de sesión y la ficha del producto, recurrimos a tarjetas (*Cards*) centradas construidas sobre una estructura de 2 columnas (`Flexbox` / `CSS Grid`).

### 2.2. Patrones de Layout
* **Patrón en Z:** Aplicado en la cabecera principal de la Landing Page. El usuario escanea de izquierda a derecha el logo (`ETAVISION / ZETAVISION`) hacia los enlaces de navegación (`Software`, `Producto`, `Acerca de`, `Tienda`), para luego bajar en diagonal al contenido central y las llamadas a la acción.
* **Layout de Lectura en F:** Implementado en la página de **Documentación**, facilitando el escaneo de títulos a la izquierda y el consumo del contenido descriptivo en la columna derecha.

### 2.3. Zonas de la Interfaz
1. **Header (Navegación Global):** Marca principal e itinerario general.
2. **Main Content (Zona Hero / Ficha / Docs):** Espacio dedicado a la interacción directa o lectura del usuario.
3. **Sidebar / Menú de Navegación Secundaria:** Índice lateral presente en la sección de soporte/docs (`El proyecto`, `Primeros pasos`, `Uso diario`, `Cuidados`, `Preguntas frecuentes`).
4. **Footer (Pie de Página):** Marco legal, enlaces de interés y derechos reservados.

---

## 3. Color y Tipografía

### 3.1. Sistema de Color
Nuestra paleta cromática se compone de tonos sobrios para proyectar una marca *tech-premium*:
* **Azul Marino Corporativo (`#1B3B6F` / `#1E3A8A`):** Nuestro color de acento y marca. Se aplica a los botones primarios (`COMPRAR`, `ACCEDER`) y los elementos activos del menú.
* **Grises Neutros (`#E5E7EB` / `#D1D5DB`):** Utilizados en fondos de sección, tarjetas de contenido y contenedores de imágenes para suavizar la vista.
* **Negro / Gris Oscuro (`#111827`):** Color principal para títulos y bloques de texto largo, garantizando un índice de legibilidad óptimo.

### 3.2. Sistema Tipográfico
* **Tipografía de Pantalla / Títulos (*Serif* / *Didone*):** Elegida específicamente para los títulos de impacto (`PRESENTAMOS ZVISION V1`, `ZETAVISION`). Aporta elegancia, personalidad de marca y un carácter editorial distintivo.
* **Tipografía de Cuerpo (*Sans-Serif* / *Humanista*):** Aplicada en los párrafos, formularios e instrucciones de la documentación. Permite una lectura fluida sin fatiga en pantallas de cualquier tamaño.

---

## 4. Componentes de Interfaz

### 4.1. Navegación
* **Header Principal:** Accesos directos y limpios sin distracciones visuales.
* **Paginación / Carrusel:** Implementamos controles vectoriales de flecha (`<-` `->`) en la galería de producto para permitir al usuario explorar distintos ángulos del producto.
* **Breadcrumbs (Migas de pan):** Utilizadas en la sección de documentación (`Home / ZETAVISION/DOCS`) para ubicar al usuario en el mapa del sitio.

### 4.2. Formularios
* **Campos de Entrada (Inputs):** Estilizados en forma de píldora (*Pill-shape*) con fondo gris claro, bordes suaves y texto de indicación (*placeholder*).
* **Campos de Registro:** Incluyen desglose especial para prefijos internacionales (`+000`) e inputs específicos para contraseña y teléfono.
* **Social Login (OAuth):** Botones integrados para inicio de sesión rápido con *Google* y *Apple*, acompañados de sus logotipos corporativos oficiales.

### 4.3. Botones y CTA
* **Botones Primarios:** Fondo azul marino sólido con texto en mayúsculas en blanco (`ACCEDER`, `COMPRAR`).
* **Botones Secundarios y Selectores:** Rectángulos de borde limpio para alternar entre las especificaciones (*Micrófono, Audio, Medidas, IA, Autonomía*).

---

## 5. Elementos Visuales

### 5.1. Iconografía
* Iconografía vectorial funcional: Flechas de desplazamiento en la ficha de producto, botón de cierre (`X`) en modales de autenticación e iconos oficiales para proveedores OAuth.

### 5.2. Espacio en Blanco (*Negative Space*)
* Diseñamos márgenes generosos alrededor de los bloques explicativos en la landing y la documentación. El espacio en blanco actúa como separador visual, reduciendo el ruido visual y canalizando la atención hacia los puntos clave.

---

## 6. Estados y Retroalimentación

### 6.1. Estados de Interacción
* **Default:** Apariencia reposada de los botones e inputs.
* **Hover:** Incremento en la saturación del color azul en botones y oscurecimiento progresivo de enlaces al pasar el cursor.
* **Focus:** Marco distintivo en los campos de formulario cuando el usuario está escribiendo datos.

### 6.2. Retroalimentación del Sistema
* Respuestas visuales claras como mensajes de ayuda (`Has olvidado la contraseña?`), avisos legales y confirmaciones de navegación activa dentro de las Preguntas Frecuentes.

---

## 7. Diseño Responsive

### 7.1. Puntos de Ruptura (*Breakpoints*)
* **Desktop (>1024px):** Vista multi-columna completa con menús laterales visibles y disposiciones horizontales.
* **Tablet (768px - 1023px):** Reorganización de cajas en dos columnas y adaptación del menú lateral de *Docs* a la parte superior.
* **Mobile (<767px):** Colapso de la navegación en un menú simplificado y apilamiento vertical (1 columna) de los campos de formulario y secciones de la landing.

### 7.2. Adaptación de Componentes
Las imágenes del producto y las tarjetas de la documentación utilizan contenedores flexibles (`Flexbox` y porcentajes) para escalar suavemente según la resolución de pantalla.

---

## 8. Accesibilidad Visual

### 8.1. Contraste de Color
* Cumplimos con los lineamientos **WCAG 2.1 AA**, garantizando un ratio de contraste adecuado entre los textos gris oscuro/negro sobre fondos neutros claros, así como en los textos blancos sobre los botones azules.

### 8.2. Tamaños Mínimos
* **Áreas de Clic:** Los botones de interacción y redes sociales poseen una altura adaptada a un mínimo de `44px` para asegurar la facilidad de toque en dispositivos móviles.
* **Texto:** La tipografía base no baja de los `14px` en notas secundarias y `16px` para el cuerpo principal.

---

## 9. Proceso de Diseño

El proyecto fue abordado mediante una metodología iterativa dividida en tres etapas clave:

```
+-------------------+      +-------------------+      +-------------------+
| FASE 1:           | ---> | FASE 2:           | ---> | FASE 3:           |
| PLANIFICACIÓN     |      | DISEÑO            |      | TESTEO            |
| (Reqs & Wireframes)|      | (UI & Design Sys) |      | (A11y & Usabilidad)|
+-------------------+      +-------------------+      +-------------------+
```

### FASE 1: PLANIFICACIÓN
* Levantamiento de requisitos para el producto *ZVision V1* (gafas de asistencia inteligente con IA y captura multimedia).
* Definición del mapa del sitio y estructuración de la navegación (Landing -> Tienda / Login -> Docs).

### FASE 2: DISEÑO
* Definición del sistema de diseño (paleta cromática, tipografías *Serif* / *Sans-Serif*, componentes reutilizables).
* Creación de los mockups finales en Figma abarcando los diferentes flujos (compra, registro, documentación de producto).

### FASE 3: TESTEO
* Validación de contrastes de color, jerarquía visual de componentes y coherencia estética general en todo el prototipo.
```
eof
```

¿Qué te parece la estructura? Si necesitas agregar o ajustar algún detalle sobre los componentes antes de presentar la entrega del martes, avísame.
