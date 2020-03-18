# terraform-azurerm-caf-agw

This module creates an Application Gateway with multiple application configurations


    * 1 to many application settings 
    
Reference the module to a specific version (recommended):



Link to terraform provider
         * Application Gateway https://www.terraform.io/docs/providers/azurerm/r/application_gateway.html
         
## Inputs 
| Name | Type | Default | Description
| -- | -- | -- | -- |
|resource_group_name |string | None | Name of the resource group where to create the resource. Changing this foreces a new resoruce to be created. |
| location | string | None | Specifies the Azure location to deploy the resource. Changing this forces a new resource to be created. |
| app_gw_object | object | None | Application Gateway Object as described in the parameters section |
| app_object    | object | None | Application object as described in the parameters section  |
| tags | map | None | Map of tags for the deployment|

## Parameters

### Application-Gateway-Object
(Required) Configuration object describing the Application Gateway resource being deployed
The object has the following sections :

#### Application Gateway Parameters 
| Name | Type | Description |
| -- | -- | -- |
| Name | Required | The name of the Application Gateway being deployed |
| resource_group_name | Required | The name of the resource group the Application Gateway is being deloyed in |
| location | Required | The region in which the Application Gateway will be deployed into |
| tags | Required | A mapping of tags to assign to the Application Gateway |
| identity | Optional | TBC | 
| zones | Optional | TBC |
| ssl_policy | Optional | TBC |
| enable_http2 | Optional | TBC |
| SKU Name | Required | TBC |
| SKU Tier | Required | TBC |
| SKU Capacity | Required |TBC |
| Gateway_ip_configuration name | Required | TBC |
| Gateway_ip_configuration subnet_id | Required | TBC |
| Frontend_port name |Required |TBC |
| Frontend_port port |Required | TBC |

### Application Object
(Required) This object describes Appplication Settings for the deployed Application Gateway

### Application Parameters 

| Name | Type | Description |









   
  
 
