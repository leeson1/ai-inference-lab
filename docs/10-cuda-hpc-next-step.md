# CUDA / HPC 下一步

## 定位

CUDA 和 HPC 是长期护城河，不是第一阶段转行的入口。

推荐顺序：

```text
LLM Serving -> 推理性能 -> CUDA/HPC
```

## CUDA 基础

需要学习：

- thread / block / grid
- warp
- global memory
- shared memory
- register memory
- coalesced memory access
- occupancy
- streams
- events

## 实验

- vector add
- matrix transpose
- reduction
- naive GEMM

## Profiling

使用：

- Nsight Systems
- Nsight Compute

需要回答的问题：

1. kernel 是 memory-bound 还是 compute-bound？
2. 显存访问是否 coalesced？
3. shared memory 是否使用正确？
4. occupancy 是否合理？
5. 瓶颈是 kernel 执行、memory copy，还是 synchronization？

## HPC 扩展

CUDA 基础之后再扩展：

- Triton
- CUTLASS
- NCCL
- RDMA 概念
- InfiniBand 概念
- Slurm
- Kubernetes GPU 调度
- 分布式推理

## 提醒

不要在构建推理网关之前，花几个月只写玩具 CUDA kernel。网关是转行项目，CUDA 是长期深度方向。