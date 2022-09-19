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

## Why use WASM instead of Docker?

WASM has many native advantages over Docker or virtual machines.

1. WASM supports multiple programming languages natively. The developer user can stick with their favorite language without needing to learn anything new. Different language modules can also work seamlessly with each other, without additional APIs.
2. WASM is currently the most portable solution in the industry, allowing Network Contributors to install Blockless worker software onto small IoT devices. Traditional server cluster manager can still adopt their old workflow and will work with the Blockless system.
3. WASM is very secure. The runtime has an extensive security and permission system in protecting the Network Contributors and the Developer.
4. WASM is extendible. New hardware or software can be extended to the runtime environment, allowing more diverse use cases. This is very hard in the traditional Docker or VM.