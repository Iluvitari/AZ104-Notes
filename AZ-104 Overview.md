# Overview 
Source: https://www.youtube.com/watch?v=VOod_VNgdJk

## Things to do:
Microsoft learn
John Savill's master class
PluralSight 
Mocks

# [[Azure AD]]
## Identity
Identity provider for cloud services - [[Azure AD]]
### Cloud Protocols:
- OIDC
- SAML
- WS-FED

### Authorisation:
- Oauth2

Function over HTTPS/work over internet

### Applications talking to [[Azure AD]] (talk programatically):
- Rest API
- MSGRAPH

SaaS > use [[Azure AD]] as identify provider
Azure/Microsoft 365 > use [[Azure AD]] as identify provider

### On-premise AD: 
Authentication:
- kerberos
- NTLM
Programatic:
- LDAP

On-Prem doesn't work well for internet

No DC for [[Azure AD]]

## AAD Connect and customization:

### Synchronisation Onprem to Cloud:
- AAD connect/AAD connect cloud sync: AD source of truth but replicated to AAD.

###  Customisation
- Company branding
- Logon text/images/logos

## Tenant:
= Default name/Primary domain name
- Can add custom domain name.

- AAD lives outside of subscriptions.
- subs trust the AAD instance.
- Domain Applications are told what AAD instance is trusted as the source of identity.

## Users:

- Directory synced: Yes/No - Yes it came from on prem AD via AAD Connect
- Guest accounts
	- Example: Different Azure AD tenant/gmail/msa > can be added as guest users in AAD.
	- Authorization controlled at AAD
	- Objects then can be given permissions for connected applications and services.
- New user/invite user (guest user from gmail, another aad instance etc)
- wont replicate back to on prem.
- Bulk creation:
	- csv template for bulk users.
	- also powershell can bulk create via script
- Add users to groups
	- Give group permission to resource

## Groups:
- Can replicate from on-prem to aad
- Cloud groups (not from on-prem):
	- Groups can be dynamic, automatically added to groups based on some defined attributes/rules defined in "***Dynamic membership rules***"
	- Assigned (manually added)
	- Dynamic (automatically added)
	- Cant manually add to dynamic group
- Azure AD roles
	- When creating group, yes indicates azure ad roles can be assigned
		- Group can't be dynamic with this enabled

## Devices:
- Make it known to AAD:
	- Register:
		- known+manage (e.g. intune)
	- Join (register+)
		- login with AAD users (direct authentication)

## Conditional access
- Rules enforced on Azure AD that determine what can be accessed by who.
	- From certain locations
	- Have to have MFA

## AAD SKus:
- Different subscriptions. Bring different capabilities
- Free sku can replicate ad to AAD. 
- Can only password write back to AD with premium license

## Self service password reset
- Link to reset password themselves
- password reset > self service password reset, can define what groups have this options.
- Methods used for password reset can be defined. Email, questions for example.

## Permissions/Roles
- Roles and Administrators in AAD
	- Descriptions provided of what roles do when going into them
	- Roles = permission sets
		- Global

## Administrative units
 - Roles in AAD - Global. Administrative units > add users/groups to it.
- Cant manage people in the group when group is added to admin unit.
- Administrative roles delegated through administrative unit. 
- Manage attributes of the group but no management of people in group. A way of delegating some administrative permissions. For example: help desk.

# [[Azure Subscriptions]]:
- Each sub *trusts* particular AZAD Tenant
- Azure is consumption based
	- Pay for what you use
	- Autoscale

## Cost analysis and budget
- Cost management and billing
	- management > cost analysis
	- Budget can be set.
		- alerts

## Resource Groups
- Resources inside group
	- vms
	- load balancer
- Group them by common life cycle
- Roles and permissions set at levels down from resource group
- Budget can be applied at resource group

## Management groups
- Root management group
	- dev - prod
		- locations
			- subs

## Tagging
- Key value pair
- Resources/resource groups/subscriptions
- metadata
- Tags do not inherit down.
	- policies can make children inherit tags from parent.

## Policies
- Guard rails
	- These are the acceptable things to do
- Policy can be created at management/resource/subscription
- Enforced at azure resource manager
- It can remediate if somethings out of policy.
- Create/assign an initiative normally
- Can see compliance of these policies
- Allowed locations can be selected in parameters of policies.

## Roles
- Resource based access control
- Assign role to an identity at a certain scope.
	- Role assignment.
- Scope could be management, resource group. rarely individual resources.
- Separate from AAD
- Custom roles can be added
	- Roles are list of permissions
	- Mainly at control plane
	- Actions set from the preset roles. Can be customised.
- Data plane roles do exist

## Control and data plane
- Control -> ARM Azure Resource Manager
	- Resources under ARM have actions in the data plane
- Actions and dataactions - control - dataplane

## Activity log
- Resources
	- At control plane
- Can be filtered to role assignments for example under operations.

