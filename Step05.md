# Enable Azure Active Directory Domain Services

1. Go to the Azure classic portal.
2. In the left pane, select the Active Directory button.
3. Select the Azure Active Directory (Azure AD) tenant (directory) for which you want to enable Azure AD DS.
> <img src="/Images/05-AAD-Domain-Services/01-ADconfigDomainServices.png" width="600"/> 
4. On the preview directory page, click the Configure tab.
5. Under domain services, change the Enable domain services for this directory option to Yes.
Additional Azure Active Directory Domain Services configuration options appear on the page.
> <img src="/Images/05-AAD-Domain-Services/02-ADconfigDomainServices.png" width="600"/>

    Note

    When you enable Azure Active Directory Domain Services for your tenant, Azure AD generates and stores the Kerberos and NTLM credential hashes that are required for authenticating users.
    
6. Specify the DNS domain name of domain services.
  - The default domain name of the directory (with a .onmicrosoft.com suffix) is selected by default.
  - The list contains all domains that have been configured for your Azure AD directory, including both verified and unverified domains that you configure on the Domains tab.
  - You can also enter a custom domain name. In this example, the custom domain name is contoso100.com.
  
  
