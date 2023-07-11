> IMPORTANT NOTICE (05/03/2023): 
The information of this page is outdated. ThreeFold team is in the process of migrating this this manual to its new home on manual.grid.tf. Please go to [manual.grid.tf](https://manual.grid.tf/) to read the latest documentation of ThreeFold.

![](img/proof_utilization_.png)

# Proof of Utilization on ThreeFold Grid 3.0

!!!include:threefold:utility_token_model


## TFChain 3.0

TF_Chain is our blockchain used to manage our TFGrid (based on Substrate). The TF_Grid operates as a DAO.

Our token TFT is multi blockchain compatible, we support TF_Chain, Stellar and Binance Smartchain as money blockchain. The user can transfer his TFT between these Blockchains.

If a user wants to use Internet Capacity (storage, compute and network) on the TF_Grid, then the user will have to transfer money to his account on TFChain.

## Proof of Utilization

All resource utilisation is registered on the TFChain on an hourly basis. We call this [Proof Of Utilization](threefold:proof_of_utilization).

TFGrid is tracking utilization based on following parameters:

- Compute resources ("CU")
- Storage resources ("SU")
- Network resources ("NU")

and network utilization :

- IPv4 addresses
- DNS, name on web gateways

## Discount on staked tokens

A personal automatic staking mechanism has been put in place that provides token holders with discounts on the capacity they purchase.

!!!include:threefold:staking_discount_levels0

A more detailed overview of prices can be found [here](threefold:pricing).

!!!def alias:grid_billing