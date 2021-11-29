!!!include:grid3_javascript_loadclient

## Deploying Caprover Leader Node

### Example code

!!!code url:https://github.com/threefoldtech/grid3_client_ts/blob/development/scripts/caprover_leader.ts



### Detailed explanation


#### building network

```javascript
// create network Object
const n = new NetworkModel();
n.name = "montest";
n.ip_range = "10.232.0.0/16";
```
Here we prepare the network model that is going to be used by specifying a name to our network and the range it will be spanning over


### building the disk model

```javascript
// create disk Object
const disk = new DiskModel();
disk.name = "newDisk";
disk.size = 100;
disk.mountpoint = "/testdisk";
```
here we create the disk model specifying its name, size in GB and where it will be mounted eventually

### building the VM

```javascript
// create vm node Object
const vm = new MachineModel();
vm.name = "testvm";
vm.node_id = 14;
vm.disks = [disk];
vm.public_ip = true;
vm.planetary = false;
vm.cpu = 4;
vm.memory = 1024 * 4;
vm.rootfs_size = 10;
vm.flist = CAPROVER_FLIST;;
vm.entrypoint = "/sbin/zinit init";
vm.env = {
    PUBLIC_KEY:
        "ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABgQDF7MKO2kjhnc3K02hsvJrMofIc8aploPsbPXzPZgeegd4sVJiGzdnTfiTjNUl7mdvct2FpoBBWQd9SeiLAW592CHMP9pOXO2CzOi/xNBrar7TnBc6nNnPjbd9bQEgLK9b2LQLCzLmZQmTWJolPETrkWcCLt4fmTchxHKROoRG6TOfAW2rieJSY8yj1+xtvjIHtFceD7vNByI62kOTzdlzOVmiGZ+9gkBJHSRTZkWniaACg0Mt3R9Xq6q6XHpIPTGqSOXeundPpaw+z+PUBc42Aa+LIgV2aoZP00yokx7WCttG3tS+xLv/6pEmIst5b/m4WNMkBx9fkGEIM4eaAH2mFXNc0bQNQJVqXEQSi7DWecWzNkHKDqRN6HoN/BAUF+clKW3fkvWme8iE8XK9xRCiNc8G3sQh2xIajKj0UbKn88k1fYMughJye93Q82mKXFw5QU3S0GzH/YoOEWhXUO8N76zZz+jyjYg9VBy/AU8lm1UJxAjiANIydkXjBFFofLh8= rafy@rafy-Inspiron-3576",
    SWM_NODE_MODE: "leader",
    CAPROVER_ROOT_DOMAIN: "rafy.grid.tf",
    DEFAULT_PASSWORD: "captain42"
};

```
Now we go to the VM model, that will be used to build our `zmachine` object

We need to specify its
- name
- node_id: where it will get deployed
- disks: disks model collection
- memory
- root filesystem size
- flist: the image it is going to start from. Check the [supported flists](grid3_supported_flists)
- entry point: entrypoint command / script to execute
- env: has the environment variables needed e.g sshkeys used
- public ip: if we want to have a public ip attached to the VM
- planetary: to enable planetary network on VM

###### Env. variables in Leader Node
- PUBLIC_KEY: Your public IP to be able to access the VM.
- SWM_NODE_MODE: Caprover Node type which must be `leader` as we are deploying a leader node.
- CAPROVER_ROOT_DOMAIN: The domain which you we will use to bind the deployed VM.
- DEFAULT_PASSWORD: Caprover default password you want to deploy with.



### building VMs collection


```javascript
// create VMs Object
const vms = new MachinesModel();
vms.name = "newVMS5";
vms.network = n;
vms.machines = [vm];
vms.metadata = "{'testVMs': true}";
vms.description = "test deploying VMs via ts grid3 client";
```


### deploy

```javascript
// deploy vms
const res = await grid3.machines.deploy(vms);
console.log(JSON.stringify(res));
```

