# Install Team Foundation Server 2017 on Azure

- Step 1 - Install Pre-requisites for SQL Server 2016 and Team Foundation Server 2017
- Step 2 - Install SQL Server 2016
- Step 3 - Install Team Foundation Server 2017
- Step 4 - Create a TFS Build / Release Server on Windows

---
>
>
> ### **STEP 1**

## Install Pre-requisites for SQL Server 2016 and Team Foundation Server 2017

Before you can install SQL Server or Team Foundation Server, you’ll need to enable their pre- requisite roles and features in Windows Server.
- Log on to the server using an account that is a member of the Administrators group
- Run Server Manager

        First we need to verify that the .NET Framework 3.5 features are installed on this server.

> <img src="/Images/11-TFS/01-TFS.png" width="300"/> 
- In Server Manager, click **Add roles and features**
- On the **Before you begin** page of the wizard, click **Next**
- On the **Select installation type** page, choose **Role-based or feature-based installation** and click **Next**
- On the **Select destination server** page
  - Choose **Select a server from the server pool**
  - Select the name of the current server
  - Click **Next**
> <img src="/Images/11-TFS/02-TFS.png" width="400"/> 
- Check **Web Server (IIS)**
- Click **Add Features** and **Next**
> <img src="/Images/11-TFS/03-TFS.png" width="400"/> 
- Expand the **.NET Framework 4.6 Features** node
- Check **ASP.NET 4.6**
- Click **Next** until you see:
> <img src="/Images/11-TFS/05-TFS.png" width="200"/>
- Click **Yes**
> <img src="/Images/11-TFS/04-TFS.png" width="400"/> 
- Check **Restart the destination server automatically if required**
- Click **Install**

                Eventually, the feature installation should finish.

> <img src="/Images/11-TFS/06-TFS.png" width="400"/> 
- Verify that the installation succeeded 
- Click Close
- (Optional) Reboot the server
>
>
---
>
> ### **STEP 2**

## Install SQL Server 2016

- Run the SQL Server setup program
- Click **Yes** on any User Account Control dialogs that appear
- In the left panel, click **Installation**
- In the right panel, click **New SQL Server stand-alone installation or add features to an existing installation**
- Enter a product key 
- Click **Next**
- Check **I accept the license terms** 
- Click **Next**
- Check **Include SQL Server product updates** 
- Click **Next**

                Verify that none of the install rule checks have failed.
                
> <img src="/Images/11-TFS/07-TFS.png" width="400"/> 
- Verify that there are 0 failures 
- Click **Next**
> <img src="/Images/11-TFS/08-TFS.png" width="600"/> 

- Under Instance Features check.

- [x] Database Engine Services
- [x] Full-text and Semantic Extractions for Search
- [x] Analysis Services
- [x] Reporting Services–Native
        
- Click **Next**

> <img src="/Images/11-TFS/09-TFS.png" width="400"/> 
- Choose **Default instance** 
- Click **Next**

> <img src="/Images/11-TFS/10-TFS.png" width="600"/> 
- For each service, set **Startup Type** to **Automatic**
- Click **Next**

> <img src="/Images/11-TFS/11-TFS.png" width="600"/> 
- Choose **Windows authentication mode**
- Click the **Add Current User** button to add the current user as a SQL Server administrator
- (Optional) Click the **Add**... button and add the **Domain Admins** group to the SQL Server
administrators
- Click **Next**

> <img src="/Images/11-TFS/12-TFS.png" width="600"/> 
- Click the **Add Current User** button to add the current user as an Analysis Server administrator
- (Optional) Click the **Add...** button and add the **Domain Admins** group to the Analysis Services administrators
- Click **Next**

- Choose **Install and configure** 
- Click **Next**
- Click Install

The installer should now be running.
> <img src="/Images/11-TFS/13-TFS.png" width="600"/> 
Eventually, the installer should finish.
> <img src="/Images/11-TFS/14-TFS.png" width="600"/> 
- Verify that all items installed successfully 
- Click **Close** to exit the installer
You should now be back on the SQL Server Installation Center.
- (Optional) Install **SQL Server Management** Tools
- Or click the close button to exit the installer

                SQL Server 2016 is now installed.
                (Recommended) Re-run Windows Update and install any available updates

---
>
> ### **STEP 3**

## Install Team Foundation Server 2017

NB.  Be Sure you did created the following users in the Active Directory: 
- TFS Service (domain\tfsservice)
- TFS Reports (domain\tfsreports)
- TFS Build (domain\tfsbuild)

- If you’re installing this on a Hyper-V virtual machine with dynamic memory enabled, change the minimum amount of RAM to 2GB (at least temporarily) to allow Team Foundation Server 2017 to install along with SQL Server.
- Gather the username and passwords for the 3 TFS service accounts (see above)
- Log on to the server using a user account with Administrator privileges

