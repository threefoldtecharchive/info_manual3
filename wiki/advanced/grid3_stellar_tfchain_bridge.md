# Transferring TFT between Stellar and TF Chain

> TODO: review what is useful and how, how does it relate with token_transfer_keygenerator

## Usage

This document will explain how you can transfer TFT from TF Chain to Stellar and back.

Note: The Bridge described below is for devnet, connected to Stellar Testnet.

## Prerequisites

- Ed25519 keypair

Create a keypair with the following tool: https://github.com/threefoldtech/tfchain_tft/tree/main/tfchain_bridge/tools/keygen

```
go build .
./keygen
```

## Stellar to TF Chain

Create a Stellar wallet from the key that you generated.

Transfer the TFT from your wallet to the bridge address:

```
GBNOTAYUMXVO5QDYWYO2SOCOYIJ3XFIP65GKOQN7H65ZZSO6BK4SLWSC
```

A deposit fee of 1 TFT will be taken, so make sure you send a larger amount as 1 TFT.

> IMPORTANT NOTE: Please **always insert the memo text** for every transaction. The memo should be **twin_** (the respective person's twin id). Failure to do so will result in lost of tokens.

### Alternative Transfer to TF Chain

We also enabled deposits to TF Grid objects. Following objects can be deposited to:

- Twin
- Farm
- Node
- Entity

To deposit to any of these objects, a memo text in format `object_objectID` must be passed on the deposit to the bridge wallet. Example: `twin_1`. 

To deposit to a TF Grid object, this object **must** exists. If the object is not found on chain, a refund is issued.

## TF Chain to Stellar

Create a TF Chain account from the key that you generated. (TF Chain raw seed).
Browse to https://polkadot.js.org/apps/?rpc=wss%3A%2F%2Ftfchain.dev.grid.tf#/accounts -> Add Account -> Click on mnemonic and select `Raw Seed` -> Paste raw TF Chain seed. 
Select `Advanced creation options` -> Click `Schnorrkel (sr25519)` -> Select `Edwards (ed25519)`. Click `I have saved my mnemonic seed safely` and proceed.

Browse to https://polkadot.js.org/apps/?rpc=wss%3A%2F%2Ftfchain.dev.grid.tf#/extrinsics , select tftBridgeModule and extrinsic: `swap_to_stellar`. Provide your substrate address and amount.
Again, a withdrawfee of 1 TFT will be taken, so make sure you send a larger amount as 1 TFT.

The amount withdrawn from TF Chain will be sent to your Stellar wallet.

Example: ![swap_to_stellar](img/swap_to_stellar.png)