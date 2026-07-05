# Benchmark Metrics

## Goal

Build the habit of measuring inference systems instead of only reading about them.

## Core Metrics

### TTFT

Time To First Token.

Measures how long it takes before the first generated token is received by the client.

Important for user-perceived responsiveness.

### TPOT

Time Per Output Token.

Measures decode speed after the first token.

Important for long responses.

### Total Latency

End-to-end request duration.

### Throughput

Common forms:

- requests per second
- output tokens per second
- total tokens per second

### P50 / P95 / P99

Latency percentile metrics.

P95/P99 are usually more important than average latency in production systems.

### GPU Metrics

- GPU utilization
- GPU memory used
- GPU memory free
- power usage
- temperature
- SM occupancy if profiling with Nsight

## Workload Dimensions

A benchmark must vary these dimensions:

- prompt length
- output length
- concurrency
- model size
- backend system
- stream vs non-stream

## First Benchmark Cases

| case | prompt | output | concurrency |
|---|---|---:|---:|
| short-prompt-low-concurrency | short | 128 | 1 |
| short-prompt-high-concurrency | short | 128 | 20 |
| long-prompt-low-concurrency | long | 128 | 1 |
| long-prompt-high-concurrency | long | 128 | 20 |
| long-output | short | 1024 | 5 |
| mixed-workload | mixed | mixed | 20 |

## Report Template

```md
# Benchmark Report

## Environment

- GPU:
- Driver:
- CUDA:
- Model:
- Backend:
- Command:

## Results

| case | concurrency | max tokens | TTFT p50 | TTFT p95 | TPOT p50 | total p95 | output tok/s |
|---|---:|---:|---:|---:|---:|---:|---:|

## Observations

## Bottleneck Guess

## Next Experiment
```
