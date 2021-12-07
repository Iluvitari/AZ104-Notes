https://www.youtube.com/watch?v=VOod_VNgdJk

### Things to do:

Microsoft learn

John Savills master class

### Identity and Azure AD

Ident provider for cloud services - AAD

{

- OIDC

- SAML

- WS-FED

  Authorisation:

- Oauth2

}

Function over HTTPS/work over internet

Application talking to AAD:

- Rest API
  - MSGRAPH

SaaS > use AAD as identify provider

 Azure > use AAD as identify provider

-

Regular AD: 

- Speaks kerberos
- NTLM
- LDAP

Doesnt work well for internet

### AAD Connect and customisation:

-- AAD connect/AAD connect cloud sync: AD source of truth but replicated to AAD.

Tenant:

AAD outside of subscriptions.

- sub trusts AAD instance. Domain

Applications are told what AAD instance is trusted as the source of identity.

### Users:

Directory synced: Yes/No - Yes it came from on prem AD

Example: Different Azure AD tenant/gmail.msa > can add as guest users in AAD. Objects then can be given permissions for connected applications and services.

New user/invite user (guest user from gmail, another aad instance etc)

- wont replicate back to on prem.

Bulk creation:

- csv template for bulk users.
- also powershell can bulk create via script

### Groups: