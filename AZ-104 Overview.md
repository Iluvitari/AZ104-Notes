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

## Tenant:
= Default name/Primary domain name
- Can add custom domain name.

- AAD lives outside of subscriptions.
- subs trust the AAD instance.
- Domain Applications are told what AAD instance is trusted as the source of identity.

## Users:

Directory synced: Yes/No - Yes it came from on prem AD

Example: Different Azure AD tenant/gmail.msa > can add as guest users in AAD. Objects then can be given permissions for connected applications and services.

New user/invite user (guest user from gmail, another aad instance etc)

- wont replicate back to on prem.

Bulk creation:

- csv template for bulk users.
- also powershell can bulk create via script

## Groups:

Replicates from on prem to aad

Cloud groups:

- Dynamic groups, automatically added to groups based on some defined attributes
- Assigned/dynamic manual/automatic
- Cant manually add to dynamic group
- rule for dynamic group

Azure AD roles

- when creating group, yes indicates azure ad roles can be assigned

## Devices:

Register-known+manage

Join (register+) - login with aad users

## AAD SKus:

Different subscriptions. Capabilities

Free sku can replicate ad to AAD. 

Can only password writeback to AD with premium license

## Self service password reset

passwordreset > self service password reset, can define what groups have this options.

Methods used forpassword reset can be defined. Email, questions forexample.

## Administrative units

Roles in AAD - Global. Administrative units > add users/groups to it.

cant manage people in the group whengroup is added to admin unit. 

Administrative roles delegated through administrative unit. 

manage attributes of the group but no management of people in group. A way of delegating some administrative permissions. Forexample: helpdesk.

## Azure Subscriptions:

