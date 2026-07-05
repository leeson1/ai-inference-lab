# System Design Q&A

## Q1: How would you design an LLM inference gateway?

Core modules:

- API router
- provider abstraction
- model routing
- stream forwarding
- timeout and cancellation
- rate limiting
- request queue
- metrics
- token accounting
- admin/config management

## Q2: How do you protect inference backends from overload?

Use:

- max in-flight requests
- queue length limit
- per-model concurrency limit
- per-user rate limit
- timeout and cancellation
- circuit breaker
- fallback model or rejection strategy

## Q3: What metrics should be exposed?

- request count
- error count
- in-flight requests
- queue size
- TTFT
- TPOT
- total latency
- input tokens
- output tokens
- backend latency
- model-level throughput

## Q4: How would you support model gray release?

Use routing rules:

- model alias points to versioned backends
- percentage-based traffic split
- user whitelist
- rollback by changing route config
- compare metrics between old and new model

## Q5: How would you handle streaming responses?

The gateway should forward Server-Sent Events or chunked responses without buffering the entire output. It must handle client disconnect, backend cancellation, timeout, and metrics finalization.
