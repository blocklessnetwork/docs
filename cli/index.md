---
title: CLI
description:
category: docs
---

# CLI
The Blockless CLI is a command line tool that makes it easy to interact with the Blockless Network and build and manage your applications. With the Blockless CLI, you can connect to the network via your on-chain identity, construct a local worker environment with one click, and build, test, deploy, and monitor your projects in real time.

# Installation
With `curl`:

```sh
sudo sh -c "curl https://raw.githubusercontent.com/BlocklessNetwork/cli/main/download.sh | bash"
```

Or with `wget`:

```sh
sudo sh -c "wget https://raw.githubusercontent.com/BlocklessNetwork/cli/main/download.sh -v -O download.sh; chmod +x download.sh; ./download.sh; rm -rf download.sh"
```

To install on Windows, go to the [releases page](https://github.com/blocklessnetwork/cli/releases) on GitHub and download the x86 version of the CLI. Currently, the Windows ARM64 version is not supported.

## Usage

To use the BLS CLI, open a terminal and run `bls` followed by the command you want to use. The command structure is as follows:

```sh
bls [command] [subcommand]
```

For example, to connect to the Blockless Network, you can run the `bls login` command:

```sh
bls login
```

## Help

To see a list of available commands, either run the `bls` command directly or run `bls` command with the `-h` or `--help` flag:

```sh
bls -h
```

You can also use `-h` or `--help` flag after any commands to display sub-commands or usage information. For example:

```sh
bls function -h
```

## Other Available Glboal Flags
### `--yes` Flag
You can use `-y` or `--yes` flag to set all options to the default value. For example:

```sh
bls function deploy -y
```

### Version Info
You can use `-v` or `--version` flags to check the version information for the CLI:

```sh
bls -v
```

## Top Level Commands
The Blockless CLI offers a variety of commands for managing your account, local components, and projects. For detailed CLI reference, please visit [Blockless CLI Reference]().

Below is a list of commonly used commands:

- `bls help`: Displays information and usage instructions for the BLS CLI and its available subcommands.
- `bls console`: Opens the BLS console, a web-based interface for managing your deployments and projects on the Blockless network.
- `bls login`: Authenticates and logs in to the Blockless network using your wallet keypair.
- `bls whoami`: Shows information about your current identity on the Blockless network, including your public key.
- `bls components`: Manages your local environment components, including the local worker agent and orchestrator agent.
- `bls function`: Build, test, and manage your projects and functions.
