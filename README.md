# OTAP-on-Azure-Guide

Step 1. Create or config Azure Active Directory.

Step 2. Create new Users.

    - tfsServices user
    - tfsBuild user
    - tfsReport user
    - tfsDeveloper users
    
Step 4. Add goup AAD DC Administrators.
    
Step 5. Change pssword new users. 

Step 6. Add Users to Group. 
          
Step 7. Create Virtual Network (Classic).

Step 8. Create AAD Domain Services.

Step 9. Add DNS server from Domain Service to the classic Network.

Step 10. Create Virtual Network (Resource Management).

Step 11. Add DNS server (ip from AAD Domain Services)

Step 12. Peer the vNets.

Step 13. Prerequisites for VM.

    - Create NSG.
    - Create Storage Account.
    - Create Availebility Set.
    
Step 14. Create VM for Team Foundation Services 2017.

    - Connect to domain AD
    - Install TFS 2017 on VM.
    
Step 15. Create VM for SonarQube.

    - Connect to domain AD
    - Install SonarQUbe.
    
Step 16. Create VM for Development.
        -Install Visual Studio 2017.


## Create an Azure Active Directory tenant.

1. Navigate to https://manage.windowsazure.com and log in with the account that has an Azure subscription.
2. Click ACTIVE DIRECTORY management icon in the left pane.
3. Click NEW button at the bottom of the page.
4. Choose APP SERVICES > ACTIVE DIRECTORY > DIRECTORY > CUSTOM CREATE.
> <img src="/Images/01-CreateAD/02-CreateAD.PNG" width="600"/> 
5. In the Add directory page, enter a name and domain name. For country or region choose United States or the country were Data Catalog is available.
> <img src="/Images/01-CreateAD/03-CreateAD.PNG" width="600"/> 
6. Choose OK icon. An Azure Active Directory is created.

## Add a user to your Azure Active Directory tenant

You need a user from your Azure AD to register an Azure AD app. Here's how to add a user to your Azure Active Directory tenant:
1. In your Azure Active Directory, click USERS.
> <img src="/Images/02-Add Users/01-AddUser.png" width="600"/> 
2. At the bottom of the page, click ADD USER. A user account is used to register a Data Catalog app.
3. In the Tell us about this user page:
    a. For TYPE OF USER, choose New user in you organization.
    b. Enter your USER NAME.
    c. Click Next.
> <img src="/Images/02-Add Users/02-AddUser.png" width="600"/> 
