# AI 推理面试问答

## Q1：什么是 TTFT？

TTFT 是 Time To First Token，衡量客户端收到第一个生成 token 之前需要等待多久。

## Q2：什么是 TPOT？

TPOT 是 Time Per Output Token，衡量首 token 之后生成 token 的平均 decode 时间。

## Q3：什么是 KV Cache？

KV Cache 在自回归解码过程中保存历史 token 的 key/value tensor。它避免重复计算 attention 历史，但会占用大量 GPU 显存。

## Q4：Prefill 和 Decode 有什么区别？

Prefill 处理输入 prompt 并构建 KV Cache。Decode 使用已有 KV Cache 逐 token 生成输出。

## Q5：为什么 batching 能提升吞吐？

Batching 通过把多个请求一起处理，提高 GPU 利用率。不过，更大的 batch 可能增加单个请求的延迟。

## Q6：什么是 PagedAttention？

PagedAttention 是一种受操作系统分页思想启发的 KV Cache 显存管理技术。它把 KV Cache 切分成 block，以减少显存浪费并支持更灵活的共享。

## Q7：为什么长上下文请求会降低并发？

长上下文请求需要更大的 KV Cache，占用更多 GPU 显存，从而减少系统可以同时服务的请求数量。

## Q8：推理网关应该做什么？

推理网关应该提供路由、流式转发、超时控制、限流、指标、token 统计和后端保护能力。