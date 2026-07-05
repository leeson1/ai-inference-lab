# 量化

## 目标

理解量化作为推理优化技术的作用。

## 为什么需要量化

量化通过使用更低精度的表示，降低显存占用，并可能提升推理吞吐。

常见收益：

- 降低 GPU 显存占用
- 支持更大的 batch size
- 降低带宽压力
- 有时能提升推理速度

常见成本：

- 精度损失
- 校准复杂度
- 后端兼容性问题
- 性能依赖硬件支持

## 常见格式

- FP16
- BF16
- FP8
- INT8
- INT4

## 需要学习的方法

- AWQ
- GPTQ
- SmoothQuant
- weight-only quantization
- KV Cache quantization

## 问题

1. weight quantization 和 activation quantization 有什么区别？
2. 为什么 INT4 能降低显存，但不一定降低延迟？
3. 为什么硬件支持很重要？
4. 什么是 KV Cache quantization？
5. 应该如何评估精度退化？

## 实验计划

用下面两类模型跑同样的 benchmark：

- baseline model
- quantized model

记录：

- GPU 显存占用
- TTFT
- TPOT
- 吞吐
- 回答质量观察