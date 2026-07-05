# GPU Observability

## Goal

Learn how to observe inference workloads from both service and GPU perspectives.

## Service Metrics

- request count
- error count
- in-flight requests
- queue size
- total latency
- TTFT
- TPOT
- input tokens
- output tokens
- tokens per second

## GPU Metrics

- GPU utilization
- memory used
- memory free
- power usage
- temperature
- SM utilization
- memory bandwidth

## Tools

- nvidia-smi
- DCGM Exporter
- Prometheus
- Grafana
- Nsight Systems
- Nsight Compute

## First Goal

Expose Prometheus metrics from the gateway and combine them with GPU metrics.

## Questions

1. Why can GPU utilization be high but throughput still bad?
2. Why can memory usage be the limiting factor?
3. How do we know whether a workload is prefill-heavy or decode-heavy?
4. How do TTFT and TPOT map to service experience?
5. What metrics should trigger scaling or throttling?
