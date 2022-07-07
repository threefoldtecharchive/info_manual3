## Setting up public configuration `PUB`

Nodes don't need `public config` to host workloads, put a node with public config can also:
- Work as an access point for user networks (ipv4 and ipv6)
- Handle gateway workloads (gateway workloads allow users to expose services from their private workloads)

### Requirements

- PolkaDot UI on the desired environment
- A node booted into your farm.
- The node ID shown from your node console (15 in the screenshot above)

### Steps

Open polkadot UI and navigate to `Developer > Extrinsics`

![set public config](img/public_config.png)

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