# [[Regions and Networking]]
## Regions
- When creating a resource, needs to be picked
- Huge network around world
	- Regions
		- Latency envelope
		- Different data centers in each region
- `Get-AzEnvironment`
	- Can show different cloud environments
	- Primarily deal with Commercial cloud.
- Availability zone
	- logical mappings
	- independent power/cooling/networking
	- fail over
	- zone redundant-distributed
	- zonal-in specific Az
- Pick region based on consumption

## Paired regions
- Asynchronous
- replication
- Azure key vault
- check regional pairs for DR

## Egress
- Generally pay for Egress not ingress
- Recommended watching AZ-700 video

## Virtual network
- Within sub/region
- Broken down to sub nets
- IPv4 and Ipv6 (-rfc1918 common.)
	- Private ip ranges
- Use unique IP space to communicate on prem
- For each sub net lose 5 IPs.
	- Net address
	- Broadcast
	- GW
	- DNS
- DHCP allocates first available private IP to resource created in subnet
	- Default can outbound to internet


## Public Ips
 - Public IP to loadbalancer to allow reachability in rather than assign directly to resource
- Public Ips are bound to regions
- 2 types of public ip
	- IPv4
	- Ipv6
- Standard is zone redundant
- For setting ips statically > tell azure fabric what specific ip to assign when resource reaches out to DHCP
	- Guest is unaware > set to dchp

## vNet peering
- More than 1 virtual network to talk
- Could be different subscription/tenant that it trusts
- Regular peering or Global peering for different regions
- Different IP ranges
- Peering virtual networks required on the networks being peered
- Other vNets can allow gateway transit so they can use the remote gateway and traffic can reach other locations.
- vNets cant normally talk to each other and rather need a mesh of peers to work.

## Network security groups (NSG)
- Restrictions for communications
- Multiple rules
	- Priority
	- rule name
	- SRC & DEST
		- IP
		- Service tag
		- ASG
		- vNets
	- Port
	- Actions: Allow/Deny
- By default:
	- VirtualNetwork (Known IP space of vNet)
		- Can communicate inside Any/Any
	- Allows Loadbalancer communication
	- Deny everything else.
- Associate NSGs with particular subnets
- Effective security rules shows NSGs in effect
	- Effective routes as well

## Firewalls and routing
- NSG doesnt understand fqdn only operates level 4
- Azure firewall does
	- Resource deploys in to its own network
- Own rules
	- Nat
	- network l4
	- application l7
- restricting and controlling traffic
	- Create routing tables
	- defining routes
	- connecting to subnet

## Azure DNS
- Public
	- host name records associated with ips
		- cnames associated with the host
- Private
	- can be registered to vnets
		- auto registered
	- vnets can associate with private zones for resolving records

## site 2 site vpn
- Requires gateway subnet /27
- can connect to any DC
- 2 different types of vpn
	- Policy
		- Itunnel
	- Route (dynamic)
		- any n tunnels
		- point 2 site vpn configurable
- On prem gateway requires set up which supplies public IP representative of the network to connect then to azure gateway vpn

## Express Route
- not encrypted
	- can run vpn gw over  ER
- Runs on the azure backplane network
- Meet me points across the network are where gateway will connect
	- This is private peering.
- This then uses a service called global reach to talk to other meet me points across the express route.
	- Can be other locations we run eg
- Talking to the internet it will talk from meet me point and pass back through gateway.
	- Gateway is not used when talking to meet me point
- Microsoft peering
	- a service for route filtering for bgp purposes
	- create a filter and add locations and services wanted to utilize the filter, add a circuit which will then offer chosen services

## Virtual WAN
- Instead of ER
- Basic
	- s2s
- STD
	- E/R
	-  s2s
	- P2S VPN
	- Vnets peered
		- with transitive communication
	- Can connect to another vwan
- With virtual routing we can skip multiple hops where resource nics cant span multiple networks.

## Service Endpoints
- Subnets require service endpoints
	- Will be flagged when associating resources with a subnet
- Flow to PAS services
	- Control of flow to outside the vnet
- allowed access from private ip range
	- Making a private IP known to a service

## Private Endpoints
- Allows connection from all different places
- Private endpoint connections tab in networking
	- Just an IP with blob that can be cnamed in dns
- Private endpoint aliases to private link connection
- Can add a service that is in a vnet which overlaps your vnet

## Azure Load Balancer
- "Azure Load Balancer"
	- protocol/port/ip
		- pools
- Rules
	- 5,3,2 tuples
	- Nat rule
	- Matches > move to pool
- Free/standard pricing
	- free = non redundant

## Azure App Gateway
- L7
	- Http/s
		- Websockets
- Listener > ssl/cert
	- Rules
- Multisite
	- fqdn>rule
- Rule
	- Bask
	- Path
	- rewrite
- Allow traffic route to Backend pools.


# [[Storage]]

# [[Virtual Machines]]





