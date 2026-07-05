# AI Inference Learning Roadmap

This roadmap is designed for a backend engineer moving into AI inference engineering.

## Overall Strategy

```text
Phase 1: LLM inference basics
Phase 2: vLLM / SGLang deployment and benchmark
Phase 3: Go inference gateway
Phase 4: observability and cost metrics
Phase 5: inference optimization concepts
Phase 6: CUDA / HPC foundation
```

## Phase 1: Inference Basics

Goal: understand what happens during LLM inference.

Topics:

- Transformer inference overview
- Prefill phase
- Decode phase
- KV Cache
- TTFT: Time To First Token
- TPOT: Time Per Output Token
- Latency vs throughput
- Context length and output length
- OpenAI-compatible API

Deliverables:

- `docs/01-llm-inference-basics.md`
- vLLM local serving screenshot or command log
- first latency measurement table

## Phase 2: vLLM / SGLang Benchmark

Goal: learn serving systems by measuring them.

Topics:

- vLLM deployment
- SGLang deployment
- streaming response
- concurrent requests
- short prompt workload
- long prompt workload
- mixed workload
- p50 / p95 / p99 latency
- TTFT / TPOT / throughput

Deliverables:

- `benchmark/bench.py`
- `benchmark/cases/*.yaml`
- `benchmark/reports/report-001.md`

## Phase 3: Go Inference Gateway

Goal: use backend engineering skills to build a production-style LLM serving gateway.

Features:

- `/v1/models`
- `/v1/chat/completions`
- stream forwarding
- provider abstraction
- vLLM provider
- SGLang provider
- model routing
- timeout and cancellation
- basic rate limiting

Deliverables:

- runnable Go server under `gateway/`
- config file under `gateway/configs/config.yaml`
- curl examples in `gateway/README.md`

## Phase 4: Observability and Cost Metrics

Goal: make the gateway look like a real platform component.

Metrics:

- request count
- failure count
- in-flight requests
- total latency histogram
- TTFT histogram
- TPOT histogram
- input tokens
- output tokens
- model-level metrics
- user-level metrics

Deliverables:

- Prometheus endpoint
- `deploy/prometheus/prometheus.yml`
- benchmark report with metric screenshots or sample output

## Phase 5: Inference Optimization Concepts

Goal: move from "can deploy" to "can reason about bottlenecks".

Topics:

- PagedAttention
- Continuous batching
- Prefix caching
- Chunked prefill
- Speculative decoding
- Quantization: INT8 / INT4 / FP8
- Tensor parallelism
- Pipeline parallelism
- GPU memory pressure

Deliverables:

- `docs/06-kv-cache.md`
- `docs/07-batching-scheduling.md`
- `docs/08-quantization.md`
- one written comparison: vLLM vs SGLang vs TensorRT-LLM

## Phase 6: CUDA / HPC Foundation

Goal: build the foundation for long-term GPU performance engineering.

Topics:

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

Labs:

- vector add
- matrix transpose
- reduction
- naive GEMM

Deliverables:

- CUDA lab code under `cuda-labs/`
- profiling notes under `docs/10-cuda-hpc-next-step.md`

## Weekly Rhythm

Every week should produce at least one visible artifact:

- one note
- one benchmark result
- one code commit
- one issue closed
- one interview Q&A entry

## Job Target

First target role:

```text
AI Inference Platform Backend Engineer
LLM Serving Backend Engineer
Model Serving Platform Engineer
AI Infra Backend Engineer
```

Later target role:

```text
Inference Performance Engineer
GPU Infra Engineer
CUDA / HPC Engineer
```
