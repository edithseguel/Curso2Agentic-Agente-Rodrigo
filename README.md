# Curso2Agentic-Agente-Rodrigo

Agente A2A independiente para cotizaciones TI.

## Ejecución local

```bash
python3 -m venv .venv
source .venv/bin/activate
python -m pip install -r requirements.txt
cp .env.example .env
uvicorn src.agente_Rodrigo_mineria_de_datos.server:app --port 8000
```

Verifica la Agent Card en `http://127.0.0.1:8000/.well-known/agent-card.json`.

## Heroku

1. Crea una aplicación Heroku y configura `GOOGLE_API_KEY`, `MODELO` y la variable de URL indicada en `.env.example`.
2. Publica este repositorio en esa aplicación.
3. Verifica `https://TU-APP.herokuapp.com/.well-known/agent-card.json`.
4. Configura la URL base obtenida en la aplicación coordinadora.
