# KV Cache

## What Is KV Cache

In autoregressive decoding, each generated token attends to previous tokens. KV Cache stores the key/value tensors from previous tokens so the model does not recompute them every step.

## Why It Matters

KV Cache is one of the most important memory bottlenecks in LLM inference.

It grows with:

- batch size
- sequence length
- number of layers
- hidden dimension
- precision

## Problems

- Large memory footprint
- Dynamic growth and shrinkage
- Fragmentation
- Lower max concurrency
- Waste from duplicated prefixes

## Related Techniques

- PagedAttention
- prefix caching
- KV Cache quantization
- KV Cache eviction/compression
- prefill/decode separation

## Questions

1. Why is KV Cache needed?
2. Why does KV Cache grow during decode?
3. Why does long context reduce concurrency?
4. Why does prefix sharing help?
5. Why does PagedAttention borrow ideas from OS virtual memory?

## Notes

PagedAttention partitions KV Cache into blocks and maps logical blocks to physical blocks. This reduces memory waste and allows sharing across requests or decoding branches.
