---
title: Network
description: 
category: docs
---

# Network

## Is the Blockless network a blockchain?

In short, the Blockless network is not a blockchain. The core of Blockless is the WASM-based worker layer where the actual execution (computation) happens. However, there is a Cosmos-based blockchain within the Blockless architecture that handles work orchestration and user credentials. 

## Is the Blockless network a P2P network?

Yes, Blockless is a multi-layered P2P network.

## How does P2P work in the Blockless network?

Blockless has 2 layers of the P2P network. 

The first layer is the Cosmos-based Orchestration Chain, which is a static P2P network with known Orchestrators to seed and secure the blockchain network.

The second layer is the Worker Layer, which uses the Orchestration Chain to strap dynamic discovery. Some Workers are assigned to be the Head Workers and register the discovery details. The rest of the Workers can join the P2P network on-demand and coordinate payload execution and computation.

## What is an Orchestrator?

An Orchestrator services the Blockless Orchestration Chain 24/7 and orchestrates the incoming function deployment to the individual workers.

## What is a Worker?

A worker is individual network-contributing hardware that executes the function payload. When a function is invoked, the designated worker boots up a WASM-based secure runtime environment and executes the function. After the function is executed, the worker reports the result and shuts down the runtime environment.

## Where does computation take place on the Blockless Network?

The computation takes place at the worker layer and in the specific workers’ WASM-based secure runtime environment.

## How is the network latency?

Currently, the network latency is around 50ms-200ms, sufficient enough for nearly all implementation scenarios. 

Over time, with more Workers joining the network, we will be able to assemble a more robust and wide-reaching edge network. This will help us to continue reducing the network latency and eventually surpass the current centralized competitors with 0-20ms latency. 

Our goal is to have enough Workers in the network powering sub-millisecond latency for major demographic centers.

## Is Blockless more reliable than centralized web service?

There are many definitions for reliability, but in general, as a decentralized system, Blockless is more resilient to single points of failure and centralization risks. 

All of the deployments running on Blockless will be deployed to multiple Workers. Our orchestration algorithm also prioritizes Workers that are not located in the same geographic or network region (e.g. multiple Workers in the same server cluster). Although very unlikely, in the case when all Workers in one particular deployment’s sub-network are down, Blockless automatically redeploys the work to other available workers in the network.

For security-related issues, you can find more answers in the security subcategory in the FAQ.

## What is WASM?
WASM is an abbreviation for WebAssembly. It is a low-level programming language that is designed to be a portable, size-efficient, and fast format for executing code on the web. It is typically used as a compilation target for high-level languages such as C, C++, or Rust, allowing developers to write complex applications that can run in web browsers at near-native speeds. WASM is supported by most modern web browsers, and is an important part of the web platform, enabling developers to build fast, complex, and powerful web applications.

## Why use WASM instead of Docker?

WASM has many native advantages over Docker or virtual machines.

1. WASM supports multiple programming languages natively. The developer user can stick with their favorite language without needing to learn anything new. Different language modules can also work seamlessly with each other, without additional APIs.
2. WASM is currently the most portable solution in the industry, allowing Network Contributors to install Blockless worker software onto small IoT devices. Traditional server cluster manager can still adopt their old workflow and will work with the Blockless system.
3. WASM is very secure. The runtime has an extensive security and permission system in protecting the Network Contributors and the Developer.
4. WASM is extendible. New hardware or software can be extended to the runtime environment, allowing more diverse use cases. This is very hard in the traditional Docker or VM.

## What is a Zero-Knowledge Proof?
ZKPs are a type of cryptographic protocol that allows one party (the prover) to prove to another party (the verifier) that they possess certain knowledge or information, without actually revealing the knowledge or information itself. This is achieved by allowing the prover to generate a mathematical proof that shows that they know the required information, without revealing the underlying data. ZKPs have a number of potential applications in various fields, including finance, cryptography, and computer science.

## What is zkWASM?
zkWASM is a technology that allows for the efficient execution of zero-knowledge proofs (ZKPs) on the WebAssembly (WASM) platform. WASM is a binary instruction format for a stack-based virtual machine that is designed to be fast, portable, and efficient. zkWASM is a WASM-based implementation of ZKPs that allows for the efficient execution of ZKPs on the WASM platform, which can be useful for a variety of applications in the decentralized space.

