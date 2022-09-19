---
title: Functions
description:
category: docs
---

# Functions

Blockless Functions is a decentralized serverless platform for creating functions that respond to on-chain and cloud events. Functions are lightweight programs that take a short period to execute, and they can work individually or in conjunction with other functions. 

Functions can be deployed to a fully-customizable service environment that consists of an arbitrary number of worker instances, assembling a function-specific subnetwork or shard. The subnetwork can also be dynamically load-balanced with varying incoming load.

## Language Support

A Function can be written in numerous supported programming languages. Currently, we support [TinyGo](https://tinygo.org) (a lite version of Go designed for WebAssembly), Rust, [AssemblyScript](https://www.assemblyscript.org/) (a variation of TypeScript designed for WebAssembly), C, and C++. We are actively adding more language support along the way. 

## Blockless SDK

For each supported programming language, we provide a SDK to enhance the development experience. Currently, the APIs in the Blockless SDK include: 

- HTTP
- Blockless Functions (allowing developers to invoke other Functions without having to send HTTP requests with authentication credentials over the internet)
- AWS S3
- IPFS
- Ethereum

For a full list of Blockless officially integrated APIs, please visit [Reference page](../reference/index.md).


## Function Configuration

The configuration of a Function is declared in a manifest file in JSON or YMAL format. 

The manifest contains the following information:

- **resources**: The upper limits of the execution resources the Function can utilize, including:

  - CPU - [0, 100], representing 0-100% of the CPU load
  - Memory - [0, 4096], representing megabytes (MiB)

  {% callout %}
  The upper resource limits declared in the manifest are only used for matching Nodes suitable to deploy the Function, and not used for billing.
  {% /callout %}

- **public**: A boolean variable declaring whether the function is public or private. See [Function Types](./types.md) for more information.

- **deployment**: How the Function is deployed.
- **extensions**: What Extensions are used and their specifications.

A sample manifest file may look like this:

```json
{
  "resources": {
    "processing": 100,
    "memory": 50,
    "storage": 10
  },
  "public": false,
  "deployment": {
    "method": "decentralized",
    "aggregation": "foundation/average"
  },
  "extensions": {
    "eth": "",
    "ipfs": "",
    "HTTP": "https://blockless.network/"
  }
}
```

## Packaging a Function

Your function source will be compiled to a WASI executable (binary format). Then, along with the function manifest, your function bundle will be uploaded to the IPFS for storage. You can also directly upload a pre-compiled WASI executable.

Upon deployment, designated worker(s) will retrieve the executable bundle and run the executable for execution.

## Function Deployment

Simply click “deploy” button and your function will be deployed to the Blockless network. 

- If the Coordinator receives a codebase, the Coordinator packages and proceeds; if the Coordinator receives a deployable package (e.g. from the Blockless CLI), the Coordinator proceeds directly.
- The Coordinator stores the deployable package.
- The Coordinator tries to match suitable Nodes to send the deployable package.
	While trying to match, the status of the Function stays at Pending Deployment.
- Suitable Nodes receive the information about the Function and download the deployable package.
- The Nodes fire up instances of Functions Runtime Environment with the deployable packages.
	At this stage, the Function’s status is Deployed. The Coordinators can direct requests to the Nodes now.

## Un-deploying a Function

To un-deploy a function, simply click the “stop” button and the function will be killed and deleted from all assigned Worker instances. Your function bundle will still exist in IPFS if you want to re-deploy it again. If you want to full remove your function from IPFS, you need to remove your function.

## Removing a Function

If you want to un-deploy a function, simply click the “stop” button and the function will be deleted from all assigned Worker instances. However, your function bundle will still exist in IPFS if you want to re-deploy it again.

To fully remove a function, un-deploy the function first, then click the “remove” button. This way, your function bundle will be fully deleted from the Blockless system, as well as the IPFS. To re-deploy, you’ll have to upload your function again.

## Invoking a Function

There are two ways to invoke a Function:

1. calling the suitable API from the Functions SDK.
2. sending a HTTP request to a Blockless Network Gateway endpoint (e.g. `https://function-name.functions.organization-name.bls.dev`) with appropriate authentication credentials.

Invoking a Function incurs a fee. See [Billing](../account/billing.md) for more details.