### get deployment information

can do so based on the name you gave to the `vms` collection
```javascript
// get the deployment
const l = await grid3.machines.getObj(vms.name);
console.log(JSON.stringify(l));
```


### deleting a deployment

```javascript
// // delete

const d = await grid3.machines.delete({ name: vms.name });
console.log(d);
```
In the underlying layer we cancel the contracts that were created on the chain and as a result all of the workloads tied to his project will get deleted.


For further details about Leader node deployment please [check](https://github.com/freeflowuniverse/freeflow_caprover#a-leader-node-deploymentsetup)


## Deploying Caprover Worker Node

### Example code

!!!code url:https://github.com/threefoldtech/grid3_client_ts/blob/development/scripts/caprover_worker.ts


Before worker node deployment:
 - Get token from the leader node
 - Get leader node public IP

  For futher inforamtion please [check](https://github.com/freeflowuniverse/freeflow_caprover#step-4-access-the-captain-dashboard)


to deploy a worked Node it has the same details as a leader node regarding the deployment details except:

- In building VMs collection

```javascript
// create VMs Object
const vms = new MachinesModel();
vms.name = "newVMS6";
vms.network = n;
vms.machines = [vm];
vms.metadata = "{'testVMs': true}";
vms.description = "test deploying VMs via ts grid3 client";
```

in `vms.name` use different name from the leader node VM to prevent any conflicts

- In building the VM
```javascript
const vm = new MachineModel();
vm.name = "capworker1";
vm.node_id = 14;
vm.disks = [disk];
vm.public_ip = true;
vm.planetary = false;
vm.cpu = 4;
vm.memory = 1024 * 4;
vm.rootfs_size = 10;
vm.flist = CAPROVER_FLIST;
vm.entrypoint = "/sbin/zinit init";
vm.env = {
    // These env. vars needed to be changed based on the leader node.
    PUBLIC_KEY:
        "ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABgQDF7MKO2kjhnc3K02hsvJrMofIc8aploPsbPXzPZgeegd4sVJiGzdnTfiTjNUl7mdvct2FpoBBWQd9SeiLAW592CHMP9pOXO2CzOi/xNBrar7TnBc6nNnPjbd9bQEgLK9b2LQLCzLmZQmTWJolPETrkWcCLt4fmTchxHKROoRG6TOfAW2rieJSY8yj1+xtvjIHtFceD7vNByI62kOTzdlzOVmiGZ+9gkBJHSRTZkWniaACg0Mt3R9Xq6q6XHpIPTGqSOXeundPpaw+z+PUBc42Aa+LIgV2aoZP00yokx7WCttG3tS+xLv/6pEmIst5b/m4WNMkBx9fkGEIM4eaAH2mFXNc0bQNQJVqXEQSi7DWecWzNkHKDqRN6HoN/BAUF+clKW3fkvWme8iE8XK9xRCiNc8G3sQh2xIajKj0UbKn88k1fYMughJye93Q82mKXFw5QU3S0GzH/YoOEWhXUO8N76zZz+jyjYg9VBy/AU8lm1UJxAjiANIydkXjBFFofLh8= rafy@rafy-Inspiron-3576",
    SWM_NODE_MODE: "worker",
    SWMTKN: "SWMTKN-1-1eikxeyat4br9t4la1dnln11l1tvlnrngzwh5iq68m2vn7edi1-6lc6xtw3pzd99lrowyuayr5yv",
    LEADER_PUBLIC_IP: "185.206.122.157",
};
```
###### Env. variables in worker Node
- PUBLIC_KEY: Your public IP to be able to access the VM.
- SWM_NODE_MODE: Caprover Node type which must be `worker` as we are deploying a worker node.
- SWMTKN: Token generated on the leader node to allow the worker node to join the docker swarm network 
- LEADER_PUBLIC_IP: Leader node public IP.
