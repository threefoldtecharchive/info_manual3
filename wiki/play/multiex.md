# What is a Main.tf?




&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; A main.tf file is a configuration file that defines the infrastructure resources that should be created and managed by Terraform. It is typically the main entry point for a Terraform configuration, and it is used to specify the provider, resources, and outputs for a configuration.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; The main.tf file is written in the HashiCorp Configuration Language (HCL), which is a declarative language that is used to define the desired state of an infrastructure. In the main.tf file, you can specify the properties of the resources that should be created, as well as any dependencies or relationships between those resources.

For example, you might use a main.tf file to define the following resources:

- Virtual machines
- Zero-Databases
- Containers
- Cloud storage buckets


# Multi Node Network Example Main.tf 

```
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
    nodes = [311, 312]
    ip_range = "10.32.0.0/16"
    name = "internal"
    description = "Internal subnet"
    add_wg_access = true
}
resource "grid_deployment" "d1" {
  node = 311
  network_name = grid_network.net1.name
  ip_range = lookup(grid_network.net1.nodes_ip_range, 311, "")
  disks {
    name = "data"
    size = 25
  }
    vms {
    name = "vm1"
    description ="Test vm 1"
    flist = "https://hub.grid.tf/tf-official-vms/ubuntu-22.04-lts.flist"
    cpu = 4
    publicip = true
    publicip6 = true
    memory = 8192
    mounts {
        disk_name = "data"
        mount_point = "/data"
    }
    planetary = true
    env_vars = {
      SSH_KEY ="ADD YOUR SSH KEY HERE"
    }
  }
}
resource "grid_deployment" "d2" {
  node = 312
  network_name = grid_network.net1.name
  ip_range = lookup(grid_network.net1.nodes_ip_range, 312, "")
  disks {
    name = "data"
    size = 25
  }
    vms {
    name = "vm2"
    description ="Test vm 2"
    flist = "https://hub.grid.tf/tf-official-vms/ubuntu-22.04-lts.flist"
    cpu = 4
    publicip = true
    publicip6 = true
    memory = 8192
    mounts {
        disk_name = "data"
        mount_point = "/data"
    }
    planetary = true
    env_vars = {
      SSH_KEY ="ADD YOUR SSH KEY HERE"
    }
  }
}
output "wg_config" {
value = grid_network.net1.access_wg_config
}
output "node1_vm1_ip" {
value = grid_deployment.d1.vms[0].ip
}
output "public_ip" {
value = grid_deployment.d1.vms[0].computedip
}
output "public_ip6" {
value = grid_deployment.d1.vms[0].computedip6
}
output "ygg_ip" {
value = grid_deployment.d1.vms[0].ygg_ip
}
```

This main.tf file is setting up two virtual machines (VMs) on the ThreeFold Grid network.

The VMs will be connected to a network with a specific name and range of IP addresses. The VMs will also have a disk attached to them with a certain name and size. The VMs will be given certain resources, like CPU and memory, and will have certain environment variables set. WireGuard access will also be enabled for the network.

Finally, the configuration will output some information about the network and the VMs, like the WireGuard configuration for the network and the IP addresses of the VMs. This information can be useful for connecting to and managing the VMs.

# Terraform Block
```
terraform {
  required_providers {
    grid = {
      source = "threefoldtech/grid"
    }
  }
}
```
The terraform block is used to specify the configuration options for the Terraform executable itself.

The required_providers block within the terraform block is used to specify a list of providers that are required by the configuration. A provider is a plugin that Terraform uses to interact with specific resources, such as cloud infrastructure or version control systems.

In this case, the required_providers block includes a single provider called "grid", which is specified using the grid block. The grid block includes a source argument, which is used to specify the location of the provider plugin. In this case, the source argument is set to "threefoldtech/grid", which indicates that the provider plugin is hosted on the "threefoldtech" organization's repository on the Terraform Registry.

# Provider Block
```
provider "grid" {
}
```

The provider block is used to specify the configuration options for a particular provider.

In this case, the provider block is for the "grid" provider, and it does not include any arguments, so it is left empty.

