# Weblets

Weblets are a super cool way how to deploy solutions on our tfgrid.

A weblet is a compiled javascript component which can be embedded in any website.
The weblet uses the TFChain javascript client to talk directly to TFChain and ZOS enabled nodes over RMB.

__Advantages__ :

- It makes it very easy to deploy a solution
- It is 100% decentralized, there is no server involved

## Some cool weblets to start with

- [Caprover](weblets_caprover)
- [Virtual Machine](weblets_vm)
- [Funkwhale](weblets_funkwhale)
- [Peertube](weblets_peertube)


## Playground

Playground is available on [https://play.grid.tf](https://play.grid.tf)

### limitations
- can only deploy one thing at a time
- don't move between pages while deploying (you will lose the feedback)
- there's no easy way to delete everything. check [cancel_contracts](cancel_contracts) for more info
- sometimes some nodes are listed as having sufficient capacity while they're not, that's because of the usage caching in the grid proxy, we will be reducing the caching time