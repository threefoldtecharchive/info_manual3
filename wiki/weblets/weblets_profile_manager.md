# Profile Manager

Currently, we're supporting four different networks.
- One for development purposes (Devnet) where you can find it at https://play.dev.grid.tf
- One for internal testing and verifications (QAnet) where you can find it at https://play.qa.grid.tf
- One for testing (Testnet) where you can find it at https://play.test.grid.tf
- One for our mainnet and you can find it at https://play.grid.tf

    
![](img/profile_manager1.png)

Start by creating a profile from the upper right button. This creates a profile, saved and encrypted locally in your browser.

### Secure 

![](img/pro_manager5.png)

The **Profile Manager Password** is how you store your profile info in browser local storage.
Create a new profile by visiting the **Create Profile Manager** tab and enter your new password. After you're done, click on **Create New Profile Manager**. 

You'll need that password to be able to load your profiles afterwards from the **Activate Profile Manager** tab.

![](img/pro_manager6.png)

### Process

Start entering the following information required to create your new profile.

![](img/dev_profile2.png)

- `Profile Name`: Any chosen name, makes it easy for you to remember between sessions.
- `Mnemonics` are the secret words of your Polkadot account, [Generate yours here!](dashboard_portal_polkadot_create_account). 
- Your `Public SSH Key` is used to login into VM's, Kubernetes, ... 

After you finish typing your credentials, click on **Activate**. Once your profile gets activated, you should find your **Twin ID** and **Address** generated under your ***Mnemonics*** for verification. Also, your **Account Balance** will be available at the top right corner under your profile name. 

![](img/dev_profile3.png)

### Keep Deployment Alive

With the [release](https://github.com/threefoldtech/home/blob/master/wiki/products/v3/tfgrid_3.6.1.md) of ThreeFold Grid 3.6.1 on mainnet, the team implemented  a new feature for [Zero-OS](https://github.com/threefoldtech/home/blob/master/wiki/products/v3/tfgrid_3.6.1.md#zos-v310). It now supports a function for **pausing workloads for up to two weeks** before cancelling the contract.

This means that if the wallet paying for a workload runs out of [TFT](https://forum.threefold.io/t/what-is-the-real-value-of-tft/3143?u=hannahcordes), it will get paused for a maximum period of two weeks but not deleted. During this time, you will not be able to access the workload. Simply **add a sufficient amount of tokens to the wallet to cover the costs of the workload**, and it will be resumed. In case the connected wallet doesn’t receive sufficient funds within the two-week grace period, the contract gets cancelled and the workload gets deleted.

### How to calculate deployment costs

With Grid V3, we implemented a **post-billing system**, so you will get billed for the utilized capacity after deploying the workload. The simplest way to estimate your workload’s cost is to deploy on the [TF Playground](https://library.threefold.me/info/manual/#/manual__weblets_home?id=playground) and wait until the **TFT per hour** field fills in. Based on this number, you can calculate your workload’s future costs. Also, you can find the costs per CU/SU/NU [here](https://library.threefold.me/info/threefold#/cloud/threefold__pricing).

### How to know when you’re running out of funds

There are several ways to figure out if your wallet is running out of funds. Simply check your wallet in the TF Connect app or go to the [TF Chain Portal](https://portal.grid.tf/#/) to check on your account balance. 

If you’d like something more advanced, there are some command line tools that allow you to write a small script for monitoring your balance and notifying you on Telegram. Also, @scott will create a bot similar to the [node status bot](https://forum.threefold.io/t/announcing-the-node-status-bot-for-telegram/1880?u=hannahcordes), so you can subscribe to a given wallet address and receive alerts when it's running low – stay tuned!