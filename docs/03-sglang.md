# SGLang Notes

## Goal

Use SGLang as the second serving backend and compare it with vLLM.

## What To Learn

- OpenAI-compatible serving
- streaming output
- structured output support
- continuous batching
- RadixAttention / KV Cache reuse concept
- serving performance under mixed workloads

## Checklist

- [ ] Start SGLang server
- [ ] Call `/v1/models`
- [ ] Call `/v1/chat/completions`
- [ ] Test streaming
- [ ] Run same benchmark cases used for vLLM
- [ ] Write vLLM vs SGLang comparison

## Questions To Answer

1. What problem does SGLang try to solve?
2. What is the relationship between frontend language and runtime?
3. What is RadixAttention?
4. In what workloads might SGLang be stronger than a plain serving engine?
5. How does it compare with vLLM in API compatibility and deployment complexity?

## Benchmark Table

| case | backend | concurrency | max tokens | TTFT | TPOT | total latency | notes |
|---|---|---:|---:|---:|---:|---:|---|
| short prompt | SGLang | 1 | 128 | TBD | TBD | TBD | TBD |
| long prompt | SGLang | 1 | 128 | TBD | TBD | TBD | TBD |
| mixed workload | SGLang | 10 | 128 | TBD | TBD | TBD | TBD |
