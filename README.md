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
| zones | Optional | A collection of availability zones to spread the Application Gateway over.|
| ssl_policy | Optional | A ssl policy block as defined below. |
| enable_http2 | Optional |  Is HTTP2 enabled on the application gateway resource? Defaults to false. |

#### Identity Block
| Name | Type | Description |
| -- | -- | -- |
| type | Optional | The Managed Service Identity Type of this Application Gateway. The only possible value is UserAssigned. Defaults to UserAssigned. | 
| type | Required | Specifies a list with a single user managed identity id to be assigned to the Application Gateway. | 

#### SKU Block
| Name | Type | Description |
| -- | -- | -- |
| Name | Required | The Name of the SKU to use for this Application Gateway. Possible values are Standard_Small, Standard_Medium, Standard_Large, Standard_v2, WAF_Medium, WAF_Large, and WAF_v2. |
| Tier | Required | The Tier of the SKU to use for this Application Gateway. Possible values are Standard, Standard_v2, WAF and WAF_v2. |
| Capacity | Required |he Capacity of the SKU to use for this Application Gateway. When using a V1 SKU this value must be between 1 and 32, and 1 to 125 for a V2 SKU. This property is optional if autoscale_configuration is set. |

#### Gateway_ip_configuration Block
| Name | Type | Description |
| -- | -- | -- |
| name | Required | The Name of this Gateway IP Configuration.|
| subnet_id | Required | The ID of a Subnet. |

#### Frontend_port Block
| Name | Type | Description |
| -- | -- | -- |
| name |Required |The name of the Frontend Port. |
| port |Required | The port used for this Frontend Port. |

### Application Object
(Required) This object describes Appplication Settings for the deployed Application Gateway

### Application Object Parameters 

#### frontend_ip_configuration Block
| Name | Type | Description |
| -- | -- | -- |
|name | required | name of frontend ip |
|subnet_id | required | name of subnet where frontend IP is being deployed |
|private_ip_address_id | optional | The Private IP Address to use for the Application Gateway.|
|public_ip_address_id | optional | The ID of a Public IP Address which the Application Gateway should use.|

#### backend_address_pool Block
| Name | Type | Description |
| -- | -- | -- |
|name | Required | The name of the Backend Address Pool. |
|fqdns | Optional | A list of FQDN's which should be part of the Backend Address Pool. |
|ip_addresses | Optional | A list of IP Addresses which should be part of the Backend Address Pool. |

#### backend_http_settings Block
| Name | Type | Description |
| -- | -- | -- |
| name | Required | The name of the Backend HTTP Settings Collection. |
| cookie_based_affinity | Required | Is Cookie-Based Affinity enabled? Possible values are Enabled and Disabled. |
| affinity_cookie_name | Optional  | The name of the affinity cookie.  |
| path | Optional | The Path which should be used as a prefix for all HTTP requests. |
| port |Required | The port which should be used for this Backend HTTP Settings Collection. |
| probe_name |Optional | The name of an associated HTTP Probe.|
| protocol |Required | The Protocol which should be used. Possible values are Http and Https. |
| request_timeout |Required | The request timeout in seconds, which must be between 1 and 86400 seconds. | 
| host_name |Optional | Host header to be sent to the backend servers. Cannot be set if pick_host_name_from_backend_address is set to true. |
| pick_host_name_from_backend_address |Optional | Whether host header should be picked from the host name of the backend server. Defaults to false. |
| authentication_certificate |Optional |  One or more authentication_certificate blocks. |
|trusted_root_certificate_names| Optional | A list of trusted_root_certificate names. |
| connection_draining |Optional | to enable connection draining when enabled connection block is required

#### connection block 
| Name | Type | Description |
| -- | -- | -- |
| enabled | Required | If connection draining is enabled or not. |
| draining_timeout_sec | Required | The number of seconds connection draining is active. Acceptable values are from 1 second to 3600 seconds. |

#### http_listener Block
| Name | Type | Description |
| -- | -- | -- |
| name | Required |The Name of the HTTP Listener.|
| frontend_ip_configuration_name | Required | The Name of the Frontend IP Configuration used for this HTTP Listener. |
|frontend_port_name|Required| The Name of the Frontend Port use for this HTTP Listener. |
| host_name |Optional | The Hostname which should be used for this HTTP Listener.|
| protocol|Required | The Protocol to use for this HTTP Listener. Possible values are Http and Https. |
|require_sni  |Optional| Should Server Name Indication be Required? Defaults to false. |
|ssl_certificate_name |Optional | The name of the associated SSL Certificate which should be used for this HTTP Listener. |
|custom_error_configuration | Optional | One or more custom_error_configuration blocks as defined below. |


#### request_routing_rule Block
| Name | Type | Description |
| -- | -- | -- |
| name | Required | The Name of this Request Routing Rule. |
| rule_type  | Required | The Type of Routing that should be used for this Rule. Possible values are Basic and PathBasedRouting. |
| http_listener_name | Required | The Name of the HTTP Listener which should be used for this Routing Rule. |
|backend_address_pool_name | Optional | The Name of the Backend Address Pool which should be used for this Routing Rule. Cannot be set if redirect_configuration_name is set. |
|backend_http_settings_name| Optional |  The Name of the Backend HTTP Settings Collection which should be used for this Routing Rule. Cannot be set if redirect_configuration_name is set. |
|redirect_configuration_name | Optional |  The Name of the Redirect Configuration which should be used for this Routing Rule. Cannot be set if either backend_address_pool_name or backend_http_settings_name is set. |
|rewrite_rule_set_name | Optional | The Name of the Rewrite Rule Set which should be used for this Routing Rule. Only valid for v2 SKUs.|
|url_path_map_name| Optional |The Name of the URL Path Map which should be associated with this Routing Rule. |
















   
  
 
