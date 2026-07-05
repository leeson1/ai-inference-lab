# vLLM 笔记

## 目标

把 vLLM 作为第一个真正动手的 LLM Serving 系统。

## 为什么是 vLLM

vLLM 是一个高吞吐的 LLM 推理与 Serving 引擎。第一阶段最重要的概念是 PagedAttention，它可以更高效地管理 KV Cache 显存。

## 学习清单

- [ ] 启动 OpenAI-compatible 的 vLLM server
- [ ] 调用 `/v1/models`
- [ ] 调用 `/v1/chat/completions`
- [ ] 测试流式输出
- [ ] 测量 TTFT
- [ ] 测量总延迟
- [ ] 对比短 prompt 和长 prompt
- [ ] 对比低并发和高并发

## 本地运行模板

```bash
python -m vllm.entrypoints.openai.api_server \
  --model <model-name> \
  --host 0.0.0.0 \
  --port 8000
```

## API 测试

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

## 需要回答的问题

1. Prefill 阶段发生了什么？
2. Decode 阶段发生了什么？
3. 为什么 KV Cache 会占用大量 GPU 显存？
4. 为什么 batching 能提升吞吐？
5. 为什么 batching 可能伤害延迟？
6. PagedAttention 优化了什么？

## Benchmark 表

| case | 并发 | prompt 长度 | max tokens | TTFT | TPOT | 总延迟 | 备注 |
|---|---:|---:|---:|---:|---:|---:|---|
| 短 prompt | 1 | TBD | 128 | TBD | TBD | TBD | TBD |
| 长 prompt | 1 | TBD | 128 | TBD | TBD | TBD | TBD |
| 短 prompt | 10 | TBD | 128 | TBD | TBD | TBD | TBD |
| 长 prompt | 10 | TBD | 128 | TBD | TBD | TBD | TBD |