
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
For sub domains name servers need to be configured for internet top level domain DNS to direct queries.

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
If no NSG then all traffic allowed
You can hold one NSG on multiple subnets, vms,nics

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
Backups can only be done for resources in the same region and storage blobs cannot be backed up to service vaults
Backup pre-check may warn if the vm agent is not up to date.

Storage:
Premium file shares can only be hosted in storage accounts called "filestorage account"
Tiering is only supported by blob storage and general purpose v2
Least cost method of redundancy is ZRS supported in v2/premium file/block storage. Not supported in V1.
v1 and v2 only for table storage
v1,v2 and blobstorage for blob storage

Alerting:
Alert rules ca be configured to send emails and sms. 
They are however rate limited and only 100 emails can be sent an hour. Only 1 sms can be sent in 5 minutes.

Kubernetes:
Azure Portal and Azaks command can be used for cluster autoscaler config
	AZ AKS is for AKS cluster config
	In portal we can configure under node pools
Autoscaling aks is referring to nodes, scaling nodes.
AKS cluster uses calico network, policies are to be configured here instead of azure network for restricting network traffic to pods.

Docker:
Docker push for deploying app to cluster

Proximity placements:
Proximity placements can only be associated with RGs in the same region.

MFA usage model:
Not possible to change the usage model of existing provider
A new one must be created from new provider
Cant change usage model after an MFA provider is created

Load balancing:
Back end pools and health probes are added by network contributors
To target a specific client for each request through load balancer a session percistence to a client IP needs to configuring
Backend pools can only have vms attached with standard sku public ip config or no ip config. Dynamic public ip means basic sku ip no standard.
Before load balancing rules can be created a backend pool and health probe must be configured.

Oauth:
Required for AKS auth from aad

Root management group:
Global admin needs assignment to access then then azure roles can be assigned to users to manage it.

External identities in AAD:
Adjust guest user settings, their access and who can invite them from , external collaboration settings in users.

Azure Import/export:
Can only be done for gen purpose v2 storage acounts, blob storage accounts and gen v1 storage accounts.
Supported only or importing blob and file, exportin blob
Azure blob storage/azure file storage can be destinations of imported data

Azure monitor:
Monitoring agent must be installed on vm 
Log analytics is then the source of alerting after log analytics workspace is configured
Azure log analytics must be target resource for monitoring in alert rule, in this example for system event logs. < for log based alerting.

Network Watcher:
To record successful connection attempts to vms we need an azure storage account, registered microsoft.insights andenabled azure network watcher flow logs.
It is network traffic that flows through an nsg, nsg must be configured

Availability:
Seperate availability zone for each vm in an app build, zones protect from datacenter level failures, sets are datacenter configuration to provide vm redundancy and availability.


Protection from SQL injection:
Application gateway using WAF tier - web application firewall. Centralised protection of web application from common exploits and vulns.

Desired state configuration:
Requires VM to be on for extension to communicate

Azure DNS ZOnes:
Zones can be imported and exported by Az CLI, scripts are availability for administrative ease.

NICS:
Nic must be created in the same region as vnet

IP Flow verify:
To identify security rule preventing network packet from reaching Az vm.

VM:
Connection outbound from vm to external host can be troubleshooted with connection troubleshoot.

VM scale sets/availability sets:
VM scale set consists of a set of identically configured vms, availability set is for a set of discrete vms. 
2 machines upgrading at anytime will mean 8 remaining up in a scale set. One availability set with 10 vms should be appropriate for an app deployment using 10 vms with no more than 2 down at one time for upgrades.

ARM template:
Parameter platform-fault-domain-count, for setting as many as possible vms to be up in the case of a failure "maxvalue" should be configured.
Maximum of 20 update domains can be assigned to availability set. 5 by default, this indicates groups of vms and hardware that can be rebooted at the sametime.

Express route:
SKU ErGw3AZ for FastPath
Skus:
-   Standard
    
-   HighPerformance
    
-   UltraPerformance
    
-   ErGw1Az
    
-   ErGw2Az
    
-   ErGw3Az