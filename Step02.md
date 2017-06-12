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


### [NEXT Step 3. Create the Azure AD DC administrators group.](Step03.md)
