> IMPORTANT NOTICE (05/03/2023): 
The information of this page is outdated. ThreeFold team is in the process of migrating this this manual to its new home on manual.grid.tf. Please go to [manual.grid.tf](https://manual.grid.tf/) to read the latest documentation of ThreeFold.


## Components Interaction

### 3Node
On first boot the node needs to create a “twin” on the grid, a twin associated with a public key. Hence it can create verifiable signed messages.
Then, a node will register itself on the grid, and links this twin to the node object.

Once the node is completely up, a user can reach out to the node to submit workload requests.
Responses from the node **must** be signed with the twin secret key, signature can be verified by a user against the node public key.

Node uses the same verification mechanism against requests from twins.

### TF-Chain

#### Definitions
- `entity`: this represents a legal entity or a person, the entity is the public key of the user associated with name, country, and a unique identifier.
- `twin`: represents the management interface that can be accessed over the Yggdrasil IPv6 address. A twin is associated also with a single public key.

On the grid, we build on top of the above concepts a more sophisticated logic to represent the following: (note, full types specifications can be found [here](https://library.threefold.me/info/threefold#/getstarted/manual__tfchain_home))
- farm: a farm is associated
  - `twin-id`: the communication endpoint for this farm.
- node:  associated with
  - `twin-id`: defines the peer information (peer-id and public ipv6)
  - `farm-id`: unique farm id this node is part of.

The grid database is a decentralized blockchain database that leverages on substrate to provide an API that can be used to
- Create Entities
- Create Twins
- Add / Remove entities from twins
- Create Nodes
- Create Farms
- Create Pricing policies for farms
- Create Certification Codes
- Query information about  entities (find node, or verify identities)

A farm has one twin, through this twin the peer_id and entity can be requested. This is also the case for nodes as they have one farm.

### Public IPs

Public IPs are assigned by the grid database from the farmer IPs pool. For this to be possible, on contract creation the user need to specify how many IPs he requires.

If the contract creation is successful it means the contract managed to acquire the required number of Ips. The IPs are going to be available for this specific node.

Once the contract is terminated, the Ips are returned back to the farmer pool.

### Pricing

Each farmer object is assigned a Pricing Policy object:
The pricing policy defines:
- Currency (TFT, USD, etc…) _we will probably drop that_
- SU
- CU
- NU

#### General notes :

Each price (except for the NU) in defined for the consumption of a reference capacity unit during a period of time (see price table [here](https://library.threefold.me/info/manual/#/tfgrid/farming/threefold__farming_reward?id=farming-reward-calculation)).

Example:
SU price is 3.6 USD per month for 1 Gigabyte of storage usage.
If a user reserves C = 10 Gigabytes during a period of T = 2 hours it will cost him C * T * SU price = 10 GB * 2h * 3.6/30d/24h USD/min = 0,1 USD

For NU the price is defined regardless of the elapsed period of time.

Example:
NU price is 1.5 mUSD for 1 Gigabyte of network usage. 
If a user transfers C = 10 Gigabytes of data it will cost him C * NU price = 10 GB * 1.5/1000 USD/GB = 0.15 USD

In all cases the user will be charged the equivalent amount in TFT for its consumptions.
