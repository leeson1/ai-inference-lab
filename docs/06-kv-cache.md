# KV Cache

## 什么是 KV Cache

在自回归解码中，每个生成 token 都需要关注之前的 token。KV Cache 保存历史 token 的 key/value tensor，避免模型在每一步都重复计算 attention 历史。

## 为什么重要

KV Cache 是 LLM 推理中最重要的显存瓶颈之一。

它会随着这些因素增长：

- batch size
- sequence length
- layer 数量
- hidden dimension
- precision

## 问题

- 显存占用大
- 动态增长和释放
- 显存碎片
- 降低最大并发
- 重复 prefix 带来的浪费

## 相关技术

- PagedAttention
- prefix caching
- KV Cache quantization
- KV Cache eviction/compression
- prefill/decode separation

## 问题

1. 为什么需要 KV Cache？
2. 为什么 KV Cache 会在 decode 阶段增长？
3. 为什么长上下文会降低并发？
4. 为什么 prefix sharing 有帮助？
5. 为什么 PagedAttention 借鉴了操作系统虚拟内存的思想？

## 笔记

PagedAttention 会把 KV Cache 切分成 block，并把逻辑 block 映射到物理 block。这样可以减少显存浪费，也方便不同请求或解码分支之间共享。