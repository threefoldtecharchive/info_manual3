> IMPORTANT NOTICE (05/03/2023): 
The information of this page is outdated. ThreeFold team is in the process of migrating this this manual to its new home on manual.grid.tf. Please go to [manual.grid.tf](https://manual.grid.tf/) to read the latest documentation of ThreeFold.


# Canceling contracts

Right now there is no easy, friendly way to cancel all of your contracts (it's planned to have an easier way)

from the graphql service ([threefold services](manual3_tfservices)) execute the following query


```
query MyQuery {

  nodeContracts(where: {twinId_eq: TWIN_ID, state_eq: Created}) {
    contractId
  }
}

```

replace `TWIN_ID` with your twin id. the information should be available on the [portal](dashboard_portal_home)

then from [polkadot UI](https://polkadot.js.org/apps/), add the tfchain endpoint ([threefold services](manual3_tfservices)) to development 

![](img/polka_web_add_development_url.png)

go to extrinsics, choose the smartContract module and cancelContract extrinsic and use the IDs from graphql to execute the cancelation

![](img/polka_web_cancel_contracts.jpg)


## cancel using code
can also cancel them using [code](https://github.com/threefoldtech/grid3_client_ts/blob/development/scripts/delete_all_contracts.ts) 

after cloning `grid3_client_ts`, `yarn install`, and update the `config.json` (beside the script), execute  `yarn run ts-node --project ./tsconfig-node.json scripts/delete_all_contracts.ts` 