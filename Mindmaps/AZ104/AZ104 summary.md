# AZ-104 AZ ADMIN

## Links

- https://www.youtube.com/watch?v=qfd-t7jIF8g

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






 links
 **inline** ~~text~~ *styles*
 multiline
  text
 `inline code`

    ```js
    console.log('code block');
    ```
 Katex - $x = {-b \pm \sqrt{b^2-4ac} \over 2a}$