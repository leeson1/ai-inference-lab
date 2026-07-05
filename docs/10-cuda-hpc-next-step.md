# CUDA / HPC Next Step

## Positioning

CUDA and HPC are the long-term moat, not the first job-switching entry point.

The recommended order:

```text
LLM serving -> inference performance -> CUDA/HPC
```

## CUDA Foundation

Learn:

- thread / block / grid
- warp
- global memory
- shared memory
- register memory
- coalesced memory access
- occupancy
- streams
- events

## Labs

- vector add
- matrix transpose
- reduction
- naive GEMM

## Profiling

Use:

- Nsight Systems
- Nsight Compute

Questions:

1. Is the kernel memory-bound or compute-bound?
2. Are memory accesses coalesced?
3. Is shared memory used correctly?
4. Is occupancy reasonable?
5. Is the bottleneck kernel execution, memory copy, or synchronization?

## HPC Expansion

After CUDA basics:

- Triton
- CUTLASS
- NCCL
- RDMA concepts
- InfiniBand concepts
- Slurm
- Kubernetes GPU scheduling
- distributed inference

## Warning

Do not spend months only writing toy CUDA kernels before building the inference gateway. The gateway is the job-switching project; CUDA is the long-term depth path.
