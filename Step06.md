# Update DNS settings for the Azure virtual network

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

NEXT STEP: Create Resource Manager Virtual Network.
