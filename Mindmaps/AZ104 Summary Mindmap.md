# AZ-104 AZ ADMIN

## Links
- https://www.youtube.com/watch?v=qfd-t7jIF8g
- https://www.examtopics.com/exams/microsoft/az-104/view/

## HTTPS - AAD

### Licensing/SKU
- Free = Partial functionality
- Per user per month
#### P1
- Full MFA
- Application group assignment
- Partial Conditional access
#### P2
- Entitlement management
- Full Identity Governance


### AAD Connect
- Replicate users/ groups from on prem AD
- AD source of truth
- Users appear as directory synced
- Password writeback with premium license

### Tenant/Domain
#### Devices
- Register = known+manage
- Join = Login AAD Users
#### Groups
- 'Dynamic Groups' for automating group addition
- Azure AD roles can be turned on for 'Assigned' groups
#### Users
- Bulk Creation via CSV
- Powershell bulk create script
##### Access
- MFA enf via Conditional Access/Grant control (allows untrustedlocal) 
##### Password reset
##### Guest Users
- Outside Accounts basic auth at e.g. gmail/alt AAD
- Inside AAD controls auth check requirements &  permissions
- Identity Issuer


#### Subscription
- AAD lives outside sub
- AAD is trusted for identities

### Protocols
#### Identiy
- Open ID connect (OIDC)
- SAML
- WS-FED
#### Authorisation
- OATH2
#### Applications
- Rest API

## Tenant
### Subscription
#### Resource Group
- Tags associate VMs/charges to departments (RG per department costly)
- Custom linux deployments with RCA - az vm create (cloudinit.txt)
- 









 links
 **inline** ~~text~~ *styles*
 multiline
  text
 `inline code`

    ```js
    console.log('code block');
    ```
 Katex - $x = {-b \pm \sqrt{b^2-4ac} \over 2a}$