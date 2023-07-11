> IMPORTANT NOTICE (05/03/2023): 
The information of this page is outdated. ThreeFold team is in the process of migrating this this manual to its new home on manual.grid.tf. Please go to [manual.grid.tf](https://manual.grid.tf/) to read the latest documentation of ThreeFold.


## consumption report

there's no easy, friendly way yet, but to find how much you're being billed

1- you need to find the contract ID
2- ask the graphql for the consumption 

example query for all contracts

```graphql
query MyQuery {
  contractBillReports {
    contractId
    amountBilled
    discountReceived
  }
}

```


And for a specific contract
```graphql
query MyQuery {
  contractBillReports(where: {contractId_eq: 10}) {
    amountBilled
    discountReceived
    contractId
  }
}

```



## consumption


```graphql
query MyQuery {
  consumptions(where: {contractId_eq: 10}) {
    contractId
    cru
    sru
    mru
    hru
    nru
  }
}
``` 

> Note for the full list of threefold services for the urls of portal and graphql updated to your active network go to [threefold services](manual3_tfservices)