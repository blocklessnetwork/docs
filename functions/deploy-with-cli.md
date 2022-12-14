---
title: Deploy with CLI
description:
category: docs
---

# Deploy with CLI

Build, preview, and deploy your Functions from the Blockless command line interface (CLI). Follow this guide to set up your development environment.

## Install Blockless CLI

```sh
sudo sh -c "curl https://raw.githubusercontent.com/BlocklessNetwork/cli/main/download.sh | bash"
```

See detailed [installation instructions](/docs/cli).

## Authenticate the CLI with your account

To enable deployments to Blockless, you'll need to authenticate by logging into your [account](/docs/account) via the CLI.

```sh
bls login
```

You will be guided to log in.

## Create your function

```sh
bls function init
```

You will be guided to initialize a new function.

## Deploy to Blockless

Navigate to the project directory, and you're ready to deploy.

```sh
bls function deploy
```
