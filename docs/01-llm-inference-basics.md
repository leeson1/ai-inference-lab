# LLM Inference Basics

## Core Question

Why is LLM inference expensive?

The cost comes mainly from:

- model size
- prompt length
- output length
- KV Cache memory
- batching strategy
- GPU utilization
- network and streaming overhead

## Prefill

Prefill processes the input prompt and builds the initial KV Cache.

Characteristics:

- compute-heavy
- benefits from parallelism
- latency grows with prompt length

## Decode

Decode generates tokens one by one.

Characteristics:

- memory-bandwidth-sensitive
- depends heavily on KV Cache access
- latency grows with output length

## KV Cache

KV Cache stores previous key/value tensors so the model does not recompute attention history for every generated token.

Why it matters:

- it grows with sequence length
- it consumes large GPU memory
- it limits max concurrency
- inefficient allocation causes fragmentation and waste

## Key Metrics

### TTFT

Time To First Token.

Represents how long users wait before seeing the first generated token.

### TPOT

Time Per Output Token.

Represents decode speed after the first token.

### Throughput

Usually measured as:

- requests per second
- output tokens per second
- total tokens per second

### Latency

Usually measured as:

- total request latency
- p50 latency
- p95 latency
- p99 latency

## Important Tradeoff

Higher batching often improves throughput but may increase individual request latency.

Inference engineering is mostly about balancing:

```text
latency vs throughput vs GPU memory vs cost
```

## First Experiment

Run one model with vLLM and record:

| prompt type | concurrency | max tokens | TTFT | TPOT | total latency |
|---|---:|---:|---:|---:|---:|
| short | 1 | 128 | TBD | TBD | TBD |
| long | 1 | 128 | TBD | TBD | TBD |
| short | 10 | 128 | TBD | TBD | TBD |
| long | 10 | 128 | TBD | TBD | TBD |