# Resource Blocks
```
resource "grid_network" "net1" {
    nodes = [311, 312]
    ip_range = "10.32.0.0/16"
    name = "internal"
    description = "Internal subnet"
    add_wg_access = true
}
resource "grid_deployment" "d1" {
  node = 311
  network_name = grid_network.net1.name
  ip_range = lookup(grid_network.net1.nodes_ip_range, 311, "")
  disks {
    name = "data"
    size = 25
  }
    vms {
    name = "vm1"
    description ="Test vm 1"
    flist = "https://hub.grid.tf/tf-official-vms/ubuntu-22.04-lts.flist"
    cpu = 4
    publicip = true
    publicip6 = true
    memory = 8192
    mounts {
        disk_name = "data"
        mount_point = "/data"
    }
    planetary = true
    env_vars = {
      SSH_KEY ="ADD YOUR SSH KEY HERE"
    }
  }
}
resource "grid_deployment" "d2" {
  node = 312
  network_name = grid_network.net1.name
  ip_range = lookup(grid_network.net1.nodes_ip_range, 312, "")
  disks {
    name = "data"
    size = 25
  }
    vms {
    name = "vm2"
    description ="Test vm 2"
    flist = "https://hub.grid.tf/tf-official-vms/ubuntu-22.04-lts.flist"
    cpu = 4
    publicip = true
    publicip6 = true
    memory = 8192
    mounts {
        disk_name = "data"
        mount_point = "/data"
    }
    planetary = true
    env_vars = {
      SSH_KEY ="ADD YOUR SSH KEY HERE"
    }
  }
}
```


The resource blocks are used to define the resources that should be created or managed by the Terraform configuration.

In this case, the main.tf file includes two resource blocks:

- # grid_network block

```
resource "grid_network" "net1" {
    nodes = [311, 312]
    ip_range = "10.32.0.0/16"
    name = "internal"
    description = "Internal subnet"
    add_wg_access = true
}
```

 The grid_network block is used to define a Grid network resource. A Grid network is a virtual network that can be used to connect VMs within a deployment. The grid_network block has the following arguments:

- **nodes:** This argument specifies a list of node IDs that should be included in the network. In this case, the nodes argument is set to [311, 312], which means that the network will include nodes 311 and 312.

- **ip_range:** This argument specifies the IP range for the network, in CIDR notation. In this case, the ip_range argument is set to "10.32.0.0/16", which means that the network will have a range of 65534 IP addresses.

- **name:** This argument specifies the name of the network. In this case, the name argument is set to "internal", which means that the network will be called "internal".

- **description:** This argument specifies a description of the network. In this case, the description argument is set to "Internal subnet", which means that the network will be described as an "Internal subnet".

- **add_wg_access:** This argument specifies whether the network should have WireGuard access enabled. In this case, the add_wg_access argument is set to true, which means that WireGuard access will be enabled for the network.

- # grid_deployment blocks
```
resource "grid_deployment" "d1" {
  node = 311
  network_name = grid_network.net1.name
  ip_range = lookup(grid_network.net1.nodes_ip_range, 311, "")
  disks {
    name = "data"
    size = 25
  }
    vms {
    name = "vm1"
    description ="Test vm 1"
    flist = "https://hub.grid.tf/tf-official-vms/ubuntu-22.04-lts.flist"
    cpu = 4
    publicip = true
    publicip6 = true
    memory = 8192
    mounts {
        disk_name = "data"
        mount_point = "/data"
    }
    planetary = true
    env_vars = {
      SSH_KEY ="ADD YOUR SSH KEY HERE"
    }
  }
}
resource "grid_deployment" "d2" {
  node = 312
  network_name = grid_network.net1.name
  ip_range = lookup(grid_network.net1.nodes_ip_range, 312, "")
  disks {
    name = "data"
    size = 25
  }
    vms {
    name = "vm2"
    description ="Test vm 2"
    flist = "https://hub.grid.tf/tf-official-vms/ubuntu-22.04-lts.flist"
    cpu = 4
    publicip = true
    publicip6 = true
    memory = 8192
    mounts {
        disk_name = "data"
        mount_point = "/data"
    }
    planetary = true
    env_vars = {
      SSH_KEY ="ADD YOUR SSH KEY HERE"
    }
  }
}
```

 The grid_deployment blocks are used to define Grid deployment resources. A Grid deployment is a group of VMs that are deployed to a single node. The grid_deployment blocks have the following arguments:
