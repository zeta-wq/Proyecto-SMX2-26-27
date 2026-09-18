Sí. Te lo dejo como un `README.md` limpio, profesional y **sin emojis ni elementos decorativos de IA**, listo para copiar a GitHub.

 README.md

# Sistema de Seguridad Inteligente con Raspberry Pi

 Proyecto Intermodular de 2.º curso de Sistemas Microinformáticos y Redes (SMR).

 Sistema de videovigilancia basado en una Raspberry Pi 5 capaz de detectar personas, realizar reconocimiento facial, activar una alarma y enviar avisos al propietario.

 El proyecto también contempla una plataforma web desde la que gestionar cámaras, personas autorizadas, grabaciones y planes de almacenamiento.

---

 ## Objetivos

 El sistema tendrá las siguientes funciones:

 - Captura y grabación de vídeo.
- Detección de personas mediante inteligencia artificial.
- Reconocimiento facial de personas autorizadas.
- Activación de una alarma ante personas desconocidas.
- Envío de notificaciones al propietario.
- Llamada de aviso al propietario.
- Almacenamiento local y en la nube.
- Gestión del sistema mediante una página web.
- Diferentes planes de almacenamiento mediante suscripción.

 Para las pruebas del proyecto, las llamadas se realizarán al teléfono del propietario en lugar de utilizar llamadas reales a servicios de emergencia.

---

 ## Arquitectura general

```
                         INTERNET
                             |
                             |
                        +----v----+
                        | ROUTER  |
                        | FIREWALL|
                        +----+----+
                             |
                             |
                  +----------v-----------+
                  |     RASPBERRY PI 5   |
                  |                      |
                  | Raspberry Pi OS Lite |
                  | Docker               |
                  | Scrypted             |
                  | Scrypted NVR         |
                  | Python               |
                  | MQTT                 |
                  +----------+-----------+
                             |
              +--------------+--------------+
              |              |              |
              v              v              v
           CAMARA           PIR          ALARMA
              |
              v
       +--------------+
       |   AI HAT+    |
       |    Hailo     |
       +------+-------+
              |
              v
      Detección de persona
              |
              v
      Reconocimiento facial
              |
        +-----+-----+
        |           |
        v           v
    Conocido    Desconocido
        |           |
        |           v
        |        ALARMA
        |           |
        |       GRABACIÓN
        |           |
        +-----+-----+
              |
              v
           SERVIDOR
              |
       +------+------+------+
       |      |      |      |
       v      v      v      v
      API    BD    VÍDEOS  MQTT
              |
              v
             WEB
```

---

 # Hardware

 | Componente | Función |
| --- | --- |
| Raspberry Pi 5 8 GB | Equipo principal del sistema |
| Raspberry Pi Camera Module 3 | Captura de vídeo |
| Raspberry Pi AI HAT+ 13 TOPS | Aceleración de inteligencia artificial |
| Sensor PIR | Detección de movimiento |
| Buzzer | Alarma sonora |
| SSD NVMe | Almacenamiento local |
| Caja | Protección del dispositivo |
| Fuente USB-C | Alimentación |

La Raspberry Pi 5 no se incluye en el presupuesto porque ya se dispone de ella.

---

 ## AI HAT+

 El Raspberry Pi AI HAT+ incorpora un acelerador de inteligencia artificial Hailo.

 Su función es realizar determinados cálculos de modelos de IA de forma especializada, reduciendo la carga de trabajo de la CPU de la Raspberry Pi.

```
Cámara
   |
   v
Raspberry Pi
   |
   v
AI HAT+ / Hailo
   |
   v
Modelo de IA
   |
   v
Detección
```

 Se utilizará inicialmente el modelo de **13 TOPS**, suficiente para el objetivo del proyecto.

---

 ## Sensor PIR

 El sensor PIR (Passive Infrared) detecta movimiento mediante radiación infrarroja.

 Se utilizará como primer filtro del sistema:

```
PIR
 |
 +-- No detecta movimiento -> No hacer nada
 |
 +-- Detecta movimiento -> Procesar cámara
```

 De esta forma, el sistema puede evitar realizar procesamiento de imagen innecesario cuando no existe movimiento.

---

 # Software de la Raspberry Pi

 ## Raspberry Pi OS Lite

 Se utilizará:

 **Raspberry Pi OS Lite 64-bit (Trixie)**

 La versión Lite no incluye entorno gráfico, ya que la Raspberry Pi funcionará como un dispositivo/servidor.

 La administración se realizará mediante SSH desde un ordenador.

