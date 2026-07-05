# TensorRT-LLM Notes

## Goal

Understand TensorRT-LLM as the NVIDIA GPU optimized inference path.

This is not the first tool to master. Study it after running vLLM and SGLang.

## What To Learn

- TensorRT-LLM architecture
- engine build concept
- serving model
- in-flight batching
- paged KV cache
- quantization
- multi-GPU and multi-node serving
- speculative decoding

## Checklist

- [ ] Read TensorRT-LLM overview
- [ ] Understand build vs serve workflow
- [ ] Compare it with vLLM and SGLang
- [ ] Record hardware requirements
- [ ] Run a small example if local GPU environment supports it

## Questions To Answer

1. Why does TensorRT-LLM focus on NVIDIA GPUs?
2. What is an engine in TensorRT/TensorRT-LLM?
3. What is in-flight batching?
4. What quantization modes are commonly used?
5. When would a company choose TensorRT-LLM instead of vLLM?

## Comparison Template

| system | strength | weakness | best scenario |
|---|---|---|---|
| vLLM | easy serving, PagedAttention, broad community | may not be max performance on every NVIDIA path | general LLM serving |
| SGLang | structured generation, runtime optimizations | more concepts to learn | agent / structured generation workloads |
| TensorRT-LLM | NVIDIA optimized inference | deployment/build complexity | high-performance production on NVIDIA GPUs |