Download TFS 22017:
https://www.visualstudio.com/downloads/

- Run Tfs2017.exe and Install

You should now see the Team Foundation Server Configuration Center.

> <img src="/Images/11-TFS/15-TFS.png" width="400"/> 

- Choose **Configure Team Foundation Server** 
- Click **Start Wizard**

> <img src="/Images/11-TFS/16-TFS.png" width="400"/> 
- Click **Next**

> <img src="/Images/11-TFS/17-TFS.png" width="400"/> 
- Select **This is a new Team Foundation Server deployment**
- Click **Next**

> <img src="/Images/11-TFS/18-TFS.png" width="400"/> 
- Choose **New Deployment – Advanced**
- Click **Next**

> <img src="/Images/11-TFS/19-TFS.png" width="400"/> 
- Click the **Test** link to verify the connection to SQL Server
- Confirm that the test passes
- Click **Next**

> <img src="/Images/11-TFS/20-TFS.png" width="400"/> 
- Choose **Use a user account**
- In the **Account Name** textbox, type the fully-qualified name of the service account.
                Example: demo\tfsservice
- In the **Password** textbox, enter the password for the service account
- Click the **Test** link to verify the credentials are correct
- Click **Next**

You should now see a page prompting you for the configuration of TFS in IIS. 
You may see a warning about using SSL encryption. It’s a good idea but it’s not required.

> <img src="/Images/11-TFS/21-TFS.png" width="400"/> 

(Optional) At the bottom of this page, there’s a section for File Cache Location. TFS caches files for efficiency. The contents of this directory can become impressively large. For performance reasons and for disk space management reasons, you probably should put this on a separate disk – ideally on a different “spindle” – than your system/operating system drive.

> <img src="/Images/11-TFS/22-TFS.png" width="400"/> 
- (Optional) Change the **Folder** path to reference the desired location and disk. 
- Click **Next**

TFS2017 adds a bunch of new features to help you search the contents of your team projects. 
This is an optional feature.

**Option 1:** If you do not want to install Search: 
- Uncheck **Install and configure Search**
- Click **Next**

**Option 2:** Install Search
• Check **Install and configure Search**

> <img src="/Images/11-TFS/23-TFS.png" width="400"/>

- Choose **Install Search Service**
- Set the **Location of the search index** to the drive and folder you want to use for search.
For performance reasons, you’ll probably want to keep this on a different drive than the system drive. If your TFS installation is large and busy, you may want to put this on its own drive by itself. In the screenshot, I’m putting this on the same drive as my TFS File Cache at E:\TfsData\Search\IndexStore.
- Under Service Account choose **Use a user account**
- Set **Account Name** to the service account want to use to run search. In this
configuration, I’m using the same account at the TFS Service, demo\tfsservice
- Set the **Password** for the service account
- Click the **Test** link to verify the service credentials
- Click **Next**

The **Configure Reporting for Team Foundation Server** page is another optional feature but this guide assumes that you’re installing support for SQL Server Reporting Services with TFS2017.

> <img src="/Images/11-TFS/24-TFS.png" width="400"/>
 - Check **Configure Reporting for use with Team Foundation Server **
 - Click **Next**

Values should be automatically populated.
> <img src="/Images/11-TFS/25-TFS.png" width="400"/>
- Click **Next**

> <img src="/Images/11-TFS/26-TFS.png" width="400"/>
- Click the Test link to verify the connection to SQL Server Analysis Services 
- Click Next

> <img src="/Images/11-TFS/27-TFS.png" width="400"/>
- Check **Use a different account than the Team Foundation Server service account...**
- Set **Account Name** to the fully qualified username of the service account
- Set the **Password** for the service account
- Click the **Test** link to verify the credentials
- Click **Next**

- Uncheck **Enable integration with SharePoint** 
- Click **Next**

The installer will now prompt you to create a new Team Project Collection (TPC). 
The answer to this one (unless you’re doing a migration) is yes.
- Check **Create a new team project collection** 
- Click **Next**
You should now be on the Confirm the Configuration Settings Before Proceeding page.
- Click **Next**

> <img src="/Images/11-TFS/28-TFS.png" width="400"/>

- Check **I accept the Oracle Binary Code License Agreement for Java SE... **
- Click the **Configure** button
The configuration process should now be running and end with a message saying Success..

> <img src="/Images/11-TFS/29-TFS.png" width="400"/>
- Click **Next**

                Team Foundation Server 2017 is now configured and running.


> <img src="/Images/11-TFS/30-TFS.png" width="400"/>
- Click **Close**



---
>
> ### **STEP 4**

## Create a TFS Build / Release Server on Windows


