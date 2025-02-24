{{ $product_link := "[Docker Hub](https://hub.docker.com)" }}
{{ $sso_navigation := `Navigate to the SSO settings page for your organization or company.
   - Organization: Select **Organizations**, your organization, **Settings**, and then **Security**.
   - Company: Select **Organizations**, your company, and then **Settings**.` }}
{{ $member_navigation := "Select **Organizations**, your organization, and then **Members**." }}
{{ $invite_button := "**Invite members**" }}
{{ $remove_button := "**Remove member**" }}
{{ $provisioning_steps := "This feature is only available in the Admin Console."}}

{{ if eq (.Get "product") "admin" }}
  {{ $product_link = "the [Admin Console](https://admin.docker.com)" }}
  {{ $invite_button = "**Invite**" }}
  {{ $sso_navigation = "Select your organization or company in the left navigation drop-down menu, and then select **SSO and SCIM**." }}
  {{ $member_navigation = `Navigate to the user management page for your organization or company. 
    - Organization: Select your organization in the left navigation drop-down menu, and then select **Members**.
    - Company: Select your company in the left navigation drop-down menu, and then select **Users**.` }}
  {{ $remove_button = "**Remove member**, if you're an organization, or **Remove user**, if you're a company" }}

> [!IMPORTANT]
>
> SSO has Just-In-Time (JIT) Provisioning enabled by default unless you have [disabled it](/security/for-admins/provisioning/just-in-time/#sso-authentication-with-jit-provisioning-disabled). This means your users are auto-provisioned to your organization.
>
> You can change this on a per-app basis. To prevent auto-provisioning users, you can create a security group in your IdP and configure the SSO app to authenticate and authorize only those users that are in the security group. Follow the instructions provided by your IdP:
>
> - [Okta](https://help.okta.com/en-us/Content/Topics/Security/policies/configure-app-signon-policies.htm)
> - [Entra ID (formerly Azure AD)](https://learn.microsoft.com/en-us/azure/active-directory/develop/howto-restrict-your-app-to-a-set-of-users)
>
> Alternatively, see [Manage how users are provisioned](/manuals/security/for-admins/single-sign-on/manage.md).


### Add guest users when SSO is enabled

To add a guest that isn't verified through your IdP:

1. Sign in to {{ $product_link }}.
2. {{ $member_navigation }}
3. Select {{ $invite_button }}.
4. Follow the on-screen instructions to invite the user.

### Remove users from the SSO company

To remove a user:

1. Sign in to {{ $product_link }}.
2. {{ $member_navigation }}
3. Select the action icon next to a user’s name, and then select {{ $remove_button }}.
4. Follow the on-screen instructions to remove the user.
{{ end }}