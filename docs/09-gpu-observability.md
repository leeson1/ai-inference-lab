# GPU 可观测性

## 目标

从服务视角和 GPU 视角同时观察推理负载。

## 服务指标

- 请求数
- 错误数
- in-flight 请求数
- 队列大小
- 总延迟
- TTFT
- TPOT
- 输入 token 数
- 输出 token 数
- tokens per second

## GPU 指标

- GPU 利用率
- 已用显存
- 空闲显存
- 功耗
- 温度
- SM 利用率
- 显存带宽

## 工具

- nvidia-smi
- DCGM Exporter
- Prometheus
- Grafana
- Nsight Systems
- Nsight Compute

## 第一目标

从网关暴露 Prometheus 指标，并与 GPU 指标结合起来观察。

## 问题

1. 为什么 GPU 利用率很高，但吞吐仍然可能很差？
2. 为什么显存使用量可能成为限制因素？
3. 如何判断一个负载是 prefill-heavy 还是 decode-heavy？
4. TTFT 和 TPOT 如何映射到服务体验？
5. 哪些指标应该触发扩容或限流？