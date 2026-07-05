# SGLang 笔记

## 目标

把 SGLang 作为第二个 Serving 后端，并与 vLLM 进行对比。

## 需要学习什么

- OpenAI-compatible Serving
- 流式输出
- 结构化输出支持
- continuous batching
- RadixAttention / KV Cache 复用概念
- 混合负载下的 Serving 性能

## 清单

- [ ] 启动 SGLang server
- [ ] 调用 `/v1/models`
- [ ] 调用 `/v1/chat/completions`
- [ ] 测试流式输出
- [ ] 运行和 vLLM 相同的 benchmark case
- [ ] 写一份 vLLM vs SGLang 对比

## 需要回答的问题

1. SGLang 试图解决什么问题？
2. frontend language 和 runtime 的关系是什么？
3. 什么是 RadixAttention？
4. SGLang 可能在哪些负载下比普通 Serving 引擎更强？
5. 它和 vLLM 在 API 兼容性、部署复杂度上如何对比？

## Benchmark 表

| case | 后端 | 并发 | max tokens | TTFT | TPOT | 总延迟 | 备注 |
|---|---|---:|---:|---:|---:|---:|---|
| 短 prompt | SGLang | 1 | 128 | TBD | TBD | TBD | TBD |
| 长 prompt | SGLang | 1 | 128 | TBD | TBD | TBD | TBD |
| 混合负载 | SGLang | 10 | 128 | TBD | TBD | TBD | TBD |