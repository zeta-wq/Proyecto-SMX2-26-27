# Servicios
### 1. Servidor
Dado que las gafas no pueden procesar la IA por sí solas, se necesita potencia en la nube para ejecutar el backend, la transcripción de voz y los modelos de lenguaje.
Se instalará Python con un framework ligero como FastAPI o Flask para crear una pequeña API que reciba las fotos y los audios de tus gafas.

-**Se necesita un servidor con Linux (Ubuntu Server)** que tenga al menos 2 o 4 GB de RAM para empezar. Si vas a correr modelos de IA pesados de forma local en el servidor (como Ollama/Llama), se necesitará un VPS con GPU, aunque para prototipos iniciales es mejor usar APIs de pago por uso (como OpenAI Whisper + GPT-4o-mini) para ahorrar costes de servidor gráfico.

-**Gestor de Contenedores (Docker)**: Es imprescindible. Te permitirá empaquetar tu servidor (el backend en Python, la base de datos, etc.) para que corra igual tanto en tu ordenador de pruebas como en la nube sin sorpresas.

### 2. Base de datos
Se necesitará alamcenar dos tipos de información: datos estructurados (perfiles de usuarios, metadatos de fotos, marcas de tiempo, historiales de chat) y archivos pesados (las fotos y audios).

-**Base de datos relacional (SQL):** PostgreSQL o MySQL. ideal para guardar los registros de las interacciones de voz, los enlaces a los archivos multimedia y la información de los usuarios.

-**Almacenamiento de objetos (Object Storage):** No hay que guardar fotos ni videos directamente dentro de la base de datos. Se usa un servicio de almacenamiento en la nube estilo **Amazon S3, Google Cloud Storage, o alternativas más económicas como Wasabi o Backblaze B2**. las gafas suben la foto mediante una URL firmada y se almacena de forma segura y escalable.

### 3. Servicios De IA
