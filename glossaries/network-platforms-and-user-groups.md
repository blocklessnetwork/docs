---
title: Network, Platforms, and User Groups Glossaries
description:
category: reference
---

# Network, Platforms, and User Groups Glossaries

## Network Glossaries

| Term | Definition |
| --- | --- |
| Blockless | Brand Name. A decentralized web service platform serving and facilitating exchanges between (1) the Developer and (2) the Network Contributor. |
| Blockless Network | A protocol composed of two layers and various participating parties. The two layers are: the Blockless Orchestration Chain and the Blockless Worker Layer. The participating parties are: Workers and Orchestrators that conform to the Blockless Network. |
| Blockless Orchestration Chain | One of the two Blockless Network layers handling work deployments. The Orchestration Chain is a Cosmos-based and IBC compatible blockchain validated by a group of Orchestrators. |
| Blockless Worker Layer | One of the two Blockless Network layers handling work execution. The worker layer is a Peer-to-Peer network with each Worker executes work deployments in the WASM-based runtime environment. |
| Worker | A device in the Blockless Network contributing its hardware resources by performing computation, data storage, etc. in exchange for token rewards. |
| Head Worker | A subset of Worker performing network-related tasks including secondary work orchestration and direct request handling. Each Head Worker takes charge (stores a record including hardware specs, load, availability, etc) of a group of Workers. The Head Worker also establishes a direct connection with the load balancing service. |
| Orchestrator | A device in the Blockless Network orchestrating Workers. The orchestrator receives work deployment transaction sent from the developer and dispatch the work to one or more Head Workers for secondary work orchestration. |

## Platform Glossaries (Developer)

| Term | Definition |
| --- | --- |
| Blockless Platform | User interfacing platforms that directly belong to the Blockless brand such as Blockless Functions and Blockless App Engine, enabled by the Blockless Network. |
| Blockless Functions | Serverless or event-driven computer programs running on Worker when invoked. See Blockless Functions Glossaries for details. |
| Blockless App Engine | A managed environment for full-scale Web3 apps and backends enabled by WASI and running on Worker. |
| Blockless CLI | A command line interface for Developer to build, compile, pack, and test Blockless platform in their development environment (local machine), and validate them for and deploy them to the Blockless Network. |
| Blockless Developer Console | A web graphical user interface or application letting the Developers view and manage their uses of the Blockless platforms. The frontend of the application can be distributed with multiple platforms. The backend of the application connects to the Blockless Network. |
| Blockless Marketplace | A feature that allows the developer to share, distribute, and purchase Blockless Functions. |

## Platform Glossaries (Network Contributor)

| Term | Definition |
| --- | --- |
| Blockless Network Contributor Software | An application (not a person) letting the Network Contributor view and manage their participation on the Blockless network. The software has a version for each supporting environment (Linux CLI, Linux GUI, Windows GUI, macOS GUI, etc.) |

## User Groups Glossaries

| Term | Definition |
| --- | --- |
| Developer | One of the two user groups in the Blockless ecosystem, developers of computer applications. |
| Network Contributor | One of the two user groups in the Blockless ecosystem, computing device owners hoping to exchange their computer resources for monetary returns. |
| End User | Be Cautious when using this term as it is overly broad. End user in the Blockless ecosystem means the customer of the Developer and the consumer of the developer‘s application or product. |