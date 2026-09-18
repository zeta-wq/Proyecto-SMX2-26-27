# Servicios
### 1. Servidor
Dado que las gafas no pueden procesar la IA por sí solas, se necesita potencia en la nube para ejecutar el backend, la transcripción de voz y los modelos de lenguaje.
Se instalará Python con un framework ligero como FastAPI o Flask para crear una pequeña API que reciba las fotos y los audios de tus gafas.

-**Se necesita un servidor con Linux (Ubuntu Server)** que tenga al menos 2 o 4 GB de RAM para empezar. Si vas a correr modelos de IA pesados de forma local en el servidor (como Ollama/Llama), se necesitará un VPS con GPU, aunque para prototipos iniciales es mejor usar APIs de pago por uso (como OpenAI Whisper + GPT-4o-mini) para ahorrar costes de servidor gráfico.

-**Gestor de Contenedores (Docker)**: Es imprescindible. Te permitirá empaquetar tu servidor (el backend en Python, la base de datos, etc.) para que corra igual tanto en tu ordenador de pruebas como en la nube sin sorpresas.

### 1.1 El dominio
**1. Consigue un dominio (o subdominio gratuito):**

Puedes usar servicios gratuitos de DDNS como No-IP o DuckDNS. Te darán un dominio gratis del tipo tualumno.duckdns.org.

Si prefieres comprar un dominio propio real (por ejemplo, misgafasai.com que cuesta muy poco al año), puedes hacerlo en cualquier registrador.

**2. Instala un cliente DDNS en tu ordenador:**

En el servidor instalas un programita pequeño proporcionado por DuckDNS o No-IP.

**4. Configura las gafas:**

En el código del XIAO ESP32-S3, en lugar de poner una IP local, poner el dominio: [http://tualumno.duckdns.org:8000/api/subir](http://tualumno.duckdns.org:8000/api/subir) (o usando un túnel como Cloudflare Tunnels, que te ahorra abrir puertos en el router).

### 2. Base de datos
Se necesitará alamcenar dos tipos de información: datos estructurados (perfiles de usuarios, metadatos de fotos, marcas de tiempo, historiales de chat) y archivos pesados (las fotos y audios).

-**Base de datos relacional (SQL):** PostgreSQL o MySQL. ideal para guardar los registros de las interacciones de voz, los enlaces a los archivos multimedia y la información de los usuarios.

-**Almacenamiento de objetos (Object Storage):** No hay que guardar fotos ni videos directamente dentro de la base de datos. Se usa un servicio de almacenamiento en la nube estilo **Amazon S3, Google Cloud Storage, o alternativas más económicas como Wasabi o Backblaze B2**. las gafas suben la foto mediante una URL firmada y se almacena de forma segura y escalable.

### 3. Servicios De IA
Se usará como IA Ollama, version qwen3.5b:8.

**1. El flujo de la IA (Cómo funciona en la práctica)**
-Imagina el ciclo cuando usas las gafas:

-Comando: Pulsas el botón de las gafas y dices: "Haz una foto" o "¿Qué ves?".

-Transcripción: El audio viaja al servidor, donde una IA lo convierte instantáneamente de Voz a Texto (Speech-to-Text).

-Razonamiento: El texto pasa por un Modelo de Lenguaje (LLM), que entiende qué quieres hacer (ej. tomar una foto, o responderte a una pregunta sobre algo).

-Respuesta: El servidor ejecuta la acción o genera una respuesta de texto, la cual opcionalmente puede convertirse de nuevo a Texto a Voz (Text-to-Speech) para que las gafas te la devuelvan por un altavoz.

**2. ¿Qué tecnologías usar para la IA? (Gratis y potentes)**
Para un proyecto escolar, no se necesita entrenar tus propios modelos (lo cual sería imposible). Lo inteligente es usar herramientas existentes conectadas mediante APIs o ejecutadas localmente:

**A. Para convertir tu voz en texto (Speech-to-Text):**
Opción recomendada: OpenAI Whisper (API) o correr el modelo Whisper (versión tiny o base) directamente en Python en tu ordenador. Es extremadamente preciso, entiende español perfectamente y procesa audios cortos en menos de un segundo.

**B. Para el "Cerebro" / Conversación (LLM):**
Opción Cloud (La más rápida y fácil): Usar la API de OpenAI (GPT-4o-mini) o la API de Groq (que ofrece modelos como Llama 3 a una velocidad brutal de cientos de tokens por segundo). Tienen capas gratuitas o costes mínimos para desarrolladores que te durarán todo el proyecto.

Opción 100% Local (Sin internet y sin gastar nada): Instalar Ollama en tu ordenador servidor. Te permite descargar y correr modelos de IA de código abierto (como Llama 3 o Mistral) localmente en tu CPU/GPU. Así, aunque estés sin internet, la IA sigue respondiendo.

**C. Para que la IA "vea" tus fotos (Visión por Computador):**
Cuando las gafas tomen una foto y la envíen al servidor, se puede usar modelos multimodales (como GPT-4o-mini o Llama 3.2 Vision) enviándoles la imagen junto con tu pregunta de voz ("¿Qué objeto es este?" o "¿En qué dirección estoy?"), para que la IA te responda analizando lo que tus gafas acaban de capturar.

**3. ¿Cómo se programa esto en el servidor (Python)?**
En el servidor de Python (usando FastAPI), la estructura del código de IA se vería más o menos así de simple:

Python

    import openai  # O la librería que elijas

    @app.post("/api/interaccion")
    async def procesar_ia(audio_file, image_file=None):

    # 1. Transcribir el audio de las gafas a texto usando Whisper
    texto_usuario = whisper.transcribe(audio_file)
    
    # 2. Enviar el texto (y la foto si la hay) al modelo de IA
    respuesta_ia = openai.ChatCompletion.create(
        model="gpt-4o-mini",
        messages=[{"role": "user", "content": f"El usuario de las gafas dijo: {texto_usuario}"}]
    )
    
    texto_respuesta = respuesta_ia.choices[0].message.content
    
    # 3. Devolver la respuesta a las gafas (en texto o convertida a audio)
    return {"respuesta": texto_respuesta}
