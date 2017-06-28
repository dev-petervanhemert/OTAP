
# Prepare Azure for OTAP in the Cloud.

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
[UP to Index](#index)


## Create or config Azure Active Directory.



---
>
>
> ### **STEP 2**
[UP to Index](#index)


## Add a user to your Azure Active Directory tenant.





---
>
>
> ### **STEP 3**
[UP to Index](#index)


## Create the Azure AD DC administrators group.






---
>
>
> ### **STEP 4**
[UP to Index](#index)


## Create an Azure virtual network (Classic).








---
>
>
> ### **STEP 5**
[UP to Index](#index)


## Create AAD Domain Services.










---
>
>
> ### **STEP 6**
[UP to Index](#index)


## Update the DNS settings for the classic Azure virtual network.












---
>
>
> ### **STEP 7**
[UP to Index](#index)


## Create Virtual Network (Resource Management) DNS and peering.











---
>
>
> ### **STEP 8**
[UP to Index](#index)


## Create network security groups using the Azure portal.












---
>
>
> ### **STEP 9**
[UP to Index](#index)


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
[UP to Index](#index)


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