```
PC
 |
 | SSH
 v
Raspberry Pi
```

---

 ## Docker

 Docker permitirá ejecutar los diferentes servicios de forma independiente.

```
Docker
 |
 +-- Scrypted
 |
 +-- Mosquitto
 |
 +-- Servicio Python
```

 Esto facilita la instalación, actualización y mantenimiento de cada servicio.

---

 ## Scrypted

 Scrypted será utilizado para gestionar la cámara y los dispositivos de vídeo.

 También permite integrar diferentes sistemas de cámaras y funciones de procesamiento de vídeo.

---

 ## Scrypted NVR

 Scrypted NVR se utilizará para las funciones relacionadas con la videovigilancia:

 - Grabación de vídeo.
- Detección de personas.
- Gestión de eventos.
- Reconocimiento facial.
- Notificaciones.

---

 ## Motor de detección e IA

 El motor de detección es el software encargado de analizar las imágenes de la cámara mediante modelos de inteligencia artificial.

 El flujo será:

```
Imagen de cámara
       |
       v
Motor de IA
       |
       v
Modelo de detección
       |
       v
¿Hay una persona?
       |
       v
Reconocimiento facial
```

 El procesamiento se realizará localmente siempre que sea posible.

---

 ## Python

 Se desarrollará un servicio propio en Python para controlar la lógica del sistema.

 Funciones principales:

 - Control del sensor PIR.
- Control de la alarma.
- Control de GPIO.
- Comunicación mediante MQTT.
- Comunicación con el servidor.
- Gestión de eventos.
- Automatizaciones.

---

 ## MQTT

 MQTT es un protocolo ligero de comunicación utilizado habitualmente en sistemas IoT.

 Se utilizará para enviar información entre la Raspberry Pi y el servidor.

 Ejemplos de mensajes:

```
camera/01/status
camera/01/motion
camera/01/person
camera/01/face
camera/01/alarm
```

 El broker MQTT utilizado será **Mosquitto**.

 Ejemplo:

```
Raspberry Pi
      |
      | MQTT
      v
  Mosquitto
      |
      v
   Servidor
```

---

 # Servidor y Cloud

 El servidor será responsable de gestionar los usuarios, cámaras, eventos, grabaciones y suscripciones.

 ## API

 Se utilizará:

 **FastAPI + Python**

 La API permitirá la comunicación entre la Raspberry Pi, la página web y la base de datos.

```
Raspberry Pi
      |
      v
   FastAPI
      |
      +-- PostgreSQL
      |
      +-- Storage
      |
      +-- Usuarios
      |
      +-- Eventos
```

---

 ## Base de datos

 Se utilizará:

 **PostgreSQL**

 La base de datos almacenará información como:

 - Usuarios.
- Cámaras.
- Eventos.
- Personas autorizadas.
- Grabaciones.
- Suscripciones.
- Configuración.

---

 ## Almacenamiento de vídeos

 Para el desarrollo se utilizará:

 **MinIO**

 MinIO permite implementar almacenamiento de objetos compatible con S3.

 Para una futura versión comercial se podría utilizar:

 **Amazon S3**

 Los vídeos se almacenarán inicialmente en el SSD local y posteriormente podrán sincronizarse con el almacenamiento remoto.

---

 ## Autenticación

 El sistema contará con:

 - Autenticación mediante usuario y contraseña.
- JWT para gestionar sesiones.
- Hashing seguro de contraseñas.
- HTTPS.
- Control de permisos.

---

 ## Notificaciones

 Se utilizará **Firebase Cloud Messaging (FCM)** para enviar notificaciones al teléfono del propietario.

 Ejemplo:

```
Persona desconocida detectada
        |
        v
     Servidor
        |
        v
      FCM
        |
        v
   Teléfono
```

---

 ## Llamadas

 Se utilizará **Twilio** para realizar llamadas de prueba al teléfono del propietario.

```
Persona desconocida
        |
        v
     Servidor
        |
        v
     Twilio
        |
        v
   Teléfono
```

---

 # Aplicación web

 La plataforma web permitirá gestionar el sistema desde un navegador.

 ## Tecnologías

 - React
- TypeScript
- FastAPI
- PostgreSQL
- Nginx
- HTTPS

 ## Funciones

 - Visualización de vídeo en directo.
- Historial de eventos.
- Historial de grabaciones.
- Gestión de cámaras.
- Gestión de personas autorizadas.
- Configuración de la alarma.
- Configuración de notificaciones.
- Gestión del almacenamiento.
- Gestión de la suscripción.

