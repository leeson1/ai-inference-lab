# Benchmark

## 目标

用测量来理解 LLM Serving 性能，而不是靠猜。

## 指标

- TTFT
- TPOT
- 总延迟
- p50 / p95 / p99
- requests per second
- output tokens per second
- success rate

## 负载

- 短 prompt
- 长 prompt
- 长输出
- 混合负载

## 第一版命令形态

```bash
python benchmark/bench.py \
  --url http://localhost:8000/v1/chat/completions \
  --model qwen \
  --concurrency 10 \
  --max-tokens 128
```

## 报告输出

把 benchmark 报告放到：

```text
benchmark/reports/
```