# Gateway

基于 Go 的 LLM 推理网关。

## 目标

在 vLLM/SGLang 前面构建一个具备生产化雏形的网关。

## 功能

- OpenAI-compatible API 转发
- `/v1/models`
- `/v1/chat/completions`
- 流式响应转发
- provider 抽象
- vLLM provider
- SGLang provider
- 模型路由
- 请求超时与取消
- 基础限流
- Prometheus 指标

## 规划结构

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

## 第一个里程碑

实现一个最小代理：

```text
client -> gateway -> vLLM OpenAI-compatible server
```

## API 示例

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