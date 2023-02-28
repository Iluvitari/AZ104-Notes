
App service plan:
Didn't read the screenshots properly

App deployment performance issues:
Correct = swap slots
Can be reverted, swapping slot first to production slot confirms functionality
If changes swapped into prod dont work they can be switched back for last known good site.

Restoring VM from backup without agent:
File recovery can be done from any machine on the internet but VM1 and VM2 only is the answer due to potential capability with any other machine, previous or future OS etc.

Restoring VMs : Create new or replace existing options only

Dns REcords: Created A records in auto registration will be private ips as a private zone in the same vnet
Same vnet, regardless of dns suffix will exist in same private azure dns zone

Auto registration for dns zones: all vms deployed in vnet will have dns records created to linked private dns zone
Auto registration cant take place if the dns zone isnt linked to a vnet




