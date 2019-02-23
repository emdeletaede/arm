# arm
# Using linked templates when deploying Azure resources
## External template and external parameters  

To link to an external template and parameter file, use templateLink and parametersLink. When linking to a template, the Resource Manager service must be able to access it. You can't specify a local file or a file that is only available on your local network. You can only provide a URI value that includes either http or https. One option is to place your linked template in a storage account, and use the URI for that item.

```json
"resources": [
  {
     "apiVersion": "2017-05-10",
     "name": "linkedTemplate",
     "type": "Microsoft.Resources/deployments",
     "properties": {
       "mode": "Incremental",
       "templateLink": {
          "uri":"https://mystorageaccount.blob.core.windows.net/AzureTemplates/newStorageAccount.json",
          "contentVersion":"1.0.0.0"
       },
       "parametersLink": {
          "uri":"https://mystorageaccount.blob.core.windows.net/AzureTemplates/newStorageAccount.parameters.json",
          "contentVersion":"1.0.0.0"
       }
     }
  }
]
```
## Understand the schema
1. From VS Code, collapse the template to the root level. You have the simplest structure with the following elements:
Resource Manager template simplest structure
![Image elements](https://docs.microsoft.com/en-us/azure/azure-resource-manager/media/resource-manager-tutorial-create-encrypted-storage-accounts/resource-manager-template-simplest-structure.png)
* **$schema**: specify the location of the JSON schema file that describes the version of the template language.
* **contentVersion**: specify any value for this element to document significant changes in your template.
* **parameters**: specify the values that are provided when deployment is executed to customize resource deployment.
* **variables**: specify the values that are used as JSON fragments in the template to simplify template language expressions.
* **resources**: specify the resource types that are deployed or updated in a resource group.
* **outputs**: specify the values that are returned after deployment.
2. Expand resources. There is a Microsoft.Storage/storageAccounts resource defined. The template creates a non-encrypted Storage account.
Resource Manager template storage account definition
