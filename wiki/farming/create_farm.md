> IMPORTANT NOTICE (05/03/2023): 
The information of this page is outdated. ThreeFold team is in the process of migrating this this manual to its new home on manual.grid.tf. Please go to [manual.grid.tf](https://manual.grid.tf/) to read the latest documentation of ThreeFold.

## Create a farm

On Grid 3, farms are registered on the ThreeFold blockchain, TF Chain. To do this, you can use the Portal interface. No TFT is required for this process, but you will need an [account](dashboard_portal_polkadot_create_account) within the [Polkadot browser extension](dashboard_portal_polkadot_widget).

The Grid has three subnetworks, devnet, testnet, and mainnet. Devnet and testnet are used for testing updates to Zero OS before they are deployed to mainnet. You will need to use the same network for your farm and boot media. If you're not sure, choose mainnet.

Navigate to the appropriate portal for the network you are joining, linked below:

!!!include:dashboard_portal_list

### Activate account and create twin

A twin is a basic identity entity on TF Chain. Every farm belongs to a twin so you'll need one before creating your farm. Activate your account and [create a twin](dashboard_portal_ui_activation) using the buttons within the portal. There's no need to fill in an IP address, the default is fine. When prompted, sign the transaction using your Polkadot extension password.

### Create farm 

Next, select "Farms" from the left navbar and use the "Create Farm" button to create a farm. Again, sign the transaction and wait for the new farm to appear.

### Add Stellar address

Since TFT minting payouts are still performed on the Stellar network, you'll need to add a Stellar address to receive your farmed tokens. This Stellar account must have a trustline enabled for TFT. The ThreeFold Connect app wallet comes preconfigured this way and is a good option if you're not sure.

Use the caret icon to the left of your farm id to open the farm details. Then click the link to add a Stellar payout address and enter your Stellar public address starting with "G...". Hit save and sign the transaction.

### Prepare to boot

Make a note of your farm id, and proceed to [generating boot media](boot_media).