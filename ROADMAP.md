# AI 推理学习路线图

这份路线图面向想转向 AI 推理工程的后端工程师。

## 总体策略

```text
Phase 1: LLM 推理基础
Phase 2: vLLM / SGLang 部署与 benchmark
Phase 3: Go 推理网关
Phase 4: 可观测性与成本指标
Phase 5: 推理优化核心概念
Phase 6: CUDA / HPC 基础
```

## Phase 1：推理基础

目标：理解 LLM 推理时到底发生了什么。

主题：

- Transformer 推理流程概览
- Prefill 阶段
- Decode 阶段
- KV Cache
- TTFT：Time To First Token
- TPOT：Time Per Output Token
- 延迟与吞吐
- 上下文长度与输出长度
- OpenAI-compatible API

交付物：

- `docs/01-llm-inference-basics.md`
- vLLM 本地 serving 的截图或命令日志
- 第一份延迟测量表

## Phase 2：vLLM / SGLang Benchmark

目标：通过测量来学习 Serving 系统。

主题：

- vLLM 部署
- SGLang 部署
- 流式响应
- 并发请求
- 短 prompt 负载
- 长 prompt 负载
- 混合负载
- p50 / p95 / p99 延迟
- TTFT / TPOT / 吞吐

交付物：

- `benchmark/bench.py`
- `benchmark/cases/*.yaml`
- `benchmark/reports/report-001.md`

## Phase 3：Go 推理网关

目标：利用后端工程能力构建具备生产化雏形的 LLM Serving 网关。

功能：

- `/v1/models`
- `/v1/chat/completions`
- 流式转发
- provider 抽象
- vLLM provider
- SGLang provider
- 模型路由
- 超时与取消
- 基础限流

交付物：

- `gateway/` 下可运行的 Go 服务
- `gateway/configs/config.yaml` 配置文件
- `gateway/README.md` 中的 curl 示例

## Phase 4：可观测性与成本指标

目标：让网关看起来像一个真实的平台组件。

指标：

- 请求数
- 失败数
- in-flight 请求数
- 总延迟直方图
- TTFT 直方图
- TPOT 直方图
- 输入 token 数
- 输出 token 数
- 模型级指标
- 用户级指标

交付物：

- Prometheus endpoint
- `deploy/prometheus/prometheus.yml`
- 带指标截图或样例输出的 benchmark 报告

## Phase 5：推理优化概念

目标：从“能部署”提升到“能分析瓶颈”。

主题：

- PagedAttention
- Continuous batching
- Prefix caching
- Chunked prefill
- Speculative decoding
- 量化：INT8 / INT4 / FP8
- Tensor parallelism
- Pipeline parallelism
- GPU 显存压力

交付物：

- `docs/06-kv-cache.md`
- `docs/07-batching-scheduling.md`
- `docs/08-quantization.md`
- 一份对比文档：vLLM vs SGLang vs TensorRT-LLM

## Phase 6：CUDA / HPC 基础

目标：为长期 GPU 性能工程打基础。

主题：

- CUDA thread / block / grid
- warp
- global memory
- shared memory
- register memory
- memory coalescing
- occupancy
- cuda stream
- cuda event
- Nsight Systems
- Nsight Compute

实验：

- vector add
- matrix transpose
- reduction
- naive GEMM

交付物：

- `cuda-labs/` 下的 CUDA 实验代码
- `docs/10-cuda-hpc-next-step.md` 下的 profiling 笔记

## 每周节奏

每周至少产出一个可见成果：

- 一篇笔记
- 一份 benchmark 结果
- 一次代码提交
- 一个关闭的 issue
- 一篇面试问答

## 求职目标

第一阶段目标岗位：

```text
AI Inference Platform Backend Engineer
LLM Serving Backend Engineer
Model Serving Platform Engineer
AI Infra Backend Engineer
```

后续目标岗位：

```text
Inference Performance Engineer
GPU Infra Engineer
CUDA / HPC Engineer
```