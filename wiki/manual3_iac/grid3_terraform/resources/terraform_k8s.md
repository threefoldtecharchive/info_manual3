![](img/terraform_.png)

# Terraform Kubernetes cluster

Kubernetes deployment can be quite difficult and requiring lots of experience, but I think we provided a very simple way to provision Kubernetes cluster on grid 3

```terraform
terraform {
  required_providers {
    grid = {
      source = "threefoldtech/grid"
    }
  }
}

provider "grid" {
}

resource "grid_network" "net1" {
    nodes = [2, 4]
    ip_range = "10.1.0.0/16"
    name = "network12346"
    description = "newer network"
}

resource "grid_kubernetes" "k8s1" {
  network_name = grid_network.net1.name
  nodes_ip_range = grid_network.net1.nodes_ip_range 
  token = "12345678910122"
  ssh_key = "ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQCeq1MFCQOv3OCLO1HxdQl8V0CxAwt5AzdsNOL91wmHiG9ocgnq2yipv7qz+uCS0AdyOSzB9umyLcOZl2apnuyzSOd+2k6Cj9ipkgVx4nx4q5W1xt4MWIwKPfbfBA9gDMVpaGYpT6ZEv2ykFPnjG0obXzIjAaOsRthawuEF8bPZku1yi83SDtpU7I0pLOl3oifuwPpXTAVkK6GabSfbCJQWBDSYXXM20eRcAhIMmt79zo78FNItHmWpfPxPTWlYW02f7vVxTN/LUeRFoaNXXY+cuPxmcmXp912kW0vhK9IvWXqGAEuSycUOwync/yj+8f7dRU7upFGqd6bXUh67iMl7 ahmed@ahmedheaven"

  master {
    disk_size = 22
    node = 2
    name = "mr"
    cpu = 2
    publicip = true
    memory = 2048
  }
  workers {
    disk_size = 15
    node = 2
    name = "w0"
    cpu = 2
    memory = 2048
  }
  workers {
    disk_size = 13
    node = 4
    name = "w2"
    cpu = 1 
    memory = 2048
  }
  workers {
    disk_size = 13
    node = 4
    name = "w3"
    cpu = 1
    memory = 2048
  }
}


output "master_public_ip" {
    value = grid_kubernetes.k8s1.master[0].computedip
}

output "wg_config" {
    value = grid_network.net1.access_wg_config
}

```
Everything looks similar to our first example, the global terraform section, the provider section and the network section.

### grid kubernetes resource


```terraform
resource "grid_kubernetes" "k8s1" {
  network_name = grid_network.net1.name
  nodes_ip_range = grid_network.net1.nodes_ip_range 
  token = "12345678910122"
  ssh_key = "ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQCeq1MFCQOv3OCLO1HxdQl8V0CxAwt5AzdsNOL91wmHiG9ocgnq2yipv7qz+uCS0AdyOSzB9umyLcOZl2apnuyzSOd+2k6Cj9ipkgVx4nx4q5W1xt4MWIwKPfbfBA9gDMVpaGYpT6ZEv2ykFPnjG0obXzIjAaOsRthawuEF8bPZku1yi83SDtpU7I0pLOl3oifuwPpXTAVkK6GabSfbCJQWBDSYXXM20eRcAhIMmt79zo78FNItHmWpfPxPTWlYW02f7vVxTN/LUeRFoaNXXY+cuPxmcmXp912kW0vhK9IvWXqGAEuSycUOwync/yj+8f7dRU7upFGqd6bXUh67iMl7 ahmed@ahmedheaven"

  master {
    disk_size = 22
    node = 2
    name = "mr"
    cpu = 2
    publicip = true
    memory = 2048
  }
  workers {
    disk_size = 15
    node = 2
    name = "w0"
    cpu = 2
    memory = 2048
  }
  workers {
    disk_size = 13
    node = 4
    name = "w2"
    cpu = 1 
    memory = 2048
  }
  workers {
    disk_size = 13
    node = 4
    name = "w3"
    cpu = 1
    memory = 2048
  }
}

```


it requires
- the network name

- nodes ip range 
- token is the cluster token
- ssh_key to access the cluster VMs


then we describe the VMs master and workers section in terms of 

- name within the deployment
- disk size
- node to deploy it on 
- cpu 
- memory

### Kubernetes outputs

```terraform
output "master_public_ip" {
    value = grid_kubernetes.k8s1.master[0].computedip
}

output "wg_config" {
    value = grid_network.net1.access_wg_config
}

```

We will be mainly interested in the master node public ip `computed IP` and the wireguard configurations

You can check the examples repo [here](https://github.com/threefoldtech/terraform-provider-grid/tree/development/examples)


### Current limitations

- [parallelism=1](https://github.com/threefoldtech/terraform-provider-grid/issues/12)
- [increasing IPs in active deployment](https://github.com/threefoldtech/terraform-provider-grid/issues/15)
- [introducing new nodes to kuberentes deployment](https://github.com/threefoldtech/terraform-provider-grid/issues/13)
- [Multiple deployments on the same node](https://github.com/threefoldtech/terraform-provider-grid/issues/11)

## More Info

A complete list of k8s resource parameters can be found [here](https://github.com/threefoldtech/terraform-provider-grid/blob/development/docs/resources/kubernetes.md).

!!!code url:'https://github.com/threefoldtech/terraform-provider-grid/blob/development/examples/resources/k8s/main.tf'

## Demo

- see [Demo](terraform_k8s_demo)