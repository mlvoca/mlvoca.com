# mlvoca.com

# Ollama API Hosting

This repository provides access to the `/api/generate` endpoint from the Ollama API, enabling text generation through various models.

## Base URL
```
https://your-api-host.com
```

## Endpoint: Generate a Completion

### **POST** `/api/generate`

Generates a response based on a given prompt using a specified model. It supports both streaming and single-response generation.

### Request Parameters

Accepts the following parameters:

- **`model` (required)** - The model name used for generation (e.g., `"llama3.2"`).
- **`prompt` (required)** - The input prompt for text generation.
- **`suffix`** - Text appended after the model response.
- **`images`** - Base64-encoded images (for multimodal models like `"llava"`).
- **`format`** - Specifies the response format (`"json"` or JSON schema).
- **`options`** - Additional model parameters (e.g., `"temperature"`).
- **`system`** - System message override.
- **`template`** - Custom prompt template.
- **`stream`** - If `false`, returns a single response instead of a stream.
- **`raw`** - If `true`, bypasses formatting and applies the full prompt.
- **`keep_alive`** - Duration the model remains loaded in memory (default: `"5m"`).

### Example Usage

#### Generate text with streaming enabled:
```
POST /api/generate
{
  "model": "llama3.2",
  "prompt": "Why is the sky blue?"
}
```

#### Generate text without streaming:
```
POST /api/generate
{
  "model": "llama3.2",
  "prompt": "Why is the sky blue?",
  "stream": false
}
```

#### Shell commands for API requests:
```sh
curl -X POST https://your-api-host.com/api/generate -d '{
  "model": "llama3.2",
  "prompt": "Why is the sky blue?"
}'
```

```sh
curl -X POST https://your-api-host.com/api/generate -d
