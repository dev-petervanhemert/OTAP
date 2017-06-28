
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


### [NEXT Step 10. Create VM Windows Server.](Step10) 


