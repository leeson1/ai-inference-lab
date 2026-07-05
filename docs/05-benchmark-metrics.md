# Benchmark 指标

## 目标

养成用测量理解推理系统的习惯，而不是只读文档。

## 核心指标

### TTFT

Time To First Token。

衡量客户端收到第一个生成 token 之前需要等待多久。

它对用户感知到的响应速度非常重要。

### TPOT

Time Per Output Token。

衡量首 token 之后的 decode 速度。

它对长回答体验非常重要。

### 总延迟

一次请求从开始到结束的端到端耗时。

### 吞吐

常见形式：

- requests per second
- output tokens per second
- total tokens per second

### P50 / P95 / P99

延迟分位数指标。

在生产系统中，P95/P99 通常比平均延迟更重要。

### GPU 指标

- GPU 利用率
- GPU 已用显存
- GPU 空闲显存
- 功耗
- 温度
- 使用 Nsight profiling 时关注 SM occupancy

## 负载维度

benchmark 必须改变这些维度：

- prompt 长度
- 输出长度
- 并发
- 模型规模
- 后端系统
- stream vs non-stream

## 第一批 Benchmark Case

| case | prompt | 输出 | 并发 |
|---|---|---:|---:|
| short-prompt-low-concurrency | 短 | 128 | 1 |
| short-prompt-high-concurrency | 短 | 128 | 20 |
| long-prompt-low-concurrency | 长 | 128 | 1 |
| long-prompt-high-concurrency | 长 | 128 | 20 |
| long-output | 短 | 1024 | 5 |
| mixed-workload | 混合 | 混合 | 20 |

## 报告模板

```md
# Benchmark 报告

## 环境

- GPU:
- Driver:
- CUDA:
- Model:
- Backend:
- Command:

## 结果

| case | concurrency | max tokens | TTFT p50 | TTFT p95 | TPOT p50 | total p95 | output tok/s |
|---|---:|---:|---:|---:|---:|---:|---:|

## 观察

## 瓶颈猜测

## 下一个实验
```