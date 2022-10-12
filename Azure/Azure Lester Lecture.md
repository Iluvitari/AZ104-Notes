Risky users page. Failed signins fine.
for seeing hacked usersWWFUK/Users/Lester March
azure is used for single sign on, logs logins for that in users as well
groups integral to office 365
main licenses used for users are 356
group DS_License_m365_E3 inheriting licenses from this groupno decommission process for leavers
in terms of licenses being freed UKLPCUPS01azure AD^^^^^
theres a cert for that


Resource group = blast container all the thtings that make up one particular serice. Everything that comprises that service makes up that resource group.

resoure group 01, dumping ground of crap

rg02 azure site recovery, disks replicated from vmware, in DR uses those disks whenever disaster happens to rebuild device in azure.

rg03 windows virtual desktip Lester playground

rg04 storage account for storing psd files

rg05 all dns zones, public dns zones. Managing dns in each zone, records for arena etc. 

front dooor designer > redirect url toloadbalancing Protocol
rg06 loganalytics workspace

rg07 logicapps container
rg08 azure virtual desktip
rg09 analytics

rg10, certicficate service vms - issuing ca 

rg11 logic apps dbs heavy use of nftp server, dump data there. Data services. sftp. automated through power shelll scripts. logic apps, power automate centralised. loic apps integrate with several services, way to build automation without righting any code.
sharepoint bot  

sharepoint site request, form, logic apps checks that sitre request and notifies you. 
logic apps: trigger > checking website, sharepoint site request, every 15 minute, if it finds new ite, slack connecter, post in triage sharepoint channel, then creates event calendar event created as well as posting message in slack.conditions as well, if statements, if posted to slack successfully, send email to requester and service desk.ifit didnt work it sends message to Leseter to say where it failed etc.

the history is very nice, shows a lot of information in each event for when it runs.

sharegate, migration from one sharepoint site to another.

rgsharepoint powershell script running in azure, picks up one sharepoint site is created, does some massage, lester becomes admin immediately and they do some styling for the website.

resource groups logical container for some service, should each have tags, created by , service its for.

portal settings > dark themm

dashboards are personal, I can create my own dashboard. can pin different pages/favourite different favourite it.
pin pins to dashboard 

recovery servives vaults


replicates data services to data services
wouk-afs on prem file server, replicate up to an azure storage account, other server pools down, all data on prem, all in azure, and in azure storage account, lots of redundancy. on prem gets backced up by veam and azure fileserver gets backed up to. 2 servers registered to storage sync service. wwfuk0afs01.wwfk.internal.

manitauins itself. 

ifwe added new fileshare we could add another sync group. 

woukafs, azure file sync.

recovery services faults DR like zerto

one rsv01 > backup part/dr part. Backup fileshares, connects to sotrage account that azure syncs to then backs them up.

resortre file hre then in veam. Lots easier.

backup sql. backing up hole M drive, M drive is backup drive. Script that runs on sql that backsu p databases to M.

wwwfuk-asrcon02 site recovery infrastructure congiruuration servers.

recovery services vaults ,rsv01, overview diagram shows the flow of recovery and all things that are onnected.

shows for each VM and its path of recovery and why it mayfail etc.

each vm has agent installed on vm for that recovery. 

updates pushed out through service account.

compute and network - which subnet to restore to once restored, what ip it should have after it comes up.

netbo all vms protected in netbox will ave two network interfaces. DR subnet, 10.99.34/82 

azure virtual desktop, LM making more of a reality, still work in progress. 

DR and FileSync - main services.

365 admin center 
some things you can do here that you cant do in azure ad, but slowly they are making it the same. or more in azure AD even.

exchange. Everything should be managed from office 365 side. Mailbox appears in exchange.  office 365, everything under hood is exchange.



