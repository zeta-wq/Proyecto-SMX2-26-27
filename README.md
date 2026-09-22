
# Las Smart Glasses Z

Las Smart Glasses Prototipo son un dispositivo wearable de asistencia inteligente diseñado para integrar captura multimedia, interacción por voz y procesamiento de IA en un factor de forma ergonómico y minimalista.

# La Smart Camera

La smart camera es un prototipo avanzado de cámara de seguridad potenciada con IA, con reconocimiento facial y alarma automatizada y configurable.

## Roadmap

**Fase 1:** Firmware y Captura en el ESP32
Configurar el entorno con Arduino IDE o PlatformIO optimizado para la placa Seeed Studio XIAO ESP32-S3 Sense.

Programar la captura de fotogramas con la cámara OV2640 y la toma de muestras de audio mediante el micrófono integrado.

Integrar un pequeño pulsador físico en la patilla para alternar los estados de grabación, pausa y captura de fotos.

**Fase 2:** Servidor, Backend y Redes
Levantar el servidor local en Python utilizando FastAPI para gestionar las rutas de recepción de datos multimedia.

Implementar la estrategia de red (ya seja mediante un punto de acceso móvil o un túnel como Ngrok) para asegurar la conectividad fuera de casa.

Diseñar la estructura de almacenamiento local en el servidor para organizar automáticamente las imágenes y audios entrantes.

**Fase 3:** Inteligencia Artificial y App Móvil 
Integrar el motor de transcripción (Whisper) y el modelo de lenguaje en el backend para procesar las peticiones de voz de forma fluida.

Desarrollar una aplicación básica en Flutter para visualizar de manera gráfica la galería de fotos y el historial del asistente.

Realizar el ensamblaje físico final de los componentes electrónicos en la montura y ejecutar pruebas de estrés completas.


## Bibliografia

 - [Awesome Readme Templates](https://awesomeopensource.com/project/elangosundar/awesome-README-templates)
 - [Awesome README](https://github.com/matiassingers/awesome-readme)
 - [How to write a Good readme](https://bulldogjob.com/news/449-how-to-write-a-good-readme-for-your-github-project)


## Badges

[![Hardware](https://img.shields.io/badge/Hardware-ESP32--S3-blue?style=for-the-badge&logo=espressif)](https://www.seeedstudio.com)
[![Camera](https://img.shields.io/badge/Sensor-OV2640_Camera-orange?style=for-the-badge)](https://www.seeedstudio.com)

[![C++](https://img.shields.io/badge/Firmware-C++-00599C?style=for-the-badge&logo=c%2B%2B&logoColor=white)](https://isocpp.org/)
[![Python](https://img.shields.io/badge/Backend-Python-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://www.python.org/)
[![FastAPI](https://img.shields.io/badge/API-FastAPI-009688?style=for-the-badge&logo=fastapi&logoColor=white)](https://fastapi.tiangolo.com/)

[![WiFi](https://img.shields.io/badge/Network-Wi--Fi_AP-success?style=for-the-badge&logo=wifi)](https://en.wikipedia.org/wiki/Wi-Fi)
[![REST API](https://img.shields.io/badge/Protocol-HTTP%2FREST-informational?style=for-the-badge)](https://restfulapi.net/)

[![AI](https://img.shields.io/badge/AI-Whisper_%26_LLM-purple?style=for-the-badge&logo=openai)](https://openai.com/)
[![App](https://img.shields.io/badge/App-Flutter-02569B?style=for-the-badge&logo=flutter&logoColor=white)](https://flutter.dev)

[![Status](https://img.shields.io/badge/Status-Prototype_In_Progress-yellow?style=for-the-badge)](https://github.com)
[![License](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)](https://opensource.org/licenses/MIT)

