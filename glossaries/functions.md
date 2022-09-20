---
title: Functions Glossaries
description:
category: reference
---

# Functions Glossaries

| Term | Definition |
| --- | --- |
| Blockless Runtime Environment | The WASM-based runtime environment in which Blockless Functions are executed. |
| Blockless SDK | A subset of the broader Blockless Extension system. An official library of computer programs provided in the Blockless Runtime Environment that can be used by the Developers through API calls in their Function program. There is one SDK for each supported programming language. |
| Manifest | A declaration of the Function’s information, including resources needed, permissions needed, extensions needed, deployment configuration, and access control configuration. |
| Resources | Fee-incurring resources from Workers including processing resources, memory resources, and ephemeral storage resources. |
| Processing Resource | The amount of processing resource used, by CPU instructions count or CPU seconds. |
| Memory Resource | The amount of RAM used, in megabytes. |
| Ephemeral Storage Resource | The amount of temporary storage used in megabytes. Accessible at path / that starts as an empty directory and will be purged after the Function finishes its execution. |
| Permissions | Access to sensitive targets that the Blockless Runtime Environment may or may not expose. For example, HTTP access to a specific domain. |
| Extensions | A computer program providing functionalities more than the Blockless SDK already provides by having more access to the Worker’s operating system or system hardware. Network Contributor can choose which Extensions to install and provide to the Blockless Functions. The Blockless platform and Extension Developers trusted by the platform can publish Extensions for Network Contributors to install. |
| Deployment Configuration | Information on how the Blockless network should deploy a Function. |
| Access Control Configuration | Information on who can invoke a Function. |