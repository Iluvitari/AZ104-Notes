Sign in to the Azure portal as a global administrator, security administrator, or Conditional Access administrator.

Browse to Azure Active Directory > Security > Conditional Access.
Select New policy.

Give your policy a name. We recommend that organizations create a meaningful standard for the names of their policies.

Under Assignments, select Users and groups

Under Include, select All users

Under Exclude, select Users and groups and choose your organization's emergency access or break-glass accounts.

Select Done.

Under Cloud apps or actions > Include, select All cloud apps.

Under Exclude, select any applications that don't require multi-factor authentication.

Under Access controls > Grant, select Grant access, Require multi-factor authentication, and select Select.

Confirm your settings and set Enable policy to Report-only.
Select Create to create to enable your policy.