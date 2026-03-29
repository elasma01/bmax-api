# bmax-api

API Java Spring Boot basee sur Spring AI qui sert de proxy HTTP vers OpenAI.

## Fonctionnalites

- `GET /v1/models`
- `POST /v1/chat/completions`
- configuration par variables d'environnement
- modele configurable

## Variables d'environnement

```bash
export OPENAI_API_KEY=sk-...
export OPENAI_MODEL=gpt-4o-mini
export SERVER_PORT=8080
```

Variables optionnelles:

```bash
export OPENAI_BASE_URL=https://api.openai.com
export OPENAI_TEMPERATURE=0.2
export PROXY_PUBLIC_MODEL_NAME=gpt-4o-mini
```

## Lancer

```bash
mvn spring-boot:run
```

## Exemple

```bash
curl http://localhost:8080/v1/chat/completions \
  -H 'Content-Type: application/json' \
  -d '{
    "model": "gpt-4o-mini",
    "messages": [
      { "role": "system", "content": "You are concise." },
      { "role": "user", "content": "Donne-moi un resume en une phrase." }
    ],
    "temperature": 0.2
  }'
```

## Limites

- streaming non implemente
- tools / function calling non implementes
- compatibilite OpenAI partielle et ciblee chat completions
