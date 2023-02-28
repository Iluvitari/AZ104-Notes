
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









