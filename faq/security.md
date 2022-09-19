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