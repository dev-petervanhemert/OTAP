
## Create an Azure virtual network (Classic)

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
