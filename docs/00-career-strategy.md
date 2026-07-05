# 职业策略：AI 推理 -> HPC

## 定位

目标不是先成为算法研究员，而是成为能构建、运维、测量和优化 LLM 推理系统的工程师。

推荐路线：

```text
AI 推理平台后端 -> 推理性能工程 -> CUDA/HPC/GPU Infra
```

## 为什么从 AI 推理开始

相比直接跳到 CUDA/HPC，从 AI 推理切入更现实：

- 它和后端工程能力衔接更自然。
- 岗位数量通常比纯 CUDA/HPC 岗更多。
- 可以逐步接触 GPU 性能问题。
- 更容易较快产出能写进简历的项目。

## 短期岗位目标

第一阶段转型目标岗位：

- AI Inference Platform Backend Engineer
- LLM Serving Backend Engineer
- Model Serving Platform Engineer
- AI Infra Backend Engineer

核心能力：

> 围绕 vLLM、SGLang、TensorRT-LLM、模型路由、流式响应、可观测性和 benchmark 分析，构建可靠的 LLM Serving 系统。

## 中期差异化能力

进入领域后，继续深挖：

- KV Cache 显存管理
- continuous batching
- prefix caching
- chunked prefill
- speculative decoding
- 量化
- 多 GPU Serving
- GPU 利用率监控
- 推理成本优化

## 长期护城河

长期技术护城河应该来自：

- CUDA 基础
- GPU memory hierarchy
- 使用 Nsight 做 profiling
- Triton / CUTLASS / CUDA kernels
- NCCL / RDMA 基础
- 分布式 GPU 集群运维
- 推理性能优化

## 不要做什么

避免这些坑：

- 只做 chatbot demo
- 只包 OpenAI API
- 只收集学习笔记，没有 benchmark 数据
- 在还没有推理 serving 上下文之前，就直接长时间钻 CUDA kernel
- 同时分散在 AI 推理、强化学习、游戏 AI 和 HPC 多个方向

## 简历叙事方向

最终简历故事应该是：

> 构建了一个基于 Go 的 LLM 推理网关，接入 vLLM/SGLang 后端，支持 OpenAI-compatible API、流式响应、模型路由、限流、Prometheus 指标，并在不同负载下 benchmark 了 TTFT、TPOT 和吞吐。