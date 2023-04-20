# Overview

In general, a Function either exists in your account or can be published to Blockless Marketplace.

Account Function and Marketplace Function do not interfere with each other, although they may be pointing to the same source WASI bundle.

# Account Function vs. Marketplace Function

Account Functions and Marketplace Functions are separate entities. Updates to an Account Function won’t affect the published Marketplace Function, and vice versa.

An Account Function can be perceived as having a version for self-use or testing purposes, whereas the Marketplace Function is for other developers to purchase.

# Account Function

An Account Function can exist in deployed or un-deployed state. Additionally, the deployed Function can either be Public or Private.

Both Public and Private functions are billed to the owner/publisher. However, once deployed, public functions can be invoked without any identity information, whereas private functions can only be invoked by the owner and authorized users.

# Marketplace Function

A Marketplace Function can be acquired for free or with a price/subscription.

When the buyer acquires a Function, they acquire the right to invoke it and the entitlement to the execution result. In other words, the buyer does not have the access to the source code that is compiled to the Function’s WASI binary bundle.

Once acquired, the buyer can view the newly purchased Function in his or her account, and the Function can be invoked at any time.

The Marketplace Function’s billing is charged to the Function’s buyer even if the Function is free to acquire.