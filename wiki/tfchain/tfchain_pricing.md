# Pricing

The pricing for deployments is a combination of following elements:

- The price of TFT
- The amount of resources used on a node
- The pricing defined by the council (DAO in the next phase)

An example will show how you can calculate the cost of a contract.

## Identify the amount of resources your contract (deployment) uses

If for example you wish to create a virtual machine with following specs:

- 2 cpu
- 8 gb ram
- 100 gb ssd

Then the amount of resources (CU/SU) can be calculated as following:

## First define hru, sru, mru, cru

Let say my workload uses following resources:

```
mru = 8 gigabytes
sru = 100 gigabytes
cru = 2 cores
hru = 0 gigabytes
```

### now calculate CU/SU

```
cu1 = MAX(cru/2, mru/4)
cu2 = MAX(cru, mru/8)
cu3 = MAX(cru/4, mru/2)
CU = MIN(cu1, cu2, cu3)

CU (in this example) = 2
```

```
SU = hru / 1200 + sru / 200

SU (in this example) = 0.5
```

### Now caculate the price in dollar

First read the pricing from either:

- library (https://library.threefold.me/info/threefold/#/tfgrid/pricing/threefold__pricing?id=cloud-pricing-it-capacity)
- chain (see below)

```
cost_usd_month = (CU * price CU in mUsd) * (SU * price SU in mUsd) * 24 (hours) * 30 (days) / 1000 (for conversion to usd)

const_usd_month = (2 * 30.56) + (0.5 * 19.44) * 24 * 30 / 10000
= 5.10048 USD / Month
```

### Getting the price from chain:

Go to one of following links based on the network you are on:

- [devnet](https://polkadot.js.org/apps/?rpc=wss%3A%2F%2Ftfchain.dev.grid.tf#/settings/developer)
- [qanet](https://polkadot.js.org/apps/?rpc=wss%3A%2F%2Ftfchain.qa.grid.tf#/settings/developer)
- [testnet](https://polkadot.js.org/apps/?rpc=wss%3A%2F%2Ftfchain.test.grid.tf#/settings/developer)
- [mainnet](https://polkadot.js.org/apps/?rpc=wss%3A%2F%2Ftfchain.grid.tf#/settings/developer)

Copy the contents of the following [file](https://raw.githubusercontent.com/threefoldtech/tfchain_client_js/master/types.json) in the developer screen.

Click on `Developer` submenu, next click `Chain State`. Select state query `tfgridModule` -> `pricingPolicies` and query the one with ID: 1.

Following similar object should be returned:

```
{
  version: 2
  id: 1
  name: threefold_default_pricing_policy
  su: {
    value: 100,000
    unit: Gigabytes
  }
  cu: {
    value: 200,000
    unit: Gigabytes
  }
  nu: {
    value: 30,000
    unit: Gigabytes
  }
  ipu: {
    value: 50,000
    unit: Gigabytes
  }
  unique_name: {
    value: 10,000
    unit: Gigabytes
  }
  domain_name: {
    value: 20,000
    unit: Gigabytes
  }
  foundation_account: 5H6XYX17yJyjazoLVZqxxEPwMdGn99wginjmFBKtjvk8iJ3e
  certified_sales_account: 5Esq6iLLBGGJFsCEXpoFhxHhqcaGqTvDasdwy8jPFDH1jYaM
  discount_for_dedicated_nodes: 50
}
```

If for example you want to know the pricing in mUsd for `cu`

->

```
cu (200000 / 1000)
= 200 mUsd
```
