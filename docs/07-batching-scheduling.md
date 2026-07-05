# Batching and Scheduling

## Core Idea

LLM serving systems improve GPU utilization by batching multiple requests together.

The challenge is that requests have different prompt lengths, output lengths, arrival times, and priorities.

## Static Batching

Wait for a batch, then process it together.

Problem:

- poor latency for early requests
- inefficient for variable-length outputs

## Continuous Batching

Dynamically add and remove requests while decoding is ongoing.

Benefits:

- better GPU utilization
- higher throughput
- better handling of variable-length requests

Tradeoff:

- more complex scheduler
- latency fairness issues
- long requests can affect short requests

## Scheduling Questions

1. Should short requests have higher priority?
2. Should long prefill requests be separated from decode-heavy requests?
3. Should users have quotas?
4. How should streaming requests be handled?
5. How should timeouts and cancellation affect queued requests?

## Gateway-Level Scheduling

The Go gateway can implement simple policies first:

- max in-flight requests per backend
- max queued requests
- per-model concurrency limit
- per-user rate limit
- timeout and cancellation

## Serving-System-Level Scheduling

vLLM/SGLang/TensorRT-LLM handle deeper GPU-level batching and scheduling.

The gateway should not duplicate GPU scheduler logic, but it should protect the backend from overload.
