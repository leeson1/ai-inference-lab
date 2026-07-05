# Batching 与调度

## 核心思想

LLM Serving 系统通过把多个请求 batch 到一起，提高 GPU 利用率。

难点在于：不同请求的 prompt 长度、输出长度、到达时间和优先级都不一样。

## 静态 Batching

等待凑齐一个 batch，然后一起处理。

问题：

- 早到请求的延迟较差
- 对变长输出不够高效

## Continuous Batching

在 decode 进行过程中，动态加入和移除请求。

收益：

- 更好的 GPU 利用率
- 更高的吞吐
- 更好地处理变长请求

取舍：

- scheduler 更复杂
- 存在延迟公平性问题
- 长请求可能影响短请求

## 调度问题

1. 短请求是否应该有更高优先级？
2. 长 prefill 请求是否应该和 decode-heavy 请求分开？
3. 用户是否应该有 quota？
4. 流式请求应该如何处理？
5. 超时和取消应该如何影响排队请求？

## 网关层调度

Go 网关可以先实现简单策略：

- 每个后端的最大 in-flight 请求数
- 最大排队请求数
- 每个模型的并发限制
- 每个用户的 rate limit
- 超时与取消

## Serving 系统层调度

vLLM/SGLang/TensorRT-LLM 负责更深层的 GPU 级 batching 和调度。

网关不应该重复实现 GPU scheduler 逻辑，但应该保护后端避免过载。