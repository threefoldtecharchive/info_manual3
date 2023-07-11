> IMPORTANT NOTICE (05/03/2023): 
The information of this page is outdated. ThreeFold team is in the process of migrating this this manual to its new home on manual.grid.tf. Please go to [manual.grid.tf](https://manual.grid.tf/) to read the latest documentation of ThreeFold.

![](img/terraform_.png)

# Terraform Provider


```
terraform {
  required_providers {
    grid = {
      source = "threefoldtech/grid"
    }
  }
}
provider "grid" {
    mnemonics = "FROM THE CREATE TWIN STEP"
    network = "dev" # or test to use testnet
}
```

### environment variables

should be recognizable as Env variables too

- `MNEMONICS`
- `NETWORK`
- `SUBSTRATE_URL` 
- `RMB_PROXY_URL`
- `GRAPHQL_URL`

The *_URL variables can be used to override the dafault urls associated with the specified network

### credential file

```
provider "threefold" {
    creds_file = "..."
}

```

### Deployment example

!!!include:terraform_basic_example

### Remarks

- Grid terraform provider is hosted on terraform registry [here](https://registry.terraform.io/providers/threefoldtech/grid/latest/docs?pollNotifications=true) 
- all provider input variables and their description can be found [here](https://github.com/threefoldtech/terraform-provider-grid/blob/development/docs/index.md)
- capitalized environment variables can be used instead of writing them in the provider (e.g. MNEMONICS)


