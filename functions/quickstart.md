---
title: Function Quickstart
description:
category: docs
---

# Function Quickstart

In this page, we will show you an entire function deployment cycle from function creation to function deployment using both the console and CLI. Next, we will show you how to invoke your function and un-deploy your function.

## Deploying Function with Blockless Console

If you have Private Alpha access, go to Blockless [Console](https://console.bls.dev) and log in using your registered Web3 address. We currently support Keplr Wallet (Cosmos), MetaMask, and Martian Wallet (Aptos). 

![Blockless Console Wallet Connect Page](/images/quick-start/login.png)

Select `Functions Tab` on the left and click the `+ Create function` button on the top right corner. This will take you to the Function Creation page where you can connect your Github account and deploy the function by choosing a repository or select one of the starter templates and deploy directly. 

![Blockless Functions Overview](/images/quick-start/functions-overview.png)

For the quick start guide, we will use the `Hello World` template button on the bottom and deploy a function that will return a JSON file with a “Hello World” message.

![Function Creation Page](/images/quick-start/new-function.png)

After clicking, when the loading is complete, your first function is deployed to the Blockless network and is running on the decentralized execution layer. Congratulations on deploying your first decentralized function! You should be seeing your deployed function in the Functions Overview page.

![Functions Overview Page with the Newly Deployed Function](/images/quick-start/functions-overview-deployed.png)

By clicking the function, you will jump to the Function Details page where you can view the function status and change the function settings.

![Function Details Page](/images/quick-start/function-details.png)

You can invoke your function with the invocation URL. Here, the function returns a “Hello World” message in JSON format.

![Returned Hello World Message](/images/quick-start/invocation-result.png)

Going back to the Functions Detail page, you can go to the function’s settings and change the function name. Alternatively, you can choose to either stop or delete the function. Here, we changed the automatically generated function name `electric_cyan_cuckoo_1cc1` to `my-first-function`.

![Changing the Function Name](/images/quick-start/functions-settings.png)

You can see the reflected name change in the Functions Overview page. 

![Functions Overview with the New Function Name](/images/quick-start/functions-overview-name-changed.png)

Finally, let’s go back to the function’s settings and delete this function. You can also choose to stop the deployment where the function will still show up in your console, but will be removed from the Blockless Workers. 

![Delete the Function](/images/quick-start/delete-function.png)

Going back to the Functions Overview page, we indeed confirm that our `my-first-function` is deleted.

![Functions Overview after Delete](/images/quick-start/function-overview-after-delete.png)

## Deploying Function with Blockless CLI

Coming soon.
