# 系统设计面试问答

## Q1：你会如何设计一个 LLM 推理网关？

核心模块：

- API router
- provider 抽象
- 模型路由
- 流式转发
- 超时与取消
- 限流
- 请求队列
- 指标
- token 统计
- admin/config 管理

## Q2：如何保护推理后端避免过载？

可以使用：

- 最大 in-flight 请求数
- 队列长度限制
- 每个模型的并发限制
- 每个用户的 rate limit
- 超时与取消
- circuit breaker
- fallback model 或拒绝策略

## Q3：应该暴露哪些指标？

- 请求数
- 错误数
- in-flight 请求数
- 队列大小
- TTFT
- TPOT
- 总延迟
- 输入 token 数
- 输出 token 数
- 后端延迟
- 模型级吞吐

## Q4：如何支持模型灰度发布？

使用路由规则：

- model alias 指向带版本的后端
- 按百分比分流
- 用户白名单
- 通过修改路由配置回滚
- 对比新旧模型的指标

## Q5：如何处理流式响应？

网关应该转发 Server-Sent Events 或 chunked response，不要等完整输出生成后再一次性返回。它必须处理客户端断开、后端取消、超时和指标收尾。