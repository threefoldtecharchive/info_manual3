# TF-Chain Portal: Create a Farm

If you want to start farming, you need a farmID, the ID of the farm that is owning the hardware node(s) you connect to the TFGrid. 

!!!include:tfchain_portal_list

Click `CREATE FARM` and choose a name. 

![](img/grid3_portal_farm.png ':size=600')

![](img/grid3_portal_create_farm.png ':size=300')

Click `CREATE` and sign the action. 

The farm is by default set up as 'DIY'. A farm can become certified through certification program. More info to be found [here](threefold:farming_certified_requirements).
Also a pricing policy is defined. Pricing policy is currently the same for all farms, the field is created for future use. 

## Add a public IP to your Farm

If you have public IPv4 addresses available that can be used for usage on the TFGrid, you can add them in your farm. 
Click `ADD IP`, specify the addresses, the gateway and click `CREATE`. 

![](img/grid3_portal_ip_add.png ':size=600')
![](img/grid3_portal_ip_add_detail.png ':size=300')

Deleting IPv4 addresses is also possible here. The `Deployed Contract ID` gives an indication of whether an IP is currently used. If it is 0, it is safe to remove it. 

![](img/grid3_portal_ip_result.png ':size=400')

## Adding public configuration

![set public config](img/tfchain_portal_farming_publicconfig.png)

You have to set the required values:
- `ipv4` is the public IPv4 assigned to the node in CIDR format (x.x.x.x/mask)
  (for example: 10.20.30.40/24)
- `ipv6` (optional) is the public IPv6 assigned to the node in CIDR format (IP/prefix)
- `gw4` gateway for ipv4
- `gw6` (optional) gateway for ipv6
- `domain` (optional) assign a domain name

> Note: For optional value enter the value `0x` for empty.

`domain` is needed if the node will host named gateway workloads. Let's assume you own domain `farmer.com` and you wanna name your gateway `gateway.farmer.com` then:
- `A` record `gatway.farmer.com` to node public IPV4
- `CNAME` record `*.gateway.farmer.com` to `gateway.farmer.com`
- `NS` record `_acme-challenge.gateway.farmer.com` to `gateway.farmer.com`

## Add a Stellar address for payout

In a first phase, farming of tokens still results in payout on the Stellar network. So to get the farming reward, a Stellar address needs to be provided. 

![](img/grid3_portal_farm0.png ':size=600')

![](img/grid3_portal_stellar.png ':size=400')

## Generate your node bootstrap image

Once you know your farmID, you can set up your node on TFGrid3. Click on `Take me to bootstrap page`.

After booting a node, the info will become available in your portal, including the status info. 

![](img/grid3_portal_node_info.png ':size=600')

## Capacity Explorer

In the upper right corner, you can click on `CAPACITY EXPLORER` to get a view of all capacity connected to TFGrid v3. For more info, see [here](explorer_home).

!!!include:tfchain_portal_toc
