---
title: Blockless CLI Reference
description:
category: reference
---

# Blockless CLI Reference
This reference documents every command, option, and flag available in the Blockless command line interface.

With the Blockless CLI, you can connect to the Blockless network via your on-chain identity, construct a local worker environment with one click, and build, test, deploy, and monitor your projects in real time.

## Identity & Account
In order to interact with the Blockless Network, you will need to first login with your on-chain identity.

### `$ bls login`
Connects the CLI to the Blockless Network (via the Blockless Gateway with a JWT token) and logs in via your on-chain identities. Currently you can use Metamask, Keplr, or Martian Wallet to log in to the network.

*Basic usage:*
```sh
$ bls login
$ 
$ Open Browser at http://0.0.0.0:8427 to complete login
$ # Your default browser with the authentication page will pop up. 
$ # Alternatively, manually enter the URL in your browser to log in.
$ Sending user to https://console.bls.dev:443 to authenticate
$ User returned from https://console.bls.dev:443 authenticated
```

### `bls logout`
Disconnects the CLI to the Blockless Network. All of your function deployments and information are still accessible when you log back in.

*Basic usage:*
```sh
$ bls logout
$ 
$ disconnecting wallet
$ user logged out
```

## `bls whoami`
Shows the information (public key address) about your current identity on the Blockless Network.

If you are not logged in, a prompt will guide you to use the `bls login` command to log in to the Blockless Network.

*Basic usage:*
```sh
$ bls whoami
$ 
$ You are connected with a JWT token to the Blockless console!
$ ┌──────────┬────────────────────────────────────────────┐
$ │ Wallet   │ Address                                    │
$ ├──────────┼────────────────────────────────────────────┤
$ │ metamask │ 0xda625c8ac3468143abe40d5ba2d4e1846417a5t4 │
$ └──────────┴────────────────────────────────────────────┘
```
## Components
Components are the installable parts of the Blockless CLI. A component can be a command-line tool (for example, bls), a set of Blockless CLI commands at the Alpha or Beta release levels, or a package that contains dependencies used by a tool in the Blockless CLI, such as the local runtime components.

The local runtime components consist of the Blockless WASM Runtime Environment and the b7s networking module. With the local runtime components, you will be able to build and test your function locally.

**If this is your first time using `bls` or building and testing your function, you need to use the `bls components install` command to install the local runtime components**.

### `$ bls components install`
Installs the local runtime components which include the Blockless WASM Runtime Environment and the b7s networking module. These components are used when you build and test your function or project locally.

*Basic usage:*
```sh
$ bls components install
$ 
$                 *%%%%%%%%%.         
$             (%%%%%%*   #%%%%%%*     
$          #%%%%%##  %%%%#   (%%%%%(  
$         (%%%  (%%#   #%%%%%%  (%%%, 
$         (%%%  %%%%%%%%   /%%%  %%%* 
$         (%%%  %%%  %%%%%%%   .%%%%* 
$         (%%%  %%%  %%#   #%%%  %%%* 
$         (%%%. ,%%  %%%%%%%%#  #%%%, 
$          #%%%%%##  #%%%/   #%%%%%,  
$             ,%%%%%%(  *%%%%%%%      
$                  #%%%%%%%#                            
$     
$ 
$ Installing local networking agent ...
$ ✔ Install Location: … /Users/sample_user/.bls
$ 
$ 
$ Installing ... installing to /Users/sample_user/.bls
$ Installing ... installing for darwin_x64
$ Installing ... downloading runtime environment
$ Installing ... unpacking /tmp/blockless-runtime.macos-latest.x86_64.tar.gz
$ Installing ... installed runtime: macos
$ Installing ... done
$ Installing ... downloading networking agent
$ Installing ... unpacking /tmp/b7s-darwin.amd64.tar.gz
$ Installing ... installed networking agent: darwin/amd64
$ Installing ... done
$ Installing ... downloading keygen identity tool
$ Installing ... done
$ Generating ... identity key in /Users/sample_user/.bls/network/keys
$ Generating ... done
$ 
$ Use the following commands to start blockless daemon:
$ 
$ 	 bls components start head to start the head agent
$ 	 bls components start worker to start the worker agent
```

### `$ bls components start [agent]`
Starts a head worker instance or a worker instance. 

For version 0.0.38 and below, the `bls components start` command is for testing purposes only and has limited use cases. In future releases, you will be able to simulate how your function is being orchestrated, deployed, and executed on the the worker instance(s).

*Basic usage:*
Starting a head worker instance:
```sh
$ bls components start head
$ 
$ Off-Chain ... starting head node
$ INFO[0000] starting b7s                                 
$ INFO[0000] config path set configPath=/Users/sample_user/.bls/network/head-config.yaml
$ INFO[0000] loading private key from: /Users/sample_user/.bls/network/keys/priv.bin 
$ INFO[0000] Opening database: /Users/sample_user/.bls/network/12t3KaoWN34D2J4QvRyA4EL9aiJqDqj1JFsqeneZYvnMNPduZsts_appDb 
$ INFO[0000] starting rest server address=0.0.0.0 port=8081
$ INFO[0000] starting chain client service      
```

