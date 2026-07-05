# LLM 推理基础

## 核心问题

为什么 LLM 推理成本很高？

成本主要来自：

- 模型规模
- prompt 长度
- 输出长度
- KV Cache 显存
- batching 策略
- GPU 利用率
- 网络与流式传输开销

## Prefill

Prefill 负责处理输入 prompt，并构建初始 KV Cache。

特点：

- 计算密集
- 能从并行计算中受益
- 延迟会随着 prompt 长度增加而增加

## Decode

Decode 逐 token 生成输出。

特点：

- 对显存带宽敏感
- 强依赖 KV Cache 访问
- 延迟会随着输出长度增加而增加

## KV Cache

KV Cache 保存历史 token 的 key/value tensor，避免模型在每次生成新 token 时重复计算完整 attention 历史。

为什么重要：

- 它会随着序列长度增长
- 它会占用大量 GPU 显存
- 它会限制最大并发
- 低效分配会造成碎片和浪费

## 核心指标

### TTFT

Time To First Token。

表示用户看到第一个生成 token 之前需要等待多久。

### TPOT

Time Per Output Token。

表示首 token 之后的 decode 速度。

### Throughput

通常用这些指标衡量：

- requests per second
- output tokens per second
- total tokens per second

### Latency

通常用这些指标衡量：

- 总请求延迟
- p50 延迟
- p95 延迟
- p99 延迟

## 重要取舍

更高的 batching 通常能提升吞吐，但可能增加单个请求的延迟。

推理工程的核心大多是在下面几者之间做平衡：

```text
latency vs throughput vs GPU memory vs cost
```

## 第一个实验

用 vLLM 运行一个模型并记录：

| prompt 类型 | 并发 | max tokens | TTFT | TPOT | 总延迟 |
|---|---:|---:|---:|---:|---:|
| 短 prompt | 1 | 128 | TBD | TBD | TBD |
| 长 prompt | 1 | 128 | TBD | TBD | TBD |
| 短 prompt | 10 | 128 | TBD | TBD | TBD |
| 长 prompt | 10 | 128 | TBD | TBD | TBD |