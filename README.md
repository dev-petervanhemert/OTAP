# OTAP-on-Azure-Guide

- Create or config Azure Active Directory.
    - Add goup AAD DC Administrators.
    - Create new Users.
        - tfsServices user
        - tfsBuild user
        - tfsReport user
        - tfsDeveloper users
    - Add new Users to Group. 
    - Change pssword new user.       
- Create Virtual Network (Classic).
- Create AAD Domain Services.
- Add DNS server from Domain Service to the classic Network.
- Create Virtual Network (Resource Management).
    - Add DNS server (ip from AAD Domain Services)
- Peer the vNets.

- Prerequisites for VM.
    - Create NSG.
    - Create Storage Account.
    - Create Availebility Set.
- Create VM for Team Foundation Services 2017.
    - Connect to domain AD
    - Install TFS 2017 on VM.
- Create VM for SonarQube.
    - Connect to domain AD
    - Install SonarQUbe.
- Create VM for Development.
        -Install Visual Studio 2017.


##Create an Azure Active Directory tenant.

1. Navigate to https://manage.windowsazure.com and log in with the account that has an Azure subscription.
2. Click ACTIVE DIRECTORY management icon in the left pane.
3. Click NEW button at the bottom of the page.
4. Choose APP SERVICES > ACTIVE DIRECTORY > DIRECTORY > CUSTOM CREATE.

      Create an Account.
> <img src="/Images/01-CreateAD/02-CreateAD.PNG" width="600"/> 

5. In the Add directory page, enter a name and domain name. For country or region choose United States or the country were Data Catalog is available.
