
![](img/releasenotes.jpg)

# ThreeFold Release Notes TFGrid 3.x

## TFChain

- Staking support (as the moment of this writing it's only on devnet now)
- KeyValue store support
- Bridging tokens from stellar to tfchain
- Smart contract for IT 
- Billing 
- Consumption Reports
- Discounts support

## Admin Portal

- Creation of twins
- Bridge from and to stellar
- Farm management
 


## ZOS
- zmachine support
- Integration with latest subtsrate client event types
- public ipv6 support in VMs
- planetary support in VMs 
- upgrade to new file system RFS
- support for QSFS
- support for gateways
- capacity reporting to the blockchain support
- Support of SR25519
- Improvements in .zosrc creation
- Safer mechanism for environment variables and init arguments
- improvments in cleaning unused mounts

https://github.com/threefoldtech/zos/releases

## Terraform
- Support ZMachine
- Support Kubernetes
- Support QSFS
- Support Capacity Planning
- Support Gateways

https://github.com/threefoldtech/tf-terraform-provider/releases


## grid3_client_ts
- Support ZMachine
- Support Kubernetes
- Support QSFS
- Support Capacity Planning
- Support Gateways

https://github.com/threefoldtech/grid3_client_ts/releases


## Weblets

- Support Profile manager
- Support Virtual machine
- Support CapRover
- Support Kubernetes
https://github.com/threefoldtech/grid_weblets/releases

## QSFS

TODO


- [TFgrid 3.0 announcement](https://forum.threefold.io/t/announcement-of-tfgrid-3-0/1132)
- [Whats new in TFGrid 3.0](https://forum.threefold.io/t/what-is-new-in-tfgrid-3-0/1133)
- [Roadmap](https://circles.threefold.me/project/despiegk-product_tfgrid3_roadmap/wiki/home)

## Known Issues 3.0

Following list is incomplete but gives some issues to think about.

- Weblets [limitations](https://library.threefold.me/info/manual/#/manual__weblets_home?id=limitations)
- Public IP6 [support](https://github.com/threefoldtech/zos/pull/1488) in ZOS
- QSFS integration is a work in progress
- ZOS and SSD performance [issue](https://github.com/threefoldtech/zos/issues/1467)
- Threefold Connect having [issues](https://circles.threefold.me/project/test-tfgrid3/issue/52) 
- Docker & ZOS containers [differences](https://github.com/threefoldtech/zos/issues/1483)
- ZOS workloads upgrade [issue](https://github.com/threefoldtech/zos/issues/1425)
- Terraform projects [don't reflect in the weblets](https://github.com/threefoldtech/terraform-provider-grid/issues/146)
- Can't detach public IP from a VM and removing it from a contract [issue](https://github.com/threefoldtech/tfchain_pallets/issues/73), please note you can still create each in separate contracts.
