# Install Team Foundation Server 2017 on Azure

### Install Pre-requisites for SQL Server 2016 and Team Foundation Server 2017

Before you can install SQL Server or Team Foundation Server, you’ll need to enable their pre- requisite roles and features in Windows Server.
- Log on to the server using an account that is a member of the Administrators group
- Run Server Manager

        First we need to verify that the .NET Framework 3.5 features are installed on this server.

> <img src="/Images/11-TFS.md/01-TFS.png" width="200"/> 
- In Server Manager, click **Add roles and features**
- On the **Before you begin** page of the wizard, click **Next**
- On the **Select installation type** page, choose **Role-based or feature-based installation** and click **Next**
- On the **Select destination server** page
  - Choose **Select a server from the server pool**
  - Select the name of the current server
  - Click **Next**
> <img src="/Images/11-TFS.md/02-TFS.png" width="400"/> 
- Check **Web Server (IIS)**
- Click **Add Features** and **Next**
> <img src="/Images/11-TFS.md/03-TFS.png" width="400"/> 
- Expand the **.NET Framework 4.6 Features** node
- Check **ASP.NET 4.6**
- Click **Next** until you see:
> <img src="/Images/11-TFS.md/05-TFS.png" width="200"/>
- Click **Yes**
> <img src="/Images/11-TFS.md/04-TFS.png" width="400"/> 
- Check **Restart the destination server automatically if required**
- Click **Install**

                Eventually, the feature installation should finish.

> <img src="/Images/11-TFS.md/06-TFS.png" width="400"/> 
- Verify that the installation succeeded 
- Click Close
- (Optional) Reboot the server

### Install SQL Server 2016

