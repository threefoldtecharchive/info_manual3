In this example we will see how to deploy a VM and mount disks on it on the Threefold grid v3

!!!include terraform_basics


## Deploying a VM with Mounts using terraform
A complete list of Mount workload parameters can be found [here](https://github.com/threefoldtech/terraform-provider-grid/blob/development/docs/resources/deployment.md#nested-schema-for-vmsmounts).

!!!code url:'https://github.com/threefoldtech/terraform-provider-grid/blob/development/examples/resources/mounts/main.tf'

!!!include terraform_outputs