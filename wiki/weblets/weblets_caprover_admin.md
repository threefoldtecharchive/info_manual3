# Manage Caprover

## Step 1: Enable https

![](img/enable_https_caprover.png)

You need to specify your email address.

You will have to login again.

![](img/caprover_https_activated.png)

> Now force https.

You will have to login again, and you should notice https is now used.

## Step 2: Deploy an app

![](img/deploy_app_caprover1.png)

just go to apps & follow the instructions, there is much more info on caprover website.


## Step 3: Enable monitoring

![](img/caprover_monitoring_start_.png)

You should now see

![](img/caprover_monitoring_2_.png)

## Step 4: Lets add nodes to caprover

- Go to the settings

![](img/caprover_cluster.png)

- Fill in your mnemonic from TF-Chain, make sure it's the right net you are connected to
- Add your SSH-key

Now go to `Cluster` :

![](img/cluster_add_nodes.png)

Specify the details of the resources you need and click on `Deploy` :

![](img/cluster_caprover_details.png)

You should then see something like

![](img/caprover_add_node2.png)

This should typically take less than 2 minutes.

> Important: the deployment process takes some time before it is known in CapRover.

Go out of the form and back to `Cluster`. 

![](img/cluster_added_caprover.png)

## Step 5: Change your password

- Go to `Settings` and change your password. This is important for your own security.   