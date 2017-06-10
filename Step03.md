## Create the Azure AD DC administrators group

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
