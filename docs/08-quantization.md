# Quantization

## Goal

Understand quantization as an inference optimization technique.

## Why Quantization

Quantization reduces memory usage and can improve inference throughput by using lower precision representations.

Common benefits:

- lower GPU memory usage
- higher batch size
- lower bandwidth pressure
- sometimes faster inference

Common costs:

- accuracy loss
- calibration complexity
- backend compatibility issues
- performance depends on hardware support

## Common Formats

- FP16
- BF16
- FP8
- INT8
- INT4

## Methods To Learn

- AWQ
- GPTQ
- SmoothQuant
- weight-only quantization
- KV Cache quantization

## Questions

1. What is the difference between weight quantization and activation quantization?
2. Why can INT4 reduce memory but not always improve latency?
3. Why does hardware support matter?
4. What is KV Cache quantization?
5. How should accuracy degradation be evaluated?

## Experiment Plan

Run the same benchmark with:

- baseline model
- quantized model

Record:

- GPU memory usage
- TTFT
- TPOT
- throughput
- response quality notes