## Why Blockless chose to execute ZKPs on WASM?
By allowing for the efficient execution of ZKPs on the WASM platform, zkWASM can help to improve the performance and scalability of decentralized applications (dApps) that use ZKPs. This can be particularly useful for applications that require the frequent execution of ZKPs, such as applications that involve the transfer of digital assets or the verification of computations. Overall, zkWASM is a technology that can help to improve the performance and efficiency of ZKP-based applications on the web3 platform, and it is likely to play a significant role in the future of decentralized technology and the broader Web3 ecosystem.

## What is serverless?
Serverless is a cloud-native development model that allows developers to build and run applications without having to manage servers.

## Why does serverless computing matter?
Serverless is a hot topic these days. This term has been gaining popularity over the last several years, and it doesn't seem to be slowing down anytime soon. It eliminates the "where" from software deployment, to put it in the simplest terms.

There has been a serverless movement in Web2 that introduced the tech world to many benefits. Developers no longer have to consider infrastructure scaling when designing applications, so they can spend more time building out the business logic. 

Web3, however, is yet to enjoy such benefits. 

As we move into a more mature Web3 where teams are building more complex business logic, we are forced to move executions off blockchains. We are now seeing hundreds of teams building out independent, community-based p2p node networks to perform executions. 

Teams experience a number of problems in this process: 
1. High capital cost in building out a battle-ready p2p layer.
2. High community maintenance, distracting teams from leveraging their expertise.
3. Individual nodes are often paid consistently regardless of execution workload, diluting project token value. 
4. Individual community networks are often not decentralized or stable enough.
5. The size of the communities limits service scaling. Cannot adapt to a sudden influx of requests. 

## Why go serverless?

Easier

A serverless model may be ideal for your application. If you need to swiftly deploy an application, serverless may be your best option. Instead of weeks or months, it is possible to launch an application within hours or days. The reason for this is that you do not need to worry about infrastructure. You may concentrate on the code and instantly release it. Scalability is automatic, and provisioning requirements are not a concern.

Cheaper
Going serverless is an excellent way to reduce costs. This is because you outsource the management of your servers, databases, and some logic. In addition to cost, serverless computing requires less processing power and fewer human resources. There is no need for you to establish your own server from scratch. Since serverless handles the infrastructure, you can concentrate on the important server-side code. Depending on your use case, there may be circumstances when the cost is not much lower.

Better scalable
If you want to become the next Google, you should examine if your server can take such a load. Choosing a serverless architecture enables you to be adaptable. If your software is successful and grows, it will be easy to make changes to keep up with the growth. Otherwise, no damage done! There is no need to create infrastructure before determining its need. 

Lower latency

Typically, serverless systems have global access points. This implies it will be simpler to manage visitors from all around the globe. Thus, you may grow your application without sacrificing performance. Imagine, for example, that you host a server in the normal way on the West Coast. If a user from the East Coast uses your application, they must make a request across the full distance and back. For a serverless design, it would only reach the nearest serverless node, which may be on the West Coast! The only possible drawback is cold starts, which is the time required for an application to be created and deployed in a container.

Sustainable

Companies that run their own data centers or servers must make sure that their servers are always up and running. Consider all the enormous data centers and the physical resources required to construct them. Consider the energy required to keep them operating. The advantage of serverless architecture is the ability to purchase servers on demand. This may lower the number of resources required to keep several businesses online.

Flexible

With serverless, it is simpler to begin the implementation of an application than with conventional approaches. Consequently, adopting serverless enables you to develop more rapidly. When you see instant, concrete results, you may go on to the next task. You may begin developing your next feature or microservice. This advantage is provided by serverless architecture when there are no limits. It is also simpler to pivot in circumstances requiring reorganization.

More efficient

A serverless design results in per-request billing. If you had a conventional server, you would always have it working. A serverless architecture charges only when the server is used. It is also more efficient since scalability is no longer an issue. Infrastructure, configuration, capacity planning, and DevOps no longer bother you.
