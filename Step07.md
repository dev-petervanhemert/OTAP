


1. Log in to the Azure portal.
2. In the Favorites pane, of the portal, click New.
3. In the New blade, click Networking. In the Networking blade, click Virtual network, as shown in the following picture:
> <img src="/Images/07-vNetRM/011-Create_vNetRM.png" width="600"/> 

4. In the Virtual network blade, leave Resource Manager selected as the deployment model, and click Create.
5. In the Create virtual network blade that appears, enter the following values, then click Create:

**Setting** |	**Value** |	**Details**
  -------       -----       -------
  
**Name**	| MyVNet |	The name must be unique within the resource group.
**Address** | space	10.0.0.0/16 |	You can specify any address space you like in CIDR notation.
**Subnet name** |	Front-end |	The subnet name must be unique within the virtual network.
**Subnet address range** |	10.0.0.0/24 |	The range you specify must exist within the address space you defined for the virtual network.
**Subscription** |	[Your subscription] |	Select a subscription to create the VNet in. A VNet exists within a single subscription.
**Resource group** |	Create new: MyRG	Create a resource group. | The resource group name must be unique within the subscription you selected. To learn more about resource groups, read the Resource Manager overview article.
**Location** |	West US |	Typically the location that is closest to your physical location is selected.




