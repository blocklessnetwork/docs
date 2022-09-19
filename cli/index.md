---
title: CLI
description:
category: docs
---

# CLI

Blockless gives you multiple ways to interact with and configure your Functions. With the command-line interface (CLI), you can interact with the Blockless network using a terminal or through an automated system, enabling you to retrieve logs, manage credentials, replicate your deployment environment locally, and more.

This page contains a complete list of all Blockless CLI commands available.

# Installing the CLI

Using `curL`:

```bash
$ sudo sh -c "curl https://raw.githubusercontent.com/txlabs/blockless-cli/main/download.sh | bash"
```

Using `wget`:

```bash
$ sudo sh -c "wget https://raw.githubusercontent.com/txlabs/blockless-cli/main/download.sh -v -O download.sh; chmod +x download.sh; ./download.sh; rm -rf download.sh"
```

To install on Windows, head over to the [releases page](https://github.com/txlabs/blockless-cli/releases) on Github and pick up the `x86` version of the CLI. Currently, Windows `ARM64` version is not supported.

## Basic Usage

Use the `bls` command from the root of a Function directory. 

```bash
$ bls
```

Alternatively, you can also use the `bls` command and supplying a path to the root directory of the Function.

```bash
$ bls {path_to_project}
```

## Help

The `--help` option, shorthand `-h`, can be used to display more information about Blockless CLI commands. At the top level, you can also use `help` directly to display help content.

```bash
$ bls help
$ bls --help
$ bls -h
```

You can also use `--help`  option after any commands to display sub-commands or usage information. For example:

```bash
$ bls function --help
```

## Top Level Commands

Use the `console` command to open the Blockless console in browser.

```bash
$ bls console
```

Use the `login` command to connect your Web3 wallet. This command will open up your browser and direct you to link the wallet.

```bash
$ bls login
```

Use the `logout` command to disconnect your Web3 wallet.

```bash
$ bls disconnect
```

Use the `whoami` command to retrieve your user information and test your authentication configuration.
```bash
$ bls whoami
```

## Components

Components are the installable parts of the Blockless CLI. A component can be a command-line tool (`bls`), a set of Blockless CLI commands at the Alpha or Beta release levels, or a package that contains dependencies used by a tool in the Blockless CLI (`localenv` ).

The most commonly-used components are installed by default (`bls` and `localenv`). Other components are installed on-demand by the Blockless CLI when you run commands that require them.

The `localenv` component is the local runtime environment consisting of one orchestrator and one worker for you to test your Function bundle locally. 

Use the `list` command to display all currently available components.

```bash
$ bls components list
```

Use the `install` command to install components.

```bash
$ bls components install localenv
```

Use the `uninstall` command to uninstall components.

```bash
$ bls components uninstall localenv
```

Use the `update` command command to update all installed components to the latest available version.

```bash
$ bls components update
```

Alternatively, you can use `update {component_id}` command to update specific component to the latest available version.

```bash
$ bls components update localenv
```

`info {component_id}` command is used to display specific component’s information.

```bash
$ bls components info localenv
```

Finally, use `config {component_id}` command to configure a specific component if available. 

```bash
$ bls components config localenv
```

## Functions

The `function` command allow you to manage, test, and deploy your Blockless Functions using the Blockless CLI.

Use the `function list` command to list both deployed and un-deployed functions in your wallet account.

```bash
$ bls function list
```

Use the `init {p1} {p2}` command to initial a Function project. 

`{p1}` is the required remote starter’s name field, for example, `assemblyscript`. Currently, we only support `assemblyscript`. Support for `tinygo`, `rust`, `c`, and `c++` will be updated shortly.
`{p2}` is an optional field for project’s name. If not entered, a random name will be automatically generated.

```bash
$ bls function init assemblyscript my-oracle
```

Use the `invoke <-n name | -p path>` command to invoke your remote or local function.

If `-n name` is supplied, the remote function will be invoked. If `-p path` is supplied, then the project in the supplied path will be executed locally inside the `localenv`.

If none of the two parameters is entered, the project in the current directory (`-p ./`) will be used by default. 

In all cases, if there are no name or project found, an error will be thrown.

```bash
$ bls function invoke -n my-oracle
$ bls function invoke -p ./
```

`deploy {project_path}`  command is used to deploy your Function to the Blockless network.

`{project_path}` is an optional field for the project path. If the project path is not supplied, the current directory will be used by default. If no project is found in the directory, an error will be thrown.

```bash
$ bls function deploy ./
```

Use the `stop {target}` command to un-deploy the Function from the Blockless network. `{target}` is a mandatory field for the currently-deployed Function name on the Blockless network.

```bash
$ bls function stop my-oracle
```

Use the `delete {target}` command to un-deploy the Function from the Blockless network and remove the Function executable bundle from the storage (IPFS). `{target}` is a mandatory field for the currently-deployed Function name on the Blockless network.

```bash
$ bls function delete my-oracle
```