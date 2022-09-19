---
title: Network
description:
category: concepts
---

# Blockless Network

The Blockless network consists of two layers, the worker layer and the orchestration chain. 

![Blockless Network Layers](/images/network-overview/blockless-network-layers.png)

The worker layer is where the functions and applications are executed. For each worker, a WASM-based runtime environment is boot up when the function is invoked. Some workers may be assigned to be head nodes handling additional work orchestration tasks.

The orchestration chain is a Cosmos-based blockchain responsible for function/app registration, work orchestration, load balancing, and identity services. The orchestration chain is maintained by orchestrators running 24/7 around the globe.
