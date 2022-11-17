# QSFS Virtual Machine

Deploy a new virtual machine wiht QFSF on the Threefold Grid

!!!include:weblets_play_go
- Make sure you have an activated [profile](weblets_profile_manager) 
- Click on the **QFSF Virtual Machine** tab

__Process__ : 

![](img/qvm1.png)

- Fill in the instance name: it's used to reference the VM in the future.
- For now the QVM comes with 
  -  Ubuntu-22.04 image
  -  1 CPU 
  -  2 GB RAM
- `Public IPv4` flag gives the QSFS virtual machine a Public IPv4
- `Public IPv6` flag gives the QSFS virtual machine a Public IPv6
- `Planetary Network` to connect the QSFS Virtual Machine to Planetary network
- Choose the node to deploy on which can be
   - Manual: where you specify the node id yourself
   - Automatic: Suggests nodes list based on search criteria e.g `country`, `farm`, capacity..

![](img/qvm2.png)
Clicking on _Environment Variables_ then _Add_ button allows you to define environment variables to pass to the QSFS virtual machine. 
> Note the Public SSH key in the profile is automatically used as variable `SSH_KEY` passed to all Virtual Machines, so you have to activate SSH key on the [profile](weblets_profile_manager) 

### QSFS Disk
Clicking on _QSFS_ allows you to define QSFS configuration.
> For more information about QSFS, please consult [Quantum Safe Filesystem](https://library.threefold.me/info/manual/#/technology/threefold__qsfs)

