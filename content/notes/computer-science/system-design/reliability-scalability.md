---
title: "Reliability and Scalability"
description: "Reliability and Scalability"
tags: []
date: 2018-01-02T02:14:56Z
---

## Reliability

A system should be *resilient* (fault-tolerant) and performant under expected load

Strategies

- design for failure and trigger them deliberately e.g. kill processes without a warning
- consider hardware faults such as blackouts, hard disk crashes, add redundancy as necessary
- consider software faults such as
  - processes that slow down or that return corrupted responses
  - fault cascadig where the a fault triggers faults in other components
- measure/monitor the system to identify faults

## Scalability

### Load

- Queries per second (QPS) to a web server
- Ratio of read/writes in a DB
- Cache hit/miss rate
- # of simultaneous users in a realtime system

#### Approximations for back of the envelope calculations

```text
1 req/s = 80k req/day = 2.5 million req/month
40 req/s = 100 million req/month
```

#### Handling load

- scaling up (vertical scaling), simple
- scaling out (horizontal scaling), complex
- manual scale, for predictable systems, simple
- elastic scale, add resources as load increases, for unpredictable systems, complex

### Performance

- throughput, # requests processed per second
- latency (time to handle the request)
- response time (latency + network/queue delays)

For the response time we use percentiles, given some metrics gathered for a set of requests in a period of time sort them from fastests to slowest, the common metrics are p50, p95, p99, p999 (used in SLAs)

When a requests involves parallel calls to multiple services, the response time is equal to the service which took the maximum time
