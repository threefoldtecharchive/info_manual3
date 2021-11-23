# Billing on ThreeFold Grid 3.0

In TFGrid 3.0 billing is in accordance with proof of utilization

!!!include:threefold:utility_token_model


## Use TFTs on Parity Substrate

As from v3.0, TFTs exist on TFChain, which is ThreeFold's blockchain on Parity Substrate.

These TFTs have the same value as on the Stellar network, there is a bridging mechanism in place that allows to transfer TFTs between the 2 blockchains, in both directions.

## Proof of Utilization

All resource utilisation is registered on the TFChain on an hourly basis. We call this [Proof Of Utilization](threefold:proof_of_utilization).

These resources are a combination of cloud units: 

- Compute resources ("CU")
- Storage resources ("SU")
- Network resources ("NU")

and network utilization :

- IPv4 addresses
- DNS, name on web gateways

## Discount on staked tokens

A personal staking mechanism has been put in place that provides token holders with discounts on the capacity they purchase.

!!!include:threefold:staking_discount_levels0

A more detailed overview of prices can be found [here](threefold:pricing).

!!!def alias:grid_billing