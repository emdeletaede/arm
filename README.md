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
