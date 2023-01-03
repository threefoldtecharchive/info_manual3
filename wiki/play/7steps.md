Tutorial: Deploying a Terraform Configuration on the Threefold Grid (Windows) 

In this tutorial, you will learn how to install Terraform, create a configuration file, and use Terraform to deploy infrastructure on the Threefold Grid from a Windows computer. By the end of this tutorial, you will have deployed a network and two virtual machines (VMs) on the Threefold Grid. 

Prerequisites 

Before you begin, you will need the following: 

A Windows computer with the following software installed: 

Git for Windows 

Terraform for Windows 

A Threefold Grid mnemonic phrase. This is used to generate the seed for your node. You can get a mnemonic phrase by creating a Threefold Grid account. 

An SSH key. This will be used to securely connect to the VMs you create. If you don't already have an SSH key, you can generate one using the ssh-keygen command in Git for Windows. 

Step 1: Create a Configuration Directory 

Create a new directory where you want to store your Terraform configuration. This directory can be named anything you like. In this tutorial, we will create a deployments directory and a testdeployment subdirectory inside of it. 

From the Git for Windows command prompt: 

Copy code 

mkdir deployments 
mkdir deployments\testdeployment 
 

Step 2: Create the main.tf File 

Copy the contents of the provided main.tf file and write it to the testdeployment directory you just created. 

Copy code 

notepad main.tf 
# paste the contents of the main tf then save and close the file 
 

Step 3: Initialize the Directory as a Terraform Configuration Directory 

From the Git for Windows command prompt, navigate to the testdeployment directory where you placed the main.tf file. 

Copy code 

cd deployments\testdeployment 
 

Run the following command to initialize the directory as a Terraform configuration directory and install the required provider(s): 

Copy code 

terraform init 
 

Step 4: Create the Infrastructure Resources 

To apply the changes specified in the configuration and create the resources defined in main.tf, you will need to provide values for the variables in your configuration. You can do this by creating a .tfvars file and specifying the values you want to use. 

For example, you might create a file called env1.tfvars and include the following contents: 

Copy code 

MNEMONICS = "your mnemonic phrase here" 
NETWORK = "main" 
TF_PARALLELISM = 2 
SSH_KEY = "your ssh key here" 
 

To use this file, pass the -var-file flag to the terraform apply command, followed by the path to the file: 

Copy code 

terraform apply -var-file="deployments\env 

Step 5: View the Output Values 

After the resources have been created, you can view the output values by running the following command: 

Copy code 

terraform output 
 

This will display the values of the output variables defined in the main.tf file. In this example, the output values include the WireGuard configuration for the network, and the IP addresses of the VMs. 

Step 6: Test Your Deployment 

To test your deployment, you will need to use an SSH client to connect to the VMs. We recommend using PuTTY with agent forwarding and your SSH key. 

Download and install PuTTY. 

Open PuTTY and enter the IP address of the VM you want to connect to in the "Host Name" field. 

Under "Connection", expand "SSH" and select "Auth". 

Click the "Browse" button next to "Private key file for authentication" and select the path to your SSH key. 

Under "Connection", expand "SSH" and select "Tunnels". 

In the "Forwarded ports" field, enter "AUTH_SOCK" in the "Source port" field and "localhost:AUTH_SOCK" in the "Destination" field. Then click the "Add" button. 

Click the "Open" button to open the connection to the VM. 

When prompted, enter your username (ubuntu) and press Enter. 

Step 7: Clean Up Your Deployment 

When you're finished testing your deployment, you can clean up the resources you created by running the following command: 

Copy code 

terraform destroy -var-file="deployments\yourfile.tfvar" 

Conclusion 

In this tutorial, you learned how to install Terraform, create a configuration file, and use Terraform to deploy infrastructure on the Threefold Grid from a Windows computer. You also learned how to use .tfvars files to provide values for the variables in your configuration, and how to view the output values of your deployment and clean up your resources when you're finished. 

I hope this tutorial was helpful! If you have any questions or need further assistance, please don't hesitate to ask. I'm happy to help you get started with Terraform and deploying your infrastructure on the Threefold Grid. 

I invite you to join us in building on the Threefold Grid in 2023! 

 
