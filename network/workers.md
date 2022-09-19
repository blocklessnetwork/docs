---
title: Workers
description:
category: concepts
---

# Workers

Workers are resource-providing hardwares that execute the assigned Function payload. Given the scale of the network, some workers may be assigned to be the Head Workers and perform secondary work orchestration and request-routing.

## Request Handling and Load Balancing

Head Worker will establish a secure connection directly with the load balancing service when a new request is received, and the request is subsequently routed to the registered Worker. Currently, the load balancing service is running on service providers such as Akash and Flux. We are currently working on incorporating the load balancing service to the Orchestration Chain.

## Worker Types

As a developer, you will not directly interface with the assigned Worker(s) for your Function. However, it is beneficial to note that two types of Workers exist in the Blockless network, Timed Workers and Freelance Workers.

Timed Worker stays in and services the network under a timed service level agreement (SLA) or else it will be penalized. Freelance Worker services the network on a resource-based SLA and can opt in or out of the network freely. Timed Workers are prioritized for function assignment to ensure service quality while Freelance Workers provide redundancy and add robustness to the network.

## Execution Environment

When an assigned Worker receives a Function request, it will boot up the WASM runtime environment and executes the WASI executable. Once the function execution is completed, the runtime environment is terminated.