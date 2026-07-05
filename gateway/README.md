# Gateway

Go-based LLM inference gateway.

## Goal

Build a production-style gateway in front of vLLM/SGLang.

## Features

- OpenAI-compatible API forwarding
- `/v1/models`
- `/v1/chat/completions`
- streaming response forwarding
- provider abstraction
- vLLM provider
- SGLang provider
- model routing
- request timeout and cancellation
- basic rate limiting
- Prometheus metrics

## Planned Structure

```text
gateway/
├── cmd/server/main.go
├── internal/config
├── internal/router
├── internal/provider
│   ├── openai
│   ├── vllm
│   └── sglang
├── internal/limiter
├── internal/metrics
├── internal/stream
├── internal/scheduler
└── configs/config.yaml
```

## First Milestone

Implement a minimal proxy:

```text
client -> gateway -> vLLM OpenAI-compatible server
```

## API Example

```bash
curl http://localhost:8080/v1/models
```

```bash
curl http://localhost:8080/v1/chat/completions \
  -H 'Content-Type: application/json' \
  -d '{
    "model": "qwen",
    "messages": [{"role": "user", "content": "Explain KV Cache."}],
    "stream": true
  }'
```
