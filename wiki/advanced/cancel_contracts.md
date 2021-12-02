# Canceling contracts

Right now there is no easy, friendly way to cancel all of your contracts (it's planned to have an easier way)

from the graphql service e.g https://graphql.dev.grid.tf/graphql execute the following query


```
query MyQuery {

  nodeContracts(where: {twinId_eq: TWIN_ID}) {
    twinId
    contractId
  }
}

```

replace `TWIN_ID` with your twin id. the information should be available on the [portal](tfchain_portal_home) 

then from polkadot UI

![](img/polka_web_cancel_contracts.jpg)
go to extrinsics, choose the smartContract module and cancelContract extrinsic and use the IDs from graphql to execute the cancelation 

> Note for the full list of threefold services for the urls of portal and graphql updated to your active network go to [threefold services](manual3_tfservices)


## cancel using code
can also cancel them using [code](https://github.com/threefoldtech/grid3_client_ts/blob/development/scripts/delete_all_contracts.ts) 

after cloning `grid3_client_ts` and `yarn install` execute  `yarn run ts-node --project ./tsconfig-node.json scripts/delete_all_contracts.ts` 