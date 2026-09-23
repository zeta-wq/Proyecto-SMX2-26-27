
# ZetaVision

Las Smart Glasses Prototipo son un dispositivo wearable de asistencia inteligente diseñado para integrar captura multimedia, interacción por voz y procesamiento de IA, reconocimiento del entorno y body tracking; todo integrado en un factor de forma ergonómico y minimalista

## Briefing

La idea principal es poder conectar las gafas con conexión directa al servidor para enviar tanto video como audio, y procesarlo con IA en el servidor.

Para uso en entorno virtual, hand tracking para utilizar el ratón del pc con tu mano a distancia.
### Ideas secundarias

A partir de la IA almacenada en el servidor porder reconocer el entorno y guardar eventos...

Poder tener enlazadas las gafas a un chatbot mediante un audífono y el micrófono para hablar con la IA.

## Arquitectura del software

Las Inteligencias artificiales que utilizaremos en este proyecto son:

- Ollama (QWEN3.5:8b)
- Scrypted (NVR)

Estas IAs estarán implementadas en el servidor principal en dockers para evitar conflictos y gastar menos recursos.

Para la comunicación entre las gafas y el servidor principal se utilizara una aplicación que establezca una conexión remota segura a partir de un hotspot del telefóno.

Por parte del ordenador se utilizara un programa que conecte el microcontrolador con el PC para poder controlar el puntero del ratón.

Para el hand tracking se utilizara un script implementado dentro del ESP32 que estará conectado al programa anteriormente mencionado.

## Tecnologías a utilizar

A nivel hardware utilizaremos el microcontrolador **Seeed estudio XIAO ESP32 S3 Sense**, es una plaquita muy pequeña ideal para poner en la patilla.

**Porqué este?** Este controlador XIAO ESP32 viene incorporado con una cámara, con un micrófono digital, una antena WIFI y Bluetooth, todo esto en una placa de **21x17,8x15mm** con placa para una futura posible expansión.


## Conlusiones


## Bibliografia

- **Getting Started del microcontrolador**: https://wiki.seeedstudio.com/es/xiao_esp32s3_getting_started/

## Guía de Usuario



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

