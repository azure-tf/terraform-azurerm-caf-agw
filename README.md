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

#### SKU Block
| Name | Type | Description |
| -- | -- | -- |
| Name | Required | TBC |
| Tier | Required | TBC |
| Capacity | Required |TBC |

#### Gateway_ip_configuration Block
| Name | Type | Description |
| -- | -- | -- |
| name | Required | TBC |
| subnet_id | Required | TBC |

#### Frontend_port Block
| Name | Type | Description |
| -- | -- | -- |
| name |Required |TBC |
| port |Required | TBC |

### Application Object
(Required) This object describes Appplication Settings for the deployed Application Gateway

### Application Object Parameters 

#### frontend_ip_configuration Block
| Name | Type | Description |
| -- | -- | -- |
|name | string | name of frontend ip |
|subnet_id | string | name of subnet where frontend IP is being deployed |
|public_ip_address_id | string | 

#### backend_address_pool Block
| Name | Type | Description |
| -- | -- | -- |
|name | string | backend pool name |

#### backend_http_settings Block
| Name | Type | Description |
| -- | -- | -- |
| name | string | backend http settings |
| cookie_based_affinity | 

#### http_listener Block
| Name | Type | Description |
| -- | -- | -- |

#### request_routing_rule Block
| Name | Type | Description |
| -- | -- | -- |
















   
  
 
