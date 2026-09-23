
# Las Smart Glasses Z / ZetaVision / Zeta&Glass

Las Smart Glasses Prototipo son un dispositivo wearable de asistencia inteligente diseñado para integrar captura multimedia, interacción por voz y procesamiento de IA, reconocimiento del entorno y body tracking; todo integrado en un factor de forma ergonómico y minimalista

## Briefing

La idea principal es poder conectar las gafas con conexión directa al servidor para enviar tanto video como audio, el video y el audio se procesa con IA en el servidor.

Con IA se reconoce el entorno y en el servidor se guardan eventos ya pueden ser un vehículos pasando, animales... y se te notifica por vía auditiva.

Para uso en entorno virtual, hand tracking para utilizar el ratón del pc con tu mano a distancia.

Poder tener enlazadas las gafas a un chatbot mediante un audífono y el micrófono para hablar con la IA.

## Arquitectura del software

Las Inteligencias artificiales que utilizaremos en este proyecto son:

- Ollama (QWEN3.5:8b)
- Scrypted (NVR)

Estas IAs estarán implementadas en el servidor principal en dockers para evitar conflictos y gastar menos recursos.

Para la comunicación entre las gafas y el servidor principal se utilizara una aplicación que establezca una conexión remota segura a partir de un hotspot del telefóno.

Por parte del ordenador se utilizara un programa que conecte el microcontrolador con el PC para poder controlar el puntero del ratón.

Para el hand tracking se utilizara un script implementado dentro del ESP32 que estará conectado al programa anteriormente mencionado.



## Conlusiones


## Bibliografia

 - [Awesome Readme Templates](https://awesomeopensource.com/project/elangosundar/awesome-README-templates)
 - [Awesome README](https://github.com/matiassingers/awesome-readme)
 - [How to write a Good readme](https://bulldogjob.com/news/449-how-to-write-a-good-readme-for-your-github-project)

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