Starting a worker instance:
```sh
$ bls components start worker
$ 
$ Off-Chain ... starting worker node
$ INFO[0000] starting b7s                                 
$ INFO[0000] config path set configPath=/Users/sample_user/.bls/network/worker-config.yaml
$ INFO[0000] Opening database: /Users/sample_user/.bls/network/12t3KaoWN34D2J4QvRyA4EL9aiJqDqj1JFsqeneZYvnMNPduZsts_appDb
$ INFO[0000] starting peer discovery    
```

## Function

The function command allows you to manage, build, test, and deploy your Blockless Functions using the command line interface.

### `$ bls function list`
Lists both deployed and stopped functions that are associated with your wallet account. 

You have to be logged in to your account before you can use this command and view the function list.

*Basic usage:*
```sh
$ bls function list
$ 
$ List of Functions:
$ -----------------------------------
$ 
$ Name:   sample_func_1
$ CID:    bafybeigusomerandomnumbersandletterskb7gvf7ybidn2wofg7fjitu
$ Status: deployed 
$ 
$ 
$ Name:   sample_func_2
$ CID:    bafybeifsomerandomnumbersandlettersfc2myf743f7lm6uwpkbsbutm
$ Status: stopped
```

### `$ bls function init [framework] [project name]`
Initializes a local starter project or template.

Framework and project name are optional positional arguments. If you omit the positional arguments, you'll be asked to provide your choice interactively with prompts.

Currently we support both Assembly Script (`assemblyscript`) and Rust (`rust`) for your starter project. Additionally, we also provide a Price Oracle template written in Assembly Script that you can directly test and deploy.

*Basic usage:*
```sh
$ bls function init
$ 
$ ✔ What would you like to name your function? … my_first_func
$ ✔ Pick a framework › Assembly Script
$ ✔ Pick a starter template › Hello World
$ 
$ Creating: new function in /Users/sample_user/my_first_func
$ Success: function created at /Users/sample_user/my_first_func
$ 
$ Change into the directory /Users/sample_user/my_first_func to get started
```
With `framework` and `project name` positional arguements:

```sh
$ bls function init assemblyscript my_first_func
$ 
$ ✔ Pick a starter template › Hello World
$ Creating: new function in /Users/sample_user/my_first_func
$ Success: function created at /Users/sample_user/my_first_func
$ 
$ Change into the directory /Users/sample_user/my_first_func to get started
```

### `$ bls function build [flag]`
Build your function locally using the build command specified in the function manifest (bls.toml). By default, this build command uses the `npm run build` command and creates a wasm function bundle that can be deployed to the Blockless Network.

Currently, you must be in the function's root directory (./) and have a function manifest file (bls.toml) in order to build the function. Otherwise, an error will be thrown.

*Basic usage:*
```sh
$ bls function build
$ 
$ Building: function sample_func_1.wasm in /Users/sample_user/sample_func_1/build...
$ 
$ > small_jade_ox@1.0.0 build:debug
$ > npm run clean; asc index.ts --target debug
$ 
$ 
$ > small_jade_ox@1.0.0 clean
$ > rm -rf build
$ 
$ Creating Archive: sample_func_1.tar.gz in /Users/sample_user/sample_func_1/build
$ Build successful!
```

### `$ bls function deploy`
Deploys your function to the Blockless network. Once deployed, you will be able to view your function status using `$ bls function list` command or via the Blockless console.

Currently, you have to be in the function's root directory (./) in order to deploy the function. Otherwise, an error will be thrown. 

The deployment process is broken down into three stages. First, the command will automatically build or rebuild the project with a final function bundle. Next, the command will publish the function bundle to the default storage option, IPFS, via the Blockless Gateway service. Finally, using the returned CID, the function will be deployed to the Blockless Network.

*Basic usage:*
```sh
$ bls function deploy
$ 
$ Building: function sample_func_1.wasm in /Users/sample_user/sample_func_1/build...
$ 
$ > sample_func_1@1.0.0 build:release
$ > npm run clean; asc index.ts --target release
$ 
$ 
$ > sample_func_1@1.0.0 clean
$ > rm -rf build
$ 
$ Creating Archive: sample_func_1.tar.gz in /Users/sample_user/sample_func_1/build
$ Build successful!
$ 
$ Publishing: function located in /Users/sample_user/sample_func_1/build
$ Publish successful!
$ 
$ Deploying sample_func_1 ...
$ Successfully deployed sample_func_1 with id bafybeyd6eiyyjrandomnumbersandlettersli5tlpa7q3qxiifuphba2q
```                              

