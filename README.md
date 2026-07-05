# AI Inference Lab

This repository is a hands-on learning and portfolio project for **LLM inference engineering**.

The short-term goal is to move from game backend development into AI inference platform engineering. The long-term goal is to build a path toward GPU performance engineering, CUDA, and HPC.

## Career Direction

```text
AI Inference Platform Backend -> Inference Performance Engineering -> CUDA / HPC / GPU Infra
```

This repo is designed around one practical project:

> Build a production-style LLM inference gateway and use it to study modern LLM serving systems.

## Final Project

A Go-based LLM inference gateway with:

- OpenAI-compatible API forwarding
- Streaming response forwarding
- vLLM / SGLang backend routing
- Model-level routing
- Request timeout and cancellation
- Basic rate limiting
- Prometheus metrics
- TTFT / TPOT / latency tracking
- Token usage statistics
- Benchmark reports

## Why This Project

Modern LLM serving is not just API wrapping. The core engineering problems are latency, throughput, batching, KV cache memory, GPU utilization, scheduling, observability, and cost.

The main systems to study:

- vLLM
- SGLang
- TensorRT-LLM
- CUDA / GPU profiling fundamentals

## Repository Structure

```text
.
├── ROADMAP.md
├── docs/                  # Learning notes
├── gateway/               # Go inference gateway project
├── benchmark/             # Benchmark scripts and reports
├── deploy/                # Local deployment configs
├── cuda-labs/             # CUDA/HPC learning labs
└── interview/             # Interview notes and resume bullets
```

## Learning Principle

Do not only read documents. Every learning unit should produce one of the following:

- a runnable demo
- a benchmark report
- a design note
- a comparison document
- a resume-ready project summary

## Current Phase

Start with Phase 1 in [ROADMAP.md](./ROADMAP.md): run vLLM locally, call the OpenAI-compatible API, and measure basic inference metrics.
