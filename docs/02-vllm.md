# vLLM Notes

## Goal

Use vLLM as the first practical LLM serving system.

## Why vLLM

vLLM is a high-throughput LLM inference and serving engine. The most important concept to study first is PagedAttention, which manages KV Cache memory more efficiently.

## Learning Checklist

- [ ] Start an OpenAI-compatible vLLM server
- [ ] Call `/v1/models`
- [ ] Call `/v1/chat/completions`
- [ ] Test streaming output
- [ ] Measure TTFT
- [ ] Measure total latency
- [ ] Compare short prompt and long prompt
- [ ] Compare low concurrency and high concurrency

## Local Run Template

```bash
python -m vllm.entrypoints.openai.api_server \
  --model <model-name> \
  --host 0.0.0.0 \
  --port 8000
```

## API Test

```bash
curl http://localhost:8000/v1/models
```

```bash
curl http://localhost:8000/v1/chat/completions \
  -H 'Content-Type: application/json' \
  -d '{
    "model": "<model-name>",
    "messages": [{"role": "user", "content": "Explain KV Cache in LLM inference."}],
    "max_tokens": 128,
    "stream": true
  }'
```

## Questions To Answer

1. What happens during prefill?
2. What happens during decode?
3. Why does KV Cache consume so much GPU memory?
4. Why does batching improve throughput?
5. Why can batching hurt latency?
6. What does PagedAttention optimize?

## Benchmark Table

| case | concurrency | prompt length | max tokens | TTFT | TPOT | total latency | notes |
|---|---:|---:|---:|---:|---:|---:|---|
| short prompt | 1 | TBD | 128 | TBD | TBD | TBD | TBD |
| long prompt | 1 | TBD | 128 | TBD | TBD | TBD | TBD |
| short prompt | 10 | TBD | 128 | TBD | TBD | TBD | TBD |
| long prompt | 10 | TBD | 128 | TBD | TBD | TBD | TBD |