### `$ bls function update`
Updates an existing deployed function under the current working directory on the Blockless Network.

With the `update` command, the function project will go through the first two stages of the deployment cycle, including building and publishing. Then, using the newly generated CID, the function will be updated on the Blockless Network accordingly. 

If your function has not been deployed before, an error will be thrown and you will be directed to deploy your function instead.

*Basic usage:*
```sh
$ bls function update
$ 
$ Building: function my_first_func.wasm in /Users/sample_user/my_first_func/build...
$ 
$ > my_first_func@1.0.0 build:release
$ > npm run clean; asc index.ts --target release
$ 
$ 
$ > my_first_func@1.0.0 clean
$ > rm -rf build
$ 
$ Creating Archive: my_first_func.tar.gz in /Users/sample_user/my_first_func/build
$ Build successful!
$ 
$ Publishing: function located in /Users/sample_user/my_first_func/build
$ Publish successful!
$ 
$ Updating my_first_func ...
$ Deploying my_first_func ...
$ Successfully deployed my_first_func with id bafybe7sckpzx3mrandomnumbersandlettersrd2tf6thmsz4cf7vxlr5a
```  

### `$ bls function stop [target name]`
Stops or un-deploys the function from the Blockless network. The `target` positional argument is an optional field for the currently-deployed function name on the Blockless network. If not specified, the command will stop the function in the current directory by default.

*Basic usage:*
```sh
$ bls function stop
$ Stopping sample_func_1 ...
$ 
$ Successfully stopped function sample_func_1!
```
With the `target` positional argument:
```sh
$ bls function stop sample_func_1
$ Stopping sample_func_1 ...
$ 
$ Successfully stopped function sample_func_1!
```

### `$ bls function delete [target name]`
Stops or un-deploys the function from the Blockless network and removes the function executable bundle from the default storage (IPFS). The `target` positional argument is an optional field for the currently-deployed function name on the Blockless network. If not specified, the command will stop the function in the current directory by default.

*Basic usage:*
```sh
$ bls function delete
$ 
$ Deleting sample_func_1 ...
$ 
$ Successfully deleted function sample_func_1!
```
With the `target` positional argument:
```sh
$ bls function stop sample_func_1
$ 
$ Deleting sample_func_1 ...
$ 
$ Successfully deleted function sample_func_1!
```

### `$ bls function invoke`
Invokes your local function at the current working directory.

Currently, you must be in the function's root directory (./) in order to invoke the function. Otherwise, an error will be thrown.

The command will automatically detect the build file in the directory. If the function's build file is not detected, the function will be built then invoked. A result will be returned in the terminal afterward.

*Basic usage:*
```sh
$ bls function invoke
$ 
$ Building: function my_first_func_debug.wasm in /Users/sample_user/my_first_func/build...
$ 
$ > my_first_func@1.0.0 build:debug
$ > npm run clean; asc index.ts --target debug
$ 
$ 
$ > my_first_func@1.0.0 clean
v> rm -rf build
$ 
$ Creating Archive: my_first_func_debug.tar.gz in /Users/sample_user/my_first_func/build
$ Build successful!
$ 
$ Hello, world!
```
## Auxurily Commands

### `$ bls console`
Opens up the [Blockless Console](https://console.bls.dev) on your default browser. 

*Basic usage:*

```sh
$ bls console
$ 
$ # Opens https://console.bls.dev on your default browser
```

### `$ bls self-update [flag]`
Automatically fetches and updates the CLI. The CLI will update to the latest release by default if you haven't specified the version tag.

*Basic usage:*
```sh
$ bls self-update
$ 
$ Installing bls latest.....
$ ############################################################################################## 100.0%
$ Installed bls latest at /usr/local/bin/bls
```

*Flag:*
`-t` or `--tag`: updates the CLI to a specific release version using its release tag (version number). You can access all of the available releases and their tags via the [releases page](https://github.com/blocklessnetwork/cli/releases) on GitHub. For example:

```sh
$ bls self-update -t v0.0.37
$ 
$ Password: 
$ Installing bls v0.0.37.....
$ ############################################################################################## 100.0%
$ Installed bls v0.0.37 at /usr/local/bin/bls
```


### `$ bls help`
Displays a list of available commands.

*Basic usage:*
```sh
$ bls help
$ 
$ bls [command] [subcommand]
$ 
$ Commands:
$   bls login        Logs into your blockless account
$   bls logout       Logs out of your blockless account
$   bls whoami       Shows the currently logged in user
$   bls console      Opens the Console in the browser
$   bls components   Manages the components of the local environment
$   bls function     Manages your functions
$   bls self-update  Update the Blockless CLI
$   bls help         Shows the usage information
$ 
$ Flags:
$   -y, --yes      Assume yes to all prompts  
$   -h, --help     Show help  
$   -v, --version  Show version number  
$ 
$ Blockless CLI v0.0.38
```

