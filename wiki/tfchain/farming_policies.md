# Farming Policies

A farming policy defines how farming rewards are handed out for nodes. Every node has a farming policy attached. A farming policy is either linked to a farm, in which case new nodes are given the farming policy of the farm they are in once they register themselves. Alternatively a farming policy can be a "default". These are not attached to a farm, but instead they are used for nodes registered in farms which don't have a farming policy. Multiple defaults can exist at the same time, and the most fitting should be chosen.

A farming policy has the following fields:

- id (used to link policies)
- name
- Default. This indicates if the policy can be used by any new node (if the parent farm does not have a dedicated attached policy). Essentially, a `Default` policy serves as a base which can be overriden per farm by linking a non default policy to said farm.
- Reward tft per CU, SU and NU
- Minimal uptime needed in percentage (can be decimal e.g. 99.8%)
- Policy end date (After this data the policy can not be linked to new farms any more)
- If this policy is immutable or not. Immutable policies can never be changed again

Additionally, we also use the following fields, though those are only useful for `Default` farming policies:

- Node needs to be certified
- Farm needs to be certified (with certification level, which will be changed to an enum).

In case a farming policy is not attached to a farm, new nodes will pick the most appropriate farming policy from the default ones. To decide which one to pick, they should be considered in order with most restrictive first until one matches. That means:

- First check for the policy with highest farming certification (in the current case gold) and certified nodes
- Then check for a policy with highest farming certification (in the current case gold) and non certified nodes
- Check for policy without farming certification but certified nodes
- Last check for a policy without any kind of certification

Important here is that certification of a node only happens after it comes live for the first time. As such, when a node gets certified, farming certification needs to be re evaluated, but only if the currently attached farming policy on the node is a `Default` policy (as specifically linked policies have priority over default ones). When evaluating again, we first consider if we are eligible for the farming policy linked to the farm, if any.

### Limits on linked policy

When a council member attaches a policy to a farm, limits can be set. These limits define how much a policy can be used for nodes, before it becomes unusable and gets removed. The limits currently are:

- CU. Every time a node is added in the farm, it's CU is calculated and deducted from this amount. If the amount drops below 0, the maximum amount of CU that can be attached to this policy is reached.
- SU. Every time a node is added in the farm, it's SU is calculated and deducted from this amount. If the amount drops below 0, the maximum amount of SU that can be attached to this policy is reached.
- End date. After this date the policy is not effective anymore and can't be used. It is removed from the farm and a default policy is used.
- Certification. If set, only certified nodes can get this policy. Non certified nodes get a default policy.

Once a limit is reached, the farming policy is removed from the farm, so new nodes will get one of the default policies until a new policy is attached to the farm.

## Creating a Policy

A council member can create a Farming Policy in the following way:

1: Open [PolkadotJS](https://polkadot.js.org/apps/?rpc=wss%3A%2F%2Ftfchain.grid.tf#/council/motions) apps on the corresponding network and go to `Council`
2: Create a council motion (proposal). Click on `Propose motion`
3: Now select the account to propose from (should be an account that's a council member).
4: Select a threshold (amount of council members to approve the motion)
5: As action, select `tfgridModule` -> `createFarmingPolicy` and fill in all the fields.
6: If all the fields are filled in, click `Propose`. Now other council members can vote, if there are enought votes, the proposal should be closed. This `Close` action will show in the UI once there are enough votes.

All (su, cu, nu, ipv4) values should be expressed in units USD. Minimal uptime should be expressed as integer that represents an percentage (example: `95`).

Policy end is optional (0 or some block number in the future). This is used for expiration.

For reference:

![image](./img/create_policy.png)