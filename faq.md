---
title: FAQ
description: 
category: docs
---

# FAQ

## General

### Why do you need Blockless?

    
    To build the next-generation decentralized applications, you need more than just a distributed blockchain ledger. Oftentimes, your application requires high-performance computation, data IO from/to IPFS, various blockchains, managed databases, and integration with various Web2 and Web3 services.

    Blockless helps with your decentralized application development process in 3 major ways. 
    
    1. With Blockless Functions and Blockless App Engine (coming Q1 2023), you can offload the heavy computation from a blockchain or centralized cloud service platform to the Blockless decentralized node network.

    2. You can access your familiar Web2 and Web3 services through Blockless SDK. Blockless supports IPFS, AWS S3, Ethereum, BNB Chain (Q4 2022), and Cosmos (Q4 2022). The platform will add more service support every month down the road.

    3. With Blockless Marketplace, you can use and integrate community functions and extensions into your own application architecture in a plug-and-play fashion. You can also sell and distribute your function to the community for profit.

### Who are Blockless network's users?
    
    Blockless is a decentralized web service platform serving two groups of users: one being our network contributors who contribute their idle computing resources in exchange for token and service fee incentives, and the other being the developers who seek distributed, decentralized, and affordable web services.
    
### What makes Blockless different?
    
    Blockless is designed with security and a UX/DX (user experience/developer experience) first principle. 
    
    Under the hood, the Blockless execution engine is a WASM/WASI-based secure runtime (sandbox) that allows for fine-grained control over various system hardware and file systems. It also enables the Blockless network to be truly multi-platform (as small as an IoT device to a full-fledged server cluster) and expandable through community-driven extensions. 
    
    In addition, the system incorporates a Cosmos-based orchestration chain that handles work orchestration and load balancing. This way, all functions and applications are dispatched automatically without the developer and network contributor needing to be interfaced with each other.
    
    For developers and network contributors, the Blockless network can be accessed via both Command Line Interface (CLI) and Graphical User Interface (GUI), providing the best-in-class system interaction flow. The Node software can be automatically installed onto the host machine, without the user ever needing to decipher the CLI commands.

### Is Blockless cheaper than a centralized web service platform?

    Yes. Currently, Blockless’ service fee will be competitive with the centralized counterparts. As the network recruits more idle resources, the price will gradually go down even more as these resources have previously been neglected. 
    
### Will there be a token?

    Yes. BLS is the official token of the Blockless network. It will be used for all in-network transactions.

