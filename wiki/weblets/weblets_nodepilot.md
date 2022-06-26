# NodePilot

This is a simple instance of upstream node-pilot: https://nodepilot.tech

When using the [flist](https://hub.grid.tf/maxux42.3bot/maxux-nodep.flist) you get a node pilot instance ready out-of-box. You need to get a public ipv4 to get it to works.

When the VM is deployed, go to https://publicip and configure your node-pilot. You can upload a backup to the VM via ssh as well if you have a backup of a previous instance.

What change compared to upstream node-pilot, we have out-of-box a transparent pre-filled blockchain database for some blochain (currently Fuse and Pokt as proof-of-concept). You can start one of theses blockchain in no-time and it will be automatically nearly sync already without the requirement of the full space locally nor downloading everything and killing bandwidth.


#TODO: update weblets docs