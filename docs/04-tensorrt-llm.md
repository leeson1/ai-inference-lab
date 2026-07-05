# TensorRT-LLM 笔记

## 目标

理解 TensorRT-LLM 作为 NVIDIA GPU 优化推理路径的定位。

它不是第一阶段最需要掌握的工具。建议在跑通 vLLM 和 SGLang 之后再学习。

## 需要学习什么

- TensorRT-LLM 架构
- engine build 概念
- Serving 模型
- in-flight batching
- paged KV cache
- 量化
- 多 GPU 与多节点 Serving
- speculative decoding

## 清单

- [ ] 阅读 TensorRT-LLM overview
- [ ] 理解 build 和 serve 的工作流差异
- [ ] 和 vLLM、SGLang 做对比
- [ ] 记录硬件要求
- [ ] 如果本地 GPU 环境支持，运行一个小例子

## 需要回答的问题

1. 为什么 TensorRT-LLM 重点面向 NVIDIA GPU？
2. TensorRT/TensorRT-LLM 里的 engine 是什么？
3. 什么是 in-flight batching？
4. 常见的量化模式有哪些？
5. 公司什么时候会选择 TensorRT-LLM，而不是 vLLM？

## 对比模板

| 系统 | 优势 | 劣势 | 最适合场景 |
|---|---|---|---|
| vLLM | serving 简单、PagedAttention、社区广 | 在所有 NVIDIA 路径上未必都是极限性能 | 通用 LLM Serving |
| SGLang | 结构化生成、runtime 优化 | 需要学习的概念更多 | agent / 结构化生成负载 |
| TensorRT-LLM | NVIDIA 优化推理 | 部署和 build 复杂度更高 | NVIDIA GPU 上的高性能生产环境 |