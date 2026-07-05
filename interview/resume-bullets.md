# Resume Bullets

## Project Summary

Built a Go-based LLM inference gateway that integrates OpenAI-compatible backends such as vLLM and SGLang, supports streaming responses, model routing, timeout control, rate limiting, Prometheus metrics, and token usage statistics.

## Resume Bullets

- Designed and implemented a Go-based LLM inference gateway with OpenAI-compatible API forwarding, streaming response support, model routing, and provider abstraction for vLLM/SGLang backends.
- Added production-oriented controls including request timeout, cancellation, basic rate limiting, in-flight request tracking, and backend overload protection.
- Built benchmark scripts to measure TTFT, TPOT, total latency, p95/p99 latency, throughput, and success rate under different prompt lengths, output lengths, and concurrency levels.
- Studied and documented core LLM serving mechanisms including KV Cache, PagedAttention, continuous batching, prefix caching, chunked prefill, speculative decoding, and quantization.
- Prepared CUDA/HPC learning labs covering vector add, matrix transpose, reduction, naive GEMM, and basic GPU profiling with Nsight.

## Chinese Version

- 设计并实现 Go 语言 LLM 推理网关，接入 vLLM/SGLang 等 OpenAI-compatible 后端，支持流式输出、模型路由和 provider 抽象。
- 增加请求超时、取消、基础限流、in-flight 请求统计和后端过载保护等生产化控制能力。
- 构建压测脚本，统计不同 prompt 长度、输出长度和并发下的 TTFT、TPOT、总延迟、p95/p99 延迟、吞吐和成功率。
- 系统学习并整理 KV Cache、PagedAttention、continuous batching、prefix caching、chunked prefill、speculative decoding 和量化等推理核心机制。
- 准备 CUDA/HPC 学习实验，覆盖 vector add、matrix transpose、reduction、naive GEMM 和 Nsight 基础 profiling。
