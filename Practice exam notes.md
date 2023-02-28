
App service plan:
Didn't read the screenshots properly

App deployment performance issues:
Correct = swap slots
Can be reverted, swapping slot first to production slot confirms functionality
If changes swapped into prod dont work they can be switched back for last known good site.

Restoring VM from backup without agent:
File recovery can be done from any machine on the internet but VM1 and VM2 only is the answer due to potential capability with any other machine, previous or future OS etc.

Restoring VMs :
Create new or replace existing options only

Dns REcords: 
Created A records in auto registration will be private ips as a private zone in the same vnet
Same vnet, regardless of dns suffix will exist in same private azure dns zone

Auto registration for dns zones: 
all vms deployed in vnet will have dns records created to linked private dns zone
Auto registration cant take place if the dns zone isnt linked to a vnet. Vritual link needs to be created
	VNEts can only be linked to private dns zones
	i.e. vm registers only to private dns zones in auto registration

Vnet peering:
Connecting vnets as long as address space does not overlap
10.10.10.0 and 10.10.128.0 are different subnets

NSG:
Default blocks all incoming traffic
Deny/allow rules
If attach network interface option is available then vm is off
Allow rule with a high priority than a block rule will allow that target and then block all others


ASG:
Associated with VM nics for NSG targetting

AAD SSPR:
Only global admin can edit the security questions for SSPR

Case study questions:
1 app with minimised open ports and has sql database, web front end and processing. 5 vms. 
	More than 1 network is not necessary
There are 3 tiers here
	There needs to be 3 subnets. 1 for each tier. Restricted by NSG. Communication is possible through vnet.

Custom Roles:
assignable scopes can be made to any subscription, remove anything under the subscription since it'll be picked up at the top level.

Roles:
Reader and storage blob contributor, reader so that user can browse through the blobs, contributor so that user can upload to a container within a blob.

Locks:
Locks can only be placed on subscriptions, resource groups and resources.

Tags:
Tags can only be placed on Azure resources, resource groups and subscriptions.
Policy can apply tags automatically.
without remediation tasks then prior resources will not be affected by policy.
If tags are no inherited then only tags from policy are applied

Azure storage lifecycle management rules:
Archived means data cannot be read unless it is rehydrated. Blob is offline.
Data can be read in cool storage

On prem replication to azure:
A hyper V site, azure recovery services vault and replication policy are required.

VPN Gateway:
If changes are made after VPN client package is installed on windows client then it needs to be downloaded and installed again to apply latest changes.

Moving between subscriptions:
VM and associated resources can be moved
Also ASR Vault can be moved to new subscription

Azure marketplace:
Set/Get-AzMarketplaceTerms cmdlet for a given publisher to accept/reject terms

Cost analysis:
Tags need to be given to each resource for filtering, they can then be filtered inthe cost analysis blade by tag and a usage report can be downloaded.

Log analytics workspace:
Database search operator Event | search "error"/Event | where EventType == "error"/search in (Event) "error"
This language is Kusto.
Workspaces can be setup independent of the location and subscription where ASR vaults exist.

Traffic analytics:
Reader role can enable traffic analytics for an azure subscription. 

Azure file sync:
Sync groups contain 1 cloud endpoint or azure file share and at least one server endpoint.
AZfile sync does not support more than one server endpoint from the same server in the same sync group.
Multiple server endpoints can exist on the same volume if their namespaces do not overlap and the endpoints are syncing to unique sync groups, not the same sync group as per above comment.

Azure site recovery:
Storage accounts must be in same region as ASR vault

Storage:
Premium file shares can only be hosted in storage accounts called "filestorage account"
Tiering is only supported by blob storage and general purpose v2
Least cost method of redundancy is ZRS supported in v2/premium file/block storage. Not supported in V1.




