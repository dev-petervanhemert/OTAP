# Create network security groups using the Azure portal

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
> <img src="/Images/08-SNG/03-CreateNSG.png" width="600"/> 
Name: Allow_RDP_In 
- Priority:  100 
- Source: Any
- Service: RDP
- Protocol: is set automaticly to TCP
- Port Range: is set automaticly to port 3389
- Action: Allow

5. Click OK.
6. Repeate for al the rules in the image.
> <img src="/Images/08-SNG/04-CreateNSG.png" width="600"/> 

