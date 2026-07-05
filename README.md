# AI Inference Lab

这个仓库是一个面向 **LLM 推理工程** 的动手学习与作品集项目。

短期目标：从游戏后端开发转向 AI 推理平台工程。长期目标：逐步深入 GPU 性能工程、CUDA 和 HPC。

## 职业方向

```text
AI 推理平台后端 -> 推理性能工程 -> CUDA / HPC / GPU Infra
```

这个仓库围绕一个实践项目展开：

> 构建一个具备生产化雏形的 LLM 推理网关，并通过它系统学习现代 LLM Serving 系统。

## 最终项目

一个基于 Go 的 LLM 推理网关，包含：

- OpenAI-compatible API 转发
- 流式响应转发
- vLLM / SGLang 后端路由
- 模型级路由
- 请求超时与取消
- 基础限流
- Prometheus 指标
- TTFT / TPOT / 延迟追踪
- Token 用量统计
- Benchmark 报告

## 为什么做这个项目

现代 LLM Serving 不只是包一层 API。核心工程问题包括延迟、吞吐、batching、KV Cache 显存、GPU 利用率、调度、可观测性和成本。

主要学习对象：

- vLLM
- SGLang
- TensorRT-LLM
- CUDA / GPU profiling 基础

## 仓库结构

```text
.
├── ROADMAP.md
├── docs/                  # 学习笔记
├── gateway/               # Go 推理网关项目
├── benchmark/             # 压测脚本与报告
├── deploy/                # 本地部署配置
├── cuda-labs/             # CUDA/HPC 学习实验
└── interview/             # 面试笔记与简历项目描述
```

## 学习原则

不要只读文档。每个学习单元至少产出下面一种可见成果：

- 一个可运行 demo
- 一份 benchmark 报告
- 一篇设计笔记
- 一份对比文档
- 一段可写进简历的项目总结

## 当前阶段

从 [ROADMAP.md](./ROADMAP.md) 的 Phase 1 开始：本地运行 vLLM，调用 OpenAI-compatible API，并测量基础推理指标。