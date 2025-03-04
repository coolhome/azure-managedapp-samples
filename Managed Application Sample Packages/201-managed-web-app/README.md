# Managed Web Application (IaaS) with Azure management services

>Note: This sample is for Managed Application in Service Catalog. For Marketplace, please see these instructions:
[**Marketplace Managed Application**](https://docs.microsoft.com/en-us/azure/managed-applications/publish-marketplace-app)

## Deploy this sample to your Service Catalog

### Deploy using Azure Portal

Clicking on the button below, will create the Managed Application definition to a Resource Group in your Azure subscription.

[![Deploy to Azure](http://azuredeploy.net/deploybutton.png)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Fazure%2Fazure-managedapp-samples%2Fmaster%2FManaged%2520Application%2520Sample%2520Packages%2F201-managed-web-app%2Fazuredeploy.json)

### Deploy using PowerShell

Modify the snippet below to deploy Managed Application definition to a Resource Group in your Azure subscription

````powershell
$rgname = "<yourRgName>"
$location = "<rgLocation>"
$authorization = "<principalId:roleDefinitionId>"
$uri = "https://raw.githubusercontent.com/Azure/azure-managedapp-samples/master/Managed Application Sample Packages/201-managed-web-app/managedwebapp.zip"

New-AzManagedApplicationDefinition -Name "ManagedWebApp" `
                                   -ResourceGroupName $rgname `
                                   -DisplayName "Managed Web App" `
                                   -Description "Managed Web App with Azure mgmt" `
                                   -Location $location `
                                   -LockLevel ReadOnly `
                                   -PackageFileUri $uri `
                                   -Authorization $authorization `
                                   -Verbose
````

### Deploy using AzureCLI

Modify the snippet below to deploy Managed Application definition to a Resource Group in your Azure subscription

````azureCLI
az managedapp definition create \
  --name "ManagedWebApp" \
  --location <rgLocation> \
  --resource-group <yourRgName> \
  --lock-level ReadOnly \
  --display-name "Managed Web Application" \
  --description "Web App with Azure mgmt" \
  --authorizations "<principalId:roleDefinitionId>" \
  --package-file-uri "https://raw.githubusercontent.com/Azure/azure-managedapp-samples/master/Managed Application Sample Packages/201-managed-web-app/managedwebapp.zip"
````