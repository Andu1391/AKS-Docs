# README.MD
## Steps to Set Up an AKS Cluster with a Windows Profile and Connect Using Azure Bastion
### 1. Create a Resource Group
```sh
az group create --name myResourceGroupTest --location eastus
# Create an AKS Cluster with a Windows Profile
az aks create --resource-group myResourceGroupTest --name myAKSCluster --node-count 1 --enable-addons monitoring --generate-ssh-keys --windows-admin-username azureuser --windows-admin-password "YourPassword123!" --network-plugin azure
# Add a Windows Server 2022 Node Pool
az aks nodepool add --resource-group myResourceGroupTest --cluster-name myAKSCluster --os-type Windows --name npwin --node-count 1 --os-sku Windows2022
# Create an Azure Bastion Host
Navigate to the Azure portal.
Go to the virtual network where your AKS cluster is deployed.
Select Bastion from the left-hand menu and click Create.
Fill in the required details and create the Bastion host.
# Connect to a Windows Node
In the Azure portal, go to your AKS cluster.
Select the Node pools tab and choose the Windows node pool.
Select Instances and choose a Windows node.
Click on Connect and then select Bastion.
Enter the credentials you set up when creating the AKS cluster and click Connect.
