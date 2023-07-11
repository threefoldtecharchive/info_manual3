> IMPORTANT NOTICE (05/03/2023): 
The information of this page is outdated. ThreeFold team is in the process of migrating this this manual to its new home on manual.grid.tf. Please go to [manual.grid.tf](https://manual.grid.tf/) to read the latest documentation of ThreeFold.

# Listing Public IPs

Listing public IPs can be done by asking graphQL for all IPs that has `contractId = 0`

```graphql
query MyQuery {
  publicIps(where: {contractId_eq: 0}) {
    ip
  }
}
```