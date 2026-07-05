# Benchmark

## Goal

Measure LLM serving performance instead of guessing.

## Metrics

- TTFT
- TPOT
- total latency
- p50 / p95 / p99
- requests per second
- output tokens per second
- success rate

## Workloads

- short prompt
- long prompt
- long output
- mixed workload

## First Command Shape

```bash
python benchmark/bench.py \
  --url http://localhost:8000/v1/chat/completions \
  --model qwen \
  --concurrency 10 \
  --max-tokens 128
```

## Report Output

Put benchmark reports under:

```text
benchmark/reports/
```
