
# Prepare Azure for OTAP in the Cloud.

### [Back to Main Menu](README.md)

### **Index**

- [Step 1. Create or config Azure Active Directory.](#step-1)

- [Step 2. Add a user to your Azure Active Directory tenant.](#step-2)
    
- [Step 3. Create the Azure AD DC administrators group.](#step-3)
          
- [Step 4. Create an Azure virtual network (Classic).](#step-4)

- [Step 5. Create AAD Domain Services.](#step-5)

- [Step 6. Update the DNS settings for the classic Azure virtual network.](#step-6)

- [Step 7. Create Virtual Network (Resource Management) DNS and peering.](#step-7)

- [Step 8. Create network security groups using the Azure portal.](#step-8)

- [Step 9. Create Storage Account.](#step-9)

- [Step 10. Create VM Windows Server.](#step-10)


---
>
>
> ### **STEP 1**
[UP to Index](#index) | [Back to Main Menu](README.md)


## Create or config Azure Active Directory.

1. Navigate to https://manage.windowsazure.com and log in with the account that has an Azure subscription.
2. Click ACTIVE DIRECTORY management icon in the left pane.
3. Click NEW button at the bottom of the page.
4. Choose APP SERVICES > ACTIVE DIRECTORY > DIRECTORY > CUSTOM CREATE.
> <img src="/Images/01-CreateAD/02-CreateAD.PNG" width="600"/> 
5. In the Add directory page, enter a name and domain name. For country or region choose United States or the country were Data Catalog is available.
> <img src="/Images/01-CreateAD/03-CreateAD.PNG" width="400"/> 
6. Choose OK icon. An Azure Active Directory is created.

---
>
>
> ### **STEP 2**
[UP to Index](#index) | [Back to Main Menu](README.md)


## Add a user to your Azure Active Directory tenant.


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



---
>
>
> ### **STEP 3**
[UP to Index](#index) | [Back to Main Menu](README.md)


## Create the Azure AD DC administrators group.

1. Go to the Azure classic portal( https://manage.windowsazure.com/ ).
2. In the left pane, select the Active Directory button.
3. Select the Azure AD tenant (directory).
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




---
>
>
> ### **STEP 4**
[UP to Index](#index) | [Back to Main Menu](README.md)


## Create an Azure virtual network (Classic).

1. Go to the Azure classic portal.
2. In the left pane, select Networks.
3. In the task pane at the bottom of the window, click New.
> <img src="/Images/04-CreateVnet/01-CreateClassicNetwork.png" width="200"/> 
4. Click Network Services, and then select Virtual Network.
> <img src="/Images/04-CreateVnet/02-CreateClassicNetwork.png" width="600"/> 
5. To create a virtual network, click Quick Create.
6. Specify a Name for your virtual network, and consider doing the following:
    - You can choose to configure Address space or Maximum VM count for this network.
    - You can leave the DNS server setting as None for now. You can update the setting after you enable Azure Active Directory Domain           Services.
7. In the Location drop-down list, select a supported Azure region.
To ascertain the Azure regions in which Azure Active Directory Domain Services is available, see Azure services by region.
8. To create your virtual network, click Create a Virtual Network.
> <img src="/Images/04-CreateVnet/03-CreateClassicNetwork.png" width="600"/> 
9. After you've created a virtual network, select the name of the virtual network, and then click the Configure tab.
> <img src="/Images/04-CreateVnet/04-CreateClassicNetwork.png" width="600"/> 
10. Under virtual network address spaces, click add subnet, and then specify a subnet with the name AaddsSubnet.
> <img src="/Images/04-CreateVnet/05-CreateClassicNetwork.png" width="600"/> 
11. To create the subnet, click Save.






---
>
>
> ### **STEP 5**
[UP to Index](#index) | [Back to Main Menu](README.md)


## Create AAD Domain Services.

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
  
    Warning

    The prefix of your specified domain name (for example, contoso100 in the contoso100.com domain name) must contain 15 or fewer characters. You cannot create an Azure Active Directory Domain Services domain with a prefix containing more than 15 characters.
  
7. Ensure that the DNS domain name you have chosen for the managed domain does not already exist in the virtual network. Specifically, check to see whether:
    - You already have a domain with the same DNS domain name on the virtual network.
    - The virtual network you've selected has a VPN connection with your on-premises network, and you have a domain with the same DNS domain name on your on-premises network.
    - You have an existing cloud service with that name on the virtual network.
    
8. Select a virtual network on which you want Azure Active Directory Domain Services to be available. Select the virtual network and dedicated subnet you created in the Connect domain services to this virtual network drop-down list. Also consider the following:
    - Ensure that the virtual network that you have specified belongs to an Azure region that's supported by Azure Active Directory Domain Services.
    - Virtual networks that belong to a region where Azure Active Directory Domain Services is not supported do not show up in the drop-down list.
    - Use a dedicated subnet within the virtual network for Azure Active Directory Domain Services. Do not select the gateway subnet. 
    - Similarly, virtual networks that were created by using Azure Resource Manager do not appear in the drop-down list. Resource Manager-based virtual networks are not currently supported by Azure Active Directory Domain Services.

9. To enable Azure Active Directory Domain Services, in the task pane at the bottom of the page, click Save.
    - While Azure Active Directory Domain Services is being enabled for your directory, the page displays a status of Pending.
    
            Note

            Azure Active Directory Domain Services provides high availability for your managed domain. After you enable Azure Active Directory Domain Services, note that the IP addresses at which domain services are available on the virtual network are displayed one at a time. The second IP address is displayed shortly after the first, as soon the service enables high availability for your domain. When high availability is configured and active for your domain, you should see two IP addresses in the domain services section of the Configure tab.
            
- After about 20 to 30 minutes, the first IP address at which domain services are available on your virtual network in the IP address field on the Configure page.
> <img src="/Images/05-AAD-Domain-Services/03-ADconfigDomainServices.png" width="600"/>
- When high availability is operational for your domain, two IP addresses are displayed on the page. Your managed domain is available on your selected virtual network at these two IP addresses.
10. Note the two IP addresses so that you can update the DNS settings for your virtual network. Doing so enables virtual machines on the virtual network to connect to the domain for operations such as domain join.
> <img src="/Images/05-AAD-Domain-Services/04-ADconfigDomainServices.png" width="200"/>

        Note

    Depending on the size of your Azure AD tenant (for example, the number of users or groups), synchronization to your managed domain takes a while. This synchronization process happens in the background. For large tenants with tens of thousands of objects, it might take a day or two for all users, group memberships, and credentials to be synchronized.











---
>
>
> ### **STEP 6**
[UP to Index](#index) | [Back to Main Menu](README.md)


## Update the DNS settings for the classic Azure virtual network.


1. Go to the Azure classic portal.
2. In the left pane, select Networks.
     
      The Networks window opens.

3. On the Virtual Networks tab, select the virtual network in which you enabled Azure Active Directory Domain Services to view its properties.
4. Click the Configure tab.
5. In the DNS servers section, enter both of the IP addresses that were displayed in the Domain Services section on the Configure tab of your directory.
> <img src="/Images/06-Add DNS-server-to-vNet/01-Add DNS server ip to vNet.png" width="400"/>
6. To save the DNS server settings for this virtual network, in the task pane at the bottom of the window, click Save.
> <img src="/Images/06-Add DNS-server-to-vNet/02-Add DNS server ip to vNet.png" width="600"/>

        Note

        After you update the DNS server settings for the virtual network, it might take a while for the virtual machines on the network to get the updated DNS configuration. 
     If a virtual machine is unable to connect to the domain, you can flush the DNS cache ('ipconfig /flushdns') on the virtual machine. 
     This command forces a refresh of the DNS settings on the virtual machine.











---
>
>
> ### **STEP 7**
[UP to Index](#index) | [Back to Main Menu](README.md)


## Create Virtual Network (Resource Management) DNS and peering.

1. Log in to the Azure portal.
2. In the Favorites pane, of the portal, click New.
3. In the New blade, click Networking. In the Networking blade, click Virtual network, as shown in the following picture:
> <img src="/Images/07-vNetRM/011-Create_vNetRM.png" width="400"/> 

4. In the Virtual network blade, leave Resource Manager selected as the deployment model, and click Create.
5. In the Create virtual network blade that appears, enter the following values, then click Create:

Setting |	Value | Details
------- | ----- | -------  
**Name**	| VNet_Main_RM |	The name must be unique within the resource group.
**Address** | space	10.1.0.0/16 |	You can specify any address space you like in CIDR notation.
**Subnet name** |	subnet_TFS |	The subnet name must be unique within the virtual network.
**Subnet address range** |	10.1.0.0/24 |	The range you specify must exist within the address space you defined for the virtual network.
**Subscription** |	[Your subscription] |	Select a subscription to create the VNet in. A VNet exists within a single subscription.
**Resource group** |	Create new: "vNETsRM"	Create a resource group. | The resource group name must be unique within the subscription you selected. To learn more about resource groups, read the Resource Manager overview article.
**Location** |	West Europe |	Typically the location that is closest to your physical location is selected.

> <img src="/Images/07-vNetRM/02-Create_vNetRM.png" width="400"/> 

    The VNet takes a few seconds to create. Once it’s created, you see the Azure portal dashboard.

6. With the virtual network created, in the Azure portal Favorites pane, click All resources. Click the VNet_Main_RM virtual network in the All resources blade. If the subscription you selected already has several resources in it, you can enter VNet_Main_RM in the Filter by name… box to easily access the VNet.
7. The VNet_Main_RM blade opens and displays information about the VNet, as shown in the following picture:
> <img src="/Images/07-vNetRM/04-Create_vNetRM.png" width="600"/>
8. Update the DNS settings for the resource manager Azure virtual network.
Select DNS servers and enter the DNS from the AAD Domain Services.

9. Click Subnets to display a list of the subnets within the VNet. The only subnet that exists is subnet_TFS, the subnet you created in step 5.
In the VNet_Main_RM - Subnets blade, click + Subnet to create a subnet with the following information and click OK to create the subnet:

Setting | Value | Details
------- | ----- | -------
Name |	subnet_SonarQube |	The name must be unique within the virtual network.
Address range |	10.1.1.0/24 |	The range you specify must exist within the address space you defined for the virtual network.
Network security group and Route table |	None (default) |	Network security groups (NSG)s are covered later.

If you create a Developer machine you need to add a third subnet named "subnet_DEV" and address range 10.1.2.0/24

** Create a virtual network peering

1. Click VNet_Main_RM.
2. In the VNet_Main_RM blade that appears, click Peerings from the vertical list of options on the left side of the blade.
> <img src="/Images/07-vNetRM/01-peering.png" width="600"/>
3. In the VNet_Main_RM - Peerings blade that appeared, click + Add
4. In the Add peering blade that appears, enter, or select the following options, then click OK:
- **Name:** PeeringVnet_RM_with_CL
- **Virtual network deployment model:** Select Classic.
- **Subscription:** Select your subscription
- **Virtual network:** Click Choose a virtual network, then click vNet_Main_CL.
- **Allow virtual network access:** Enabled
> <img src="/Images/07-vNetRM/02-peering.png" width="600"/>

A few seconds after clicking OK to create the peering, the PeeringVnet_RM_with_CL peering you just created is listed with Connected in the PEERING STATUS column.
> <img src="/Images/07-vNetRM/04-peering.png" width="600"/>











---
>
>
> ### **STEP 8**
[UP to Index](#index) | [Back to Main Menu](README.md)


## Create network security groups using the Azure portal.

1. From a browser, navigate to http://portal.azure.com 
2. Click Browse > > Network Security Groups.
3. In the Network security groups blade, click Add.
> <img src="/Images/08-SNG/01-CreateNSG.png" width="600"/> 
4. In the Create network security group blade, create an NSG named NSG_TFS in the NSGs resource group, and then click Create.

      Repeate these steps to create NSG_SonarQube and NSG_Development.
      
### Create rules in an existing NSGs

1. Click Browse > > Network security groups.
2. In the list of NSGs, click NSG-TFS > Inbound security rules.
> <img src="/Images/08-SNG/02-CreateNSG.png" width="600"/> 
3. In the list of Inbound security rules, click Add.
4. In the Add inbound security rule blade, create a rule:
> <img src="/Images/08-SNG/04-CreateNSG.png" width="600"/> 
Name: Allow_RDP_In 
- Priority:  100 
- Source: Any
- Service: RDP
- Protocol: is set automaticly to TCP
- Port Range: is set automaticly to port 3389
- Action: Allow

5. Click OK.
6. Repeate for al the NSGs and rules like in the image.
> <img src="/Images/08-SNG/03-CreateNSG.png" width="600"/> 










---
>
>
> ### **STEP 9**
[UP to Index](#index) | [Back to Main Menu](README.md)


## Create Storage Account.

1. Sign in to the Azure portal.
2. On the Hub menu, select New -> Storage -> Storage account.
> <img src="/Images/09-StorageAccount/01-CreateStorageAccount.png" width="600"/> 

- Enter a name for your storage account.
- Specify the deployment model to be used: Resource Manager.
- Select the type of storage account: General purpose.
- Select the type of Performance: Standard.
- Select the replication option for the storage account: LRS.
- Storage service encryption: Disabled.
- Secure transfer required: Disabled.
- Select the subscription in which you want to create the new storage account.
- Specify a new resource group or select an existing resource group. 
- Select the geographic location for your storage account: West Europe.

Click Create.


---
>
>
> ### **STEP 10**
[UP to Index](#index) | [Back to Main Menu](README.md)


## Create VM Windows Server.

1. Sign in to the Azure portal.
2. Select Compute, select Windows Server 2016 Datacenter, and ensure that Resource Manager is the selected deployment model. Click the Create button.
3. Enter the virtual machine information. The user name and password entered here is used to log in to the virtual machine. When complete, click OK.
> <img src="/Images/10-VM.md/01-VM.PNG" width="600"/> 

4. Select a size for the VM. To see more sizes, select View all or change the Supported disk type filter. 
> <img src="/Images/10-VM.md/02-VM.PNG" width="600"/> 

5. On the settings blade: 
- Use managed disks: Yes
- Virtual Network: Select the before created vNet
- Subnet: Select the before created Subnet for your purpose
- Public IP addres: keep the default
- Network Security Group: Select the before created NSG for your purpose
- Extensions: No Extensions
- Availability set: keep the default
- Boot dianostics: Enabled
- Guest OS diagnostics: Enabled
- Diagnostics storage account: Select the before created storage account

click OK.
> <img src="/Images/10-VM.md/03-VM.PNG" width="400"/> 

6. On the summary page, click Ok to start the virtual machine deployment.

      The VM will be pinned to the Azure portal dashboard. Once the deployment has completed, the VM summary blade automatically opens.

### Connect to the virtual machine


1. Click the Connect button on the virtual machine properties. A Remote Desktop Protocol file (.rdp file) is created and downloaded.

> <img src="/Images/10-VM.md/04-VM.PNG" width="600"/> 

2. To connect to your VM, open the downloaded RDP file. If prompted, click Connect. On a Mac, you need an RDP client such as this Remote Desktop Client from the Mac App Store.

3. Enter the user name and password you specified when creating the virtual machine, then click Ok.

          You may receive a certificate warning during the sign-in process. 
          Click Yes or Continue to proceed with the connection.
 
          You should now be logged in and you should see the server manager dashboard. 
          The next step is to run Windows Update to patch this server.

4. Update the Server
- Click the Windows button in the bottom left of the screen to navigate to the Start screen.

> <img src="/Images/10-VM.md/05-VM.png" width="600"/> 

- In the search box, type Check for updates and Click Check for updates in the search results.
> <img src="/Images/10-VM.md/06-VM.png" width="600"/> 
- Ones updated, Click the **Advanced options** link
> <img src="/Images/10-VM.md/07-VM.png" width="400"/> 
- Check Give me updates for other Microsoft products when I update Windows and **Check for updates** again.
> <img src="/Images/10-VM.md/08-VM.png" width="400"/> 

5. (Optional) Turn off IE Enhanced Security Configuration.
> <img src="/Images/10-VM.md/09-VM.png" width="400"/> 
> <img src="/Images/10-VM.md/10-VM.png" width="600"/> 
- Click the link that says On.
> <img src="/Images/10-VM.md/11-VM.png" width="400"/> 
- Under Administrators, select the Off radio button 
- (Optional) Under Users, select the Off radio button 
- Click the OK button and refresh.

            IE Enhanced Security Configuration should now be set to Off.

6. Join this Server to the Active Directory Domain.
> <img src="/Images/10-VM.md/12-VM.png" width="400"/> 
- Click on the computer name link
> <img src="/Images/10-VM.md/13-VM.png" width="400"/> 
- Click the Change... button

> <img src="/Images/10-VM.md/14-VM.png" width="400"/> 

- In the Computer name textbox, enter the desired name for this server 
- Under Member of choose the Domain radio button
- In the Domain textbox, enter the name of the Active Directory domain 
- Click the OK button
> <img src="/Images/10-VM.md/15-VM.png" width="400"/> 
- Enter the username and password
- Click OK
> <img src="/Images/10-VM.md/16-VM.png" width="300"/> 

            You’ll be notified that you’ll need to reboot this server.

[UP to Index](#index) | [Back to Main Menu](README.md)