---

 # Planes de almacenamiento

 El proyecto contempla un modelo de suscripción.

 | Plan | Precio | Retención |
| --- | --- | --- |
| Free | 0 €/mes | 3 días |
| Basic | 2,99 €/mes | 7 días |
| Plus | 5,99 €/mes | 30 días |
| Pro | 9,99 €/mes | 90 días |

Los precios son orientativos y forman parte de la propuesta comercial del proyecto.

---

 # Funcionamiento del sistema

```
1. El sensor PIR detecta movimiento
                    |
                    v
2. Se procesa la cámara
                    |
                    v
3. La IA detecta una persona
                    |
                    v
4. Se realiza reconocimiento facial
                    |
              +-----+-----+
              |           |
              v           v
          Conocido    Desconocido
              |           |
              v           v
           Ignorar      Alarma
                          |
                    +-----+-----+
                    |           |
                    v           v
                Grabación   Notificación
                                |
                                v
                              Llamada
```

---

 # Diseño de red

 Se plantea separar los dispositivos mediante VLAN.

```
                         ROUTER
                            |
                       FIREWALL
                            |
              +-------------+-------------+
              |             |             |
              v             v             v
          VLAN 10       VLAN 20       VLAN 30
       Administración      IoT        Servidores
              |             |             |
              |             +-- Raspberry |
              |             +-- Cámaras   |
              |                           +-- API
              +-- PC                       +-- PostgreSQL
                                          +-- MQTT
                                          +-- Storage
```

 La segmentación de red permitirá limitar la comunicación entre los diferentes dispositivos y mejorar la seguridad del sistema.

---

 # Administración

 La Raspberry Pi se administrará remotamente mediante SSH.

```
PC
 |
 | SSH
 v
Raspberry Pi
 |
 +-- Docker
 +-- Scrypted
 +-- MQTT
 +-- Python
```

 No será necesario conectar un monitor, teclado o ratón permanentemente a la Raspberry Pi.

---

 # Seguridad y privacidad

 Debido al uso de videovigilancia y reconocimiento facial, se tendrán en cuenta aspectos relacionados con la seguridad y protección de datos.

 Medidas previstas:

 - Procesamiento local de IA.
- Comunicaciones mediante HTTPS.
- Autenticación segura.
- Contraseñas almacenadas mediante hashing.
- Control de acceso.
- Segmentación de red.
- Eliminación automática de grabaciones.
- Limitación del tiempo de almacenamiento.
- Minimización de los datos almacenados.

---

 # Tecnologías

 | Categoría | Tecnología |
| --- | --- |
| Hardware | Raspberry Pi 5 |
| Cámara | Camera Module 3 |
| Acelerador IA | Hailo AI HAT+ |
| Detección | Scrypted NVR |
| Sistema operativo | Raspberry Pi OS Lite 64-bit |
| Contenedores | Docker |
| Programación | Python |
| IoT | MQTT / Mosquitto |
| Backend | FastAPI |
| Base de datos | PostgreSQL |
| Almacenamiento | MinIO / Amazon S3 |
| Frontend | React + TypeScript |
| Proxy | Nginx |
| Notificaciones | Firebase Cloud Messaging |
| Llamadas | Twilio |
| Administración | SSH |

---

 # Estado del proyecto

 - [ ] Preparar Raspberry Pi
- [ ] Instalar Raspberry Pi OS Lite
- [ ] Configurar SSH
- [ ] Instalar Docker
- [ ] Configurar cámara
- [ ] Instalar Scrypted
- [ ] Configurar Scrypted NVR
- [ ] Instalar AI HAT+
- [ ] Configurar detección de personas
- [ ] Configurar reconocimiento facial
- [ ] Configurar sensor PIR
- [ ] Configurar alarma
- [ ] Configurar MQTT
- [ ] Desarrollar API
- [ ] Crear base de datos
- [ ] Crear almacenamiento
- [ ] Desarrollar página web
- [ ] Implementar notificaciones
- [ ] Implementar llamadas
- [ ] Implementar planes de almacenamiento
- [ ] Realizar pruebas
- [ ] Documentar el proyecto

---

 # Proyecto Intermodular

 **Ciclo:** Sistemas Microinformáticos y Redes (SMR)

 **Curso:** 2.º SMR

 **Curso académico:** 2026/2027

 **Autor:** \[Tu nombre\]

 **Centro:** \[Nombre del centro\]
