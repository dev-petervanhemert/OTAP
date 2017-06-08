# OTAP-on-Azure-Guide

Step 1. Create or config Azure Active Directory.

Step 2. Create new Users.
    
Step 4. Create the Azure AD DC administrators group.
    
Step 5. Change pssword new users. 

Step 6. Add Users to Group. 
          
Step 7. Create an Azure virtual network (Classic).

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
> <img src="/Images/01-CreateAD/03-CreateAD.PNG" width="400"/> 
6. Choose OK icon. An Azure Active Directory is created.

## Add a user to your Azure Active Directory tenant

        NB. You need for TFS 2017 multiply users.
        Name these users:
        tfsServices, tfsBuild, tfsReport

You need a user from your Azure AD to register an Azure AD app. Here's how to add a user to your Azure Active Directory tenant:
1. In your Azure Active Directory, click USERS.
> <img src="/Images/02-Add Users/01-AddUser.png" width="400"/> 
2. At the bottom of the page, click ADD USER. A user account is used to register a Data Catalog app.
3. In the Tell us about this user page:

    a. For TYPE OF USER, choose New user in you organization.
    
    b. Enter your USER NAME.
    
    c. Click Next.
    
> <img src="/Images/02-Add Users/02-AddUser.png" width="400"/> 
4. In the user profile page, enter your DISPLAY NAME. Display name is a required field.
> <img src="/Images/02-Add Users/04-AddUser.png" width="400"/> 
5. Click Next. For ROLE, you can use User.
6. Click Create to create a temporary password. The new user is assigned a temporary password that must be changed on first sign in.
> <img src="/Images/02-Add Users/05-AddUser.png" width="400"/> 
7. In the Get temporary password page, copy the temporary password, and click Complete icon. You use the temporary password when you first login to your AAD.
> <img src="/Images/02-Add Users/06-AddUser.png" width="400"/> 
After you click the Complete icon, a new Azure AD user is created.

Change temporary password.
1. Login into the azure portal with the temporary password
> <img src="/Images/02-Add Users/01-ChangePassword.png" width="400"/> 
2. Change the password
> <img src="/Images/02-Add Users/02-ChangePassword.png" width="400"/>

To complete the next step the new AAD user will need access to an Azure Subscription. You can either make the new user a co-admin on the existing subscription or you can create a new subscription for the new AAD user.

## Create the Azure AD DC administrators group

1. Go to the Azure classic portal( https://manage.windowsazure.com/ ).
2. In the left pane, select the Active Directory button.
3. Select the Azure AD tenant (directory) for which you want to enable Azure Active Directory Domain Services. You can create only one domain for each Azure AD directory.
> <img src="/Images/03-CreateGroup/00-CreateGroup.png" width="400"/> 
4. On the preview directory page, click the Groups tab.
> <img src="/Images/03-CreateGroup/01-CreateGroup.png" width="400"/> 
5. To add a group to your Azure AD tenant, on the task pane at the bottom of the window, click Add Group.
> <img src="/Images/03-CreateGroup/04-CreateGroup.png" width="400"/> 
6. In the Add Group dialog box, create a group named AAD DC Administrators, and then set Group Type to Security.
> <img src="/Images/03-CreateGroup/02-CreateGroup.png" width="400"/> 

        Warning

        To enable access within your Azure Active Directory Domain Services-managed domain, 
        create a group with this exact name.

7. In the Description box, enter a description that enables others to understand that this group grants administrative permissions within Azure Active Directory Domain Services.
8. After you've created the group, click the group name to view its properties.
9. To add users as members of the group, at the bottom of the window, click the Add Members button.
> <img src="/Images/03-CreateGroup/03-AddGroupMember.png" width="600"/> 
10. In the Add members dialog box, select the users who should be members of this group, and then click the checkmark icon at the lower right.
> <img src="/Images/03-CreateGroup/02-AddGroupMember.png" width="600"/> 

## Create an Azure virtual network
> <img src="/Images/04-CreateVnet/01-CreateClassicNetwork.png" width="600"/> 
