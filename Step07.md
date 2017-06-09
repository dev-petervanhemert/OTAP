


1. Log in to the Azure portal.
2. In the Favorites pane, of the portal, click New.
3. In the New blade, click Networking. In the Networking blade, click Virtual network, as shown in the following picture:
> <img src="/Images/07-vNetRM/011-Create_vNetRM.png" width="600"/> 

4. In the Virtual network blade, leave Resource Manager selected as the deployment model, and click Create.
5. In the Create virtual network blade that appears, enter the following values, then click Create:

Setting |	Value | Details
------- | ----- | -------  
**Name**	| VNet_Main_RM |	The name must be unique within the resource group.
**Address** | space	10.0.0.0/16 |	You can specify any address space you like in CIDR notation.
**Subnet name** |	subnet_TFS |	The subnet name must be unique within the virtual network.
**Subnet address range** |	10.0.0.0/24 |	The range you specify must exist within the address space you defined for the virtual network.
**Subscription** |	[Your subscription] |	Select a subscription to create the VNet in. A VNet exists within a single subscription.
**Resource group** |	Create new: "vNETsRM"	Create a resource group. | The resource group name must be unique within the subscription you selected. To learn more about resource groups, read the Resource Manager overview article.
**Location** |	West Europe |	Typically the location that is closest to your physical location is selected.

> <img src="/Images/07-vNetRM/02-Create_vNetRM.png" width="400"/> 

    The VNet takes a few seconds to create. Once it’s created, you see the Azure portal dashboard.

6. With the virtual network created, in the Azure portal Favorites pane, click All resources. Click the VNet_Main_RM virtual network in the All resources blade. If the subscription you selected already has several resources in it, you can enter VNet_Main_RM in the Filter by name… box to easily access the VNet.
7. The VNet_Main_RM blade opens and displays information about the VNet, as shown in the following picture:
> <img src="/Images/07-vNetRM/04-Create_vNetRM.png" width="400"/>
8. Select DNS servers and enter the DNS from the AAD Domain Services.

9. Click Subnets to display a list of the subnets within the VNet. The only subnet that exists is subnet_TFS, the subnet you created in step 5.
In the VNet_Main_RM - Subnets blade, click + Subnet to create a subnet with the following information and click OK to create the subnet:
Setting |	Value |	Details
------- | ----- | -------
Name |	subnet_SonarQube |	The name must be unique within the virtual network.
Address range |	10.0.1.0/24 |	The range you specify must exist within the address space you defined for the virtual network.
Network security group and Route table |	None (default) |	Network security groups (NSG)s are covered later.

If you will create a Developer machine you need to add a third subnet named "subnet_DEV" and address range 10.0.2.0/24

10. After the new subnet is added to the VNet, you can close the MyVNet – Subnets blade, then close the All resources blade.
