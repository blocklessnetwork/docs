---
title: Runtime Environment
description:
category: concepts
---

# Blockless Runtime Environment

The Blockless Runtime Environment is a WASM-based secure sandbox that inherits and expands on the WASM's native features. Some of the characteristics of the Blockless Runtime Environment are of the following:

- **Efficient**: The Blockless Runtime Environment is optimized for efficient instantiation, low-overhead transitions between the embedder and wasm, and scalability of concurrent instances.
- **Secure**: Blockless Runtime Environment is sandboxed by design. Developers must declare all needed functionalities (such as CPU, memory, and file system usage) and extensions beforehand, preventing any unwanted exploitations on the host machine. Memory is also isolated between each runtime instance. Additionally, the safe Rust API is intended to mitigate accidental bugs in hosts.
- **Extensible**: Blockless Runtime Environment can be extended via community-built Extensions, providing new functionalities and hardware access for the Developers.
- **Multi-Language Support:** Blockless Runtime Environment is designed with extensibility in mind. The Runtime Environment can run WASI bytecode bundles compiled from Rust, AssemblyScript, TinyGo, and C/C++. The team is actively adding more programming languages along the project development. The runtime environment also supports the mixing of the aforementioned languages. For example, using Rust to implement a JavaScript API.
- **Cross-Platform Compatibility**: Blockless Runtime Environment can be run in tiny environments all the way up to massive servers with many concurrent instances.