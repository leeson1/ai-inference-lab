# Career Strategy: AI Inference -> HPC

## Positioning

The goal is not to become an algorithm researcher first. The goal is to become an engineer who can build, operate, measure, and optimize LLM inference systems.

Recommended path:

```text
AI inference platform backend -> inference performance engineering -> CUDA/HPC/GPU infra
```

## Why Start from AI Inference

Starting from AI inference is more practical than directly jumping into CUDA/HPC:

- It connects naturally with backend engineering.
- It has more job openings than pure CUDA/HPC roles.
- It allows gradual exposure to GPU performance problems.
- It produces resume-ready projects faster.

## Short-Term Role Target

Target roles for the first transition:

- AI Inference Platform Backend Engineer
- LLM Serving Backend Engineer
- Model Serving Platform Engineer
- AI Infra Backend Engineer

Core capability:

> Build reliable serving systems around vLLM, SGLang, TensorRT-LLM, model routing, streaming responses, observability, and benchmark analysis.

## Medium-Term Differentiation

After entering the field, deepen the following:

- KV Cache memory management
- continuous batching
- prefix caching
- chunked prefill
- speculative decoding
- quantization
- multi-GPU serving
- GPU utilization monitoring
- inference cost optimization

## Long-Term Moat

Long-term technical moat should come from:

- CUDA fundamentals
- GPU memory hierarchy
- profiling with Nsight
- Triton / CUTLASS / CUDA kernels
- NCCL / RDMA basics
- distributed GPU cluster operations
- inference performance optimization

## What Not To Do

Avoid these traps:

- only building chatbot demos
- only wrapping OpenAI APIs
- only collecting learning notes without benchmark data
- starting with deep CUDA kernel work before having inference serving context
- spreading attention across AI inference, RL, game AI, and HPC at the same time

## Resume Direction

The final resume story should be:

> Built a Go-based LLM inference gateway, integrated vLLM/SGLang backends, supported OpenAI-compatible APIs, streaming responses, model routing, rate limiting, Prometheus metrics, and benchmarked TTFT/TPOT/throughput under different workloads.
