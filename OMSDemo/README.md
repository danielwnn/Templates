# Microsoft Operations Management Suite

Your time is precious, so here's a set of ARM templates that will deploy all of the OMS services, fully integrated, with running VM workloads attached to it.

### How to deploy

The main template will deploy resources into two different resource groups, and you can use the following PoweShell example to deploy:
	
	# Create 2 resource groups, for mgmt and workload
	
	$MgmtRg = New-AzureRmResourceGroup -Name OMS-Mgmt-RG -Location westeurope -Verbose
	$WorkloadRg = New-AzureRmResourceGroup -Name OMS-Workload-RG -Location westeurope -Verbose
	
	# Deploy template
	
	New-AzureRmResourceGroupDeployment -Name myDemo `
	                                   -ResourceGroupName $MgmtRg.ResourceGroupName `
	                                   -TemplateUri https://raw.githubusercontent.com/danielwnn/Templates/master/OMSDemo/azuredeploy.json `
	                                   -verbose 


### Post Deployment

Navigate to [Azure Portal](https://portal.azure.com) and find the newly created dashboard, which will have the following naming convention *AzureMgmt(uniqueString(deployment().name))*:
