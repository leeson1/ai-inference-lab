# 简历项目描述

## 项目总结

构建了一个基于 Go 的 LLM 推理网关，接入 vLLM 和 SGLang 等 OpenAI-compatible 后端，支持流式响应、模型路由、超时控制、限流、Prometheus 指标和 token 用量统计。

## 简历要点

- 设计并实现 Go 语言 LLM 推理网关，接入 vLLM/SGLang 等 OpenAI-compatible 后端，支持流式输出、模型路由和 provider 抽象。
- 增加请求超时、取消、基础限流、in-flight 请求统计和后端过载保护等生产化控制能力。
- 构建压测脚本，统计不同 prompt 长度、输出长度和并发下的 TTFT、TPOT、总延迟、p95/p99 延迟、吞吐和成功率。
- 系统学习并整理 KV Cache、PagedAttention、continuous batching、prefix caching、chunked prefill、speculative decoding 和量化等推理核心机制。
- 准备 CUDA/HPC 学习实验，覆盖 vector add、matrix transpose、reduction、naive GEMM 和 Nsight 基础 profiling。