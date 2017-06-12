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
