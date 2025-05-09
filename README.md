# mlvoca.com

## A free LLM API

This repository provides access to a publicly `/api/generate` endpoint from the Ollama API, enabling text generation through various models.
<br>

<div style="border-radius: 15px; overflow: hidden;">
    <img src="https://github.com/mlvoca/mlvoca.com/blob/main/images/mlvoca_image2.png?raw=true" style="width: 70%;">
</div>

## Base URL
```
https://mlvoca.com
```

## Endpoint: Generate a Completion

### **POST** `/api/generate`

Generates a response based on a given prompt using a specified model. It supports both streaming and single-response generation.

### Available Models
- TinyLlama
- DeepSeek R1 (1.5b)

### Request Parameters

Accepts the following parameters:

- **`model` (required)** - The model name used for generation (can be `"tinyllama"` or `"deepseek-r1:1.5b"`).
- **`prompt` (required)** - The input prompt for text generation.
- **`suffix`** - Text appended after the model response.
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
  "model": "tinyllama",
  "prompt": "Why is the sky blue?"
}
```

#### Generate text without streaming:
```
POST /api/generate
{
  "model": "tinyllama",
  "prompt": "Why is the sky blue?",
  "stream": false
}
```

#### Shell commands for API requests:
```sh
curl -X POST https://mlvoca.com/api/generate -d '{
  "model": "deepseek-r1:1.5b",
  "prompt": "Why is the sky blue?"
}'
```

```sh
curl -X POST https://mlvoca.com/api/generate -d '{
  "model": "tinyllama",
  "prompt": "Why is the sky blue?",
  "stream": false
}'
```

### Example Responses

#### Streaming response:
```
{
  "model": "deepseek-r1:1.5b",
  "created_at": "2025-05-09T19:32:00Z",
  "response": "The",
  "done": false
}
```

#### Final streamed object:
```
{
  "model": "tinyllama",
  "created_at": "2025-05-09T19:33:00Z",
  "response": "The sky is blue due to Rayleigh scattering.",
  "done": true,
  "total_duration": 5043500667,
  "load_duration": 5025959,
  "prompt_eval_count": 26,
  "prompt_eval_duration": 325953000,
  "eval_count": 290,
  "eval_duration": 4709213000
}
```

#### Single-response output:
```
{
  "model": "tinyllama",
  "created_at": "2025-05-09T19:34:00Z",
  "response": "The sky is blue because of Rayleigh scattering.",
  "done": true
}
```

---