### 4. Where can I find more information?

    - [Twitter](https://twitter.com/theblockless)

    - [Medium](https://blockless.medium.com)

    - [Telegram](https://t.me/blocklessofficial)

    - [Discord](https://discord.gg/9eeRHxSCTZ)


## Network

### Is the Blockless network a blockchain?
    
    In short, the Blockless network is not a blockchain. The core of Blockless is the WASM-based worker layer where the actual execution (computation) happens. However, there is a Cosmos-based blockchain within the Blockless architecture that handles work orchestration and user credentials.  
    
### Is the Blockless network a P2P network?
    
    Yes, Blockless is a multi-layered P2P network.
    
### How does P2P work in the Blockless network?
    
    Blockless has 2 layers of the P2P network. 
    
    The first layer is the Cosmos-based Orchestration Chain, which is a static P2P network with known Orchestrators to seed and secure the blockchain network.
    
    The second layer is the Worker Layer, which uses the Orchestration Chain to strap dynamic discovery. Some Workers are assigned as the Head Workers and register discovery details. The rest of the Workers can join the P2P network on-demand and coordinate payload execution and computation.
    
### What is an Orchestrator?
    
    An Orchestrator serves the Blockless Orchestration Chain 24/7 and orchestrates incoming function deployment to individual workers.
    
### What is a Worker?
    
    A worker is individual network-contributing hardware that executes the function payload. When a function is invoked, the designated worker boots up a WASM-based secure runtime environment and executes the function. After the function is executed, the worker reports the result and shuts down the runtime environment.
    
### Where does computation take place on the Blockless Network?
    
    The computation takes place at the worker layer and in the specific workers’ WASM-based secure runtime environment.
    
### What is the network latency? 

    Currently, the network latency is around 50ms-200ms, sufficient enough for nearly all implementation scenarios.

    Over time, with more Workers joining the network, we will be able to assemble a more robust and wide-reaching edge network. This will help us to continue reducing the network latency and eventually surpass the current centralized competitors with a 0-20ms latency. 

    Our goal is to have enough Workers in the network powering sub-millisecond latency for major demographic centers.

### Is Blockless more reliable than centralized web service?

    There are many dimensions to reliability, but in general, as a decentralized system, Blockless is more resilient to single points of failure and centralization risks. 

    All deployments running on Blockless will be deployed to multiple Workers. Our orchestration algorithm also prioritizes Workers that are not located in the same geographic or network region (e.g. multiple Workers in the same server cluster). Although very unlikely, in the case when all Workers in one particular deployment’s sub-network are down, Blockless automatically redeploys the work to other available workers in the network.

    For security-related questions, you can find more in the security subcategory of the FAQ.

    
### Why using WASM instead of Docker?

    WASM has many native advantages over Docker or virtual machines.

    1.  WASM supports multiple programming languages natively. Developers can stick with their favorite language without needing to learn anything new. Modules in different languages can also work seamlessly with each other, without additional APIs.

    2.  WASM is currently the most portable solution in the industry, allowing Network Contributors to install Blockless worker software onto even small IoT devices. Traditional server cluster manager can still adopt their old workflow and will work with the Blockless system.

    3.  WASM is very secure. The runtime has an extensive security and permission system in protecting Network Contributors and Developers.

    4.  WASM is extendible. New hardware or software can be extended to the runtime environment, allowing more diverse use cases. This is very hard to achieve in traditional Docker or VM.


## Security

### How does Blockless guarantee the security of the code that is running in the Blockless runtime environment?

    All functions are pre-compiled into WASI executable (byte code) locally before being uploaded to IPFS for storage and ultimately deployment. This means that no actual function code can be accessible to the network contributor.

    Additionally, all secrets, including private keys are callable via environment variables and are encrypted during the P2P communication. The secrets are decrypted inside the runtime environment and live in the node contributor’s memory. Blockless cannot prevent the decrypted secrets from being discovered in memory, although the chances for such an operation to succeed are extremely low. In future updates, we will introduce delegated signing to eliminate the chance of memory hacking.

### Is user data secure?

    Since Blockless doesn't require conventional identities to create an account, minimum user data is collected. The collected user data is either stored on the immutable Orchestration Chain or stored under industry-standard isolation and encryption, AES256-CBC.

    User data is further secured by random one-time and time-limited messages that must be verified locally by a user’s private key.

### How is Blockless’ peer-to-peer worker layer secured and how does Blockless mitigate man-in-the-middle attacks?

    The Blockless peer-to-peer worker layer (network) is secured via TLS encryption. As the networking module is built upon LibP2P, we also inherit the majority of the security parameters from the open-sourced framework.

    For orchestrator-worker communication, we use cryptographic identities to ensure a secure point of contact.

    For request handling, execution, and response on the Blockless Workers, however, man-in-the-middle attacks (MITM) are hard to mitigate. We believe a network contributor should be allowed to employ performance-enhancing technologies and layered proxies to get the most out of his topology, but this does leave opportunities for potential vulnerabilities. Additionally, we always assume the decentralized Workers are prone to compromise, so Blockless employs two novel designs, **Optimistically Trusted Workers** and **Worker Pinning** to mitigate MITM risks. 

    In the production scenario, self-signed certificates are not a problem as the system does not accept them for anything other than MTLS (two-way client communication). Nonetheless, our HTTP Extension does require proper authority on calls, and someone can potentially use a malicious certificate in this scenario. In this case, the developer can pin a trusted Head Worker to always handle and distribute incoming requests. The trust, nonetheless, is established on the fact that all Head Workers’ work records can be openly audited and disputed. Any malicious Head Worker’s stake will be slashed. 

    Going deeper into the technicality, your Function binary encodes the certificate into the WASM file and ensures it matches the server you call to (typically found in mobile environments today). The network will SUM hash your binary during the deployment process, and then the Worker checks the sum is correct before execution.

    With **Optimistically Trusted Workers,** **Worker Pinning,** and off-chain consensus (off-chain aggregation and/or zk-SNARK proofs), the system will be able to detect MITM attacks and respond to them appropriately.

### What are the considerations for the security and decentralization of the orchestration process?

    Currently, the security and decentralization of the orchestration process rely on identifying geographic and IP clustering of the Worker subnetwork. This way, we ensure that the Workers serving your application are not located predominantly in the same server cluster (e.g. the same AWS or Google Cloud data center) or geo-location.

    The Blockless team is actively monitoring additional attributes that can cause security and decentralization concerns. These attributes will be addressed vigilantly to ensure the overall security level of the network.


## Functions

### Where do Functions exist on the Blockless Network?
    
    Functions are compiled into the WASI binary bundle and uploaded to IPFS. They are executed within Workers’ WASM-based secure runtime environment.

## Account and Billing

### How do I access my account?
    
    You can access your account using a supported Web3 wallet and address. Currently, your address is only used for credentials and not used for billing. We support Metamask, Keplr Wallet (Cosmos), and Martian Wallet (Aptos).
    
### How do I pay for my functions’ service fee?
    
    Currently, billing is disabled in the Private Alpha release. All function deployment is free with a 15min max execution time per invocation.
    
### Where does the service fee go?
    
    The majority of the service fees will be given to the worker who provided the execution service. Portions of the service fee will be burnt.