- **node:** This argument specifies the ID of the node on which the deployment should be created. In this case, the node argument is set to 311 for the first deployment and 312 for the second deployment,
- **network_name:** This argument specifies the name of the network that the deployment should be connected to. In this case, the network_name argument is set to grid_network.net1.name, which means that the deployment will be connected to the network defined in the grid_network block with the identifier "net1".
- **ip_range:** This argument specifies the IP range for the deployment, in CIDR notation. In this case, the ip_range argument is set to lookup(grid_network.net1.nodes_ip_range, 311, "") for the first deployment and lookup(grid_network.net1.nodes_ip_range, 312, "") for the second deployment, which means that the IP range for the deployment will be determined by looking up the nodes_ip_range attribute of the grid_network block with the identifier "net1" and using the node ID specified in the node argument as the key. If a value is not found for the specified key, an empty string will be used as the default value.

	- **disks block:** The disks block is used to specify the disks that should be attached to the VMs in the deployment. In this case, the disks block includes a single disk with the following arguments:

		- **name:** This argument specifies the name of the disk. In this case, the name argument is set to "data", which means that the disk will be called "data".
		- **size:** This argument specifies the size of the disk, in GB. In this case, the size argument is set to 25, which means that the disk will be 25 GB in size.
	- **vms block:** The vms block is used to specify the VMs that should be included in the deployment. In this case, the vms block includes a single VM with the following arguments:
		- **name:** This argument specifies the name of the VM. In this case, the name argument is set to "vm1" for the first deployment and "vm2" for the second deployment, which means that the VMs will be called "vm1" and "vm2", respectively.
		- **description:** This argument specifies a description of the VM. In this case, the description argument is set to "Test vm 1" for the first deployment and "Test vm 2" for the second deployment, which means that the VMs will be described as "Test vm 1" and "Test vm 2", respectively.
		- **flist:** This argument specifies the flist that should be used to create the VM. Flists are essentially pre-packaged disk images that contain the operating system and any other software that you want to include in the VM. In this case, the flist argument is set to "https://hub.grid.tf/tf-official-vms/ubuntu-22.04-lts.flist", which means that the VM will be created using an Ubuntu 22.04 LTS flist from the official Terraform VMs repository on the Grid.
		- **cpu:** This argument specifies the number of CPU cores that should be allocated to the VM. In this case, the cpu argument is set to 4, which means that the VM will be allocated 4 CPU cores.
		- **publicip:** This argument specifies whether or not the VM should be given a public IP address. In this case, the publicip argument is set to true, which means that the VM will be given a public IP address.
		- **publicip6:** This argument specifies whether or not the VM should be given a public IPv6 address. In this case, the publicip6 argument is set to true, which means that the VM will be given a public IPv6 address.
		- **memory:** This argument specifies the amount of memory that should be allocated to the VM, in MB. In this case, the memory argument is set to 8192, which means that the VM will be allocated 8192 MB of memory.
					
		- **mounts block:** The mounts block is used to specify the disks that should be mounted to the VM. In this case, the mounts block includes a single disk with the following arguments:
			- **disk_name:** This argument specifies the name of the disk that should be mounted. In this case, the disk_name argument is set to "data", which means that the disk named "data" will be mounted to the VM.
			- **mount_point:** This argument specifies the mount point for the disk. In this case, the mount_point argument is set to "/data", which means that the disk will be mounted to the /data directory on the VM.
		- **planetary:** This argument specifies whether or not the VM should be deployed in planetary mode. Planetary mode is a feature of the Grid that allows you to deploy VMs on nodes in different physical locations around the world. In this case, the planetary argument is set to true, which means that the VM will be deployed in planetary mode.
		- **env_vars:** This argument specifies a map of environment variables that should be set on the VM. In this case, the env_vars argument is set to { SSH_KEY ="ADD YOUR SSH KEY HERE" }, which means that an environment variable called SSH_KEY will be set on the VM and its value will be "ADD YOUR SSH KEY HERE". You can use environment variables to pass configuration values to the VM, env vars are used to pass your ssh key to the vm for access 

# Output Blocks
Output variables are used to display information about the resources created by Terraform. Here are the output variables defined in the main.tf file:
```
output "wg_config" {
value = grid_network.net1.access_wg_config
}
```
**wg_config:** This output variable displays the WireGuard configuration for the network with the identifier "net1". The value of the output is set to grid_network.net1.access_wg_config, which means that it will display the access_wg_config attribute of the grid_network resource with the identifier "net1".
```
output "node1_vm1_ip" {
value = grid_deployment.d1.vms[0].ip
}
```
**node1_vm1_ip:** This output variable displays the private IP address of the first VM in the deployment with the identifier "d1". The value of the output is set to grid_deployment.d1.vms[0].ip, which means that it will display the ip attribute of the first element in the vms list of the grid_deployment resource with the identifier "d1".
```
output "public_ip" {
value = grid_deployment.d1.vms[0].computedip
}
```
**public_ip:** This output variable displays the public IP address of the first VM in the deployment with the identifier "d1". The value of the output is set to grid_deployment.d1.vms[0].computedip, which means that it will display the computedip attribute of the first element in the vms list of the grid_deployment resource with the identifier "d1".
```
output "public_ip6" {
value = grid_deployment.d1.vms[0].computedip6
}
```
**public_ip6:** This output variable displays the public IPv6 address of the first VM in the deployment with the identifier "d1". The value of the output is set to grid_deployment.d1.vms[0].computedip6, which means that it will display the computedip6 attribute of the first element in the vms list of the grid_deployment resource with the identifier "d1".
```
output "ygg_ip" {
value = grid_deployment.d1.vms[0].ygg_ip
}
```
**ygg_ip:** This output variable displays the Yggdrasil IP address of the first VM in the deployment with the identifier "d1". The value of the output is set to grid_deployment.d1.vms[0].ygg_ip, which means that it will display the ygg_ip attribute of the first element in the vms list of the grid_deployment resource with the identifier "d1".
