# Create virtual machine

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
> <img src="/Images/10-VM.md/03-VM.PNG" width="600"/> 

6. On the summary page, click Ok to start the virtual machine deployment.

      The VM will be pinned to the Azure portal dashboard. Once the deployment has completed, the VM summary blade automatically opens.

### Connect to the virtual machine


1. Click the Connect button on the virtual machine properties. A Remote Desktop Protocol file (.rdp file) is created and downloaded.

> <img src="/Images/10-VM.md/04-VM.PNG" width="600"/> 

2. To connect to your VM, open the downloaded RDP file. If prompted, click Connect. On a Mac, you need an RDP client such as this Remote Desktop Client from the Mac App Store.

3. Enter the user name and password you specified when creating the virtual machine, then click Ok.

          You may receive a certificate warning during the sign-in process. Click Yes or Continue to proceed with the connection.
          
4. Run Windows Update to patch this server.

You should now be at the Start menu.  
•
In the search box, type 
Check for updates
•
Click 
Check for updates
 in the search results

[NEXT Step 11 Install TFS 2017 ](../../../TFS-2017-Installation-Guide/blob/master/TFS2017-install-guide.pdf)


  
