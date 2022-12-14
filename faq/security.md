---
title: Security
description: 
category: docs
---

# Security

## How does Blockless guarantee the security of the code that is running in the Blockless runtime environment?

All of the Functions are pre-compiled into WASI executable (byte code) locally before uploading them to the IPFS for storage and ultimately deployment. This means that no actual function code can be accessible to the network contributor.

Additionally, all secrets, including private keys are callable via environment variables and are encrypted during the P2P communication. The secrets are decrypted inside the runtime environment and live in the node contributor’s memory. Blockless cannot prevent the decrypted secrets from being discovered in memory, although the chances of such an operation are extremely unlikely. In the next iteration of the Blockless updates, we will introduce delegated signing to eliminate the chance of memory hacking.

## Is user data secure?

Since Blockless doesn't require conventional identities to create an account, minimum user data is collected. The collected user data is either stored on the Orchestration Chain, which is immutable, or stored under industry-standard isolation and encryption, AES256-CBC.

The user data is further secured by random one-time and time-limited messages that must be verified locally by a user’s private key.

## How is Blockless’ peer-to-peer worker layer secured and how does Blockless mitigate man-in-the-middle attacks?

The Blockless peer-to-peer worker layer (network) is secured via TLS encryption. As the networking module is built upon LibP2P, we also inherit the majority of the security parameters from the open-sourced framework.

For orchestrator-worker communication, we use cryptographic identities to ensure a secure point of contact. 

For request handling, execution, and response on the Blockless Workers, however, man-in-the-middle attacks (MITM) are hard to mitigate. We believe a network contributor should be allowed to employ performance-enhancing technologies and layered proxies to get the most out of his topology, but this does leave opportunities for potential vulnerabilities. Additionally, we always assume the decentralized Workers are prone to compromise, so Blockless employs two novel designs, **Optimistically Trusted Workers** and **Worker Pinning** to mitigate MITM risks. 

In the production scenario, self-signed certificates are not a problem as the system does not accept them for anything other than MTLS (two-way client communication). Nonetheless, our HTTP Extension does require proper authority on calls, and someone can potentially use a malicious certificate in this scenario. In this case, the developer can **pin** a trusted Head Worker to always handle and distribute incoming requests. The trust, nonetheless, is established on the fact that all Head Workers’ work records can be openly audited and disputed. Any malicious Head Worker’s stake will be slashed. 

Going deeper into the technicality, your Function binary encodes the certificate into the WASM file, and ensures it matches the server you call to (typically found in mobile environments today). The network will SUM hash your binary during the deployment process, and then the Worker checks the sum is correct before execution.

With **Optimistically Trusted Workers, Worker Pinning**, and off-chain consensus (off-chain aggregation and/or zero knowledge snark proofs), the system will be able to detect MITM attacks and respond to them appropriately.

## What are the considerations for the security and decentralization of the orchestration process?

Currently, the security and decentralization of the orchestration process rely on identifying geographic and IP clustering of the Worker subnetwork. This way, we ensure that the Workers serving your application are not located predominantly in the same server cluster (e.g. the same AWS or Google Cloud data center) or geo-location.

The core team of Blockless is actively monitoring additional attributes that can cause security and decentralization concerns. These attributes will be addressed vigilantly to ensure the overall security level of the network.

## What kind of development practices are followed internally within the team? 

We utilize Lean Six Sigma principles (LSS) for agile development where it makes sense. Scrum, Backlog, and Prioritization. We utilize a Kanban system with a Kaizen feedback loop.

Our priority cycle is 1 week, with a retarget every Monday. We utilize a more fluid structure for completing work as followed loosely by high-performant integrated teams. Work assignments, goals, and targets are fluid as we move from week to week.

The development process starts with the dev team quoting to the product team based on the PRDs signed off and finishes with testing and deployment. Scrum metrics and KPIs are tracked by the dev team. Release metrics are tracked by the dev and product teams.

## What applications and languages are used for development? 

Rust is used for core runtime environment, app engine, and many of the first party extensions for the runtime. GoLang is used extensively to build the Orchestration Chain and the Worker Layer networks. We also used C to develop wrapper interfaces (dll) to different higher level languages for integration to the Runtime. JavaScript drives almost all user facing experiences, from the Web properties to the CLI. We also used Next JS and Storybook for frontend framework + component management.

## Are there any single points of failure in the system (hard-coded values, private keys held centrally, dependency on a 3rd-party for core functionality)? 

No private keys are stored. Our nodes generate new keys for the owner, those keys are retained by the owner. Under the current topology, the Orchestration Chain will be the identity and security layer for the Worker Layer and User interaction.

## What are the benchmarks on transaction times, latencies, costs of transaction, throughput, etc.? 

Currently, the average response time is around 20ms. Our Worker Layer’s networking module is based on libP2P, with our own stream configuration for our channels. This means that the network’s theoretical upper bound is libP2P’s performance upper bound. Here is some reading about the improvements overtime that have happened with libP2P streams. https://research.protocol.ai/blog/2020/honey-i-shrunk-our-libp2p-streams

## What are Minimum Specification Considerations for Blockless?

**Blockchain Validator and Sentry Nodes**

- When enabled CosmWasm will require the minimum validator configuration

- CPU 3.5Ghz , Gen 5 Intel or later , High TDP 100W or greater

- 64 GB DDR4

- NVMe 2Tb of high speed (5000 MB/s write recommended)

**Execution Network Head Node**
- CPUs for Head Nodes are Currently not Subject to Benchmarking, so these specs can be a little lower while we work through Dev Net and Alpha
- Minimum CPU 3.5Ghz (2 fulltime vCPUS) + 4 GB RAM HDD ~500Gb (we don’t have a perm storage option yet)

**Execution network Worker Node**
- Execution Worker Nodes Need more Memory than CPU to accomplish appropriate throughput for P2P communication and execution. It is recommended to have 2x the RAM as the CPU starting with 0.5 vCPU, you should have 1GB Ram.
- HDD 500 Gb until perm storage.
- A typical 4 Core Processor with Hyper-threading Yields 8vCPUs, and should have a minimum of 16Gb of RAM to ensure enough IO availability for processes running on that machine.
- The worker will dynamically report back the amount of work that is available, based on the CPU scheduling.


