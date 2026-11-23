# Rodrigo · Minería de Datos

Prepara cotizaciones de análisis, preprocesamiento, modelado y evaluación de datos. Expone una Agent Card y recibe solicitudes mediante A2A HTTP.

## Requisitos y configuración

Requiere Python 3.12, una cuenta de Gemini y una clave `GOOGLE_API_KEY`. El
archivo `.python-version` fija la versión usada por Heroku.

```bash
python3 -m venv .venv
source .venv/bin/activate
python -m pip install -r requirements.txt
cp .env.example .env
```

Configura `.env` sin publicar secretos:

```env
GOOGLE_API_KEY=tu_clave_de_gemini
MODELO=gemini-3.5-flash-lite
URL_RODRIGO_MINERIA_DE_DATOS=http://127.0.0.1:8000
```

## Ejecución local

```bash
uvicorn src.agente_Rodrigo_mineria_de_datos.server:app --port 8000
```

Verifica la Agent Card:

```text
http://127.0.0.1:8000/.well-known/agent-card.json
```

Para detener el agente utiliza `Ctrl+C`.

## Heroku

1. Crea una aplicación Heroku y conecta este repositorio en **Deploy → GitHub**.
2. Configura `GOOGLE_API_KEY`, `MODELO` y `URL_RODRIGO_MINERIA_DE_DATOS`. Esta última debe ser la
   URL base HTTPS de la propia aplicación, por ejemplo
   `https://NOMBRE-APP.herokuapp.com`.
3. Despliega la rama `main`. El `Procfile` inicia el servidor A2A.
4. Verifica:

```text
https://NOMBRE-APP.herokuapp.com/.well-known/agent-card.json
```

5. Copia esa URL base en la aplicación coordinadora, usando la variable
   `URL_RODRIGO_MINERIA_DE_DATOS`.

No publiques `.env`, claves Gemini ni otros secretos.
