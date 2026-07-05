# AI Inference Interview Q&A

## Q1: What is TTFT?

TTFT means Time To First Token. It measures how long the client waits before receiving the first generated token.

## Q2: What is TPOT?

TPOT means Time Per Output Token. It measures the average decode time for generated tokens after the first token.

## Q3: What is KV Cache?

KV Cache stores key/value tensors from previous tokens during autoregressive decoding. It avoids recomputing attention history but consumes large GPU memory.

## Q4: What is the difference between prefill and decode?

Prefill processes the input prompt and builds KV Cache. Decode generates tokens one by one using the existing KV Cache.

## Q5: Why does batching improve throughput?

Batching improves GPU utilization by processing multiple requests together. However, larger batches may increase per-request latency.

## Q6: What is PagedAttention?

PagedAttention is a KV Cache memory management technique inspired by OS paging. It partitions KV Cache into blocks to reduce memory waste and support flexible sharing.

## Q7: Why do long-context requests reduce concurrency?

Long-context requests require larger KV Cache, consuming more GPU memory and reducing the number of requests that can be served concurrently.

## Q8: What should an inference gateway do?

An inference gateway should provide routing, streaming forwarding, timeout control, rate limiting, metrics, token accounting, and backend protection.
