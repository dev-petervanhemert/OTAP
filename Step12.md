
# Install SonarQube on VM-Sonar.

[Back to Main Menu](README.md)

    NOTE: 
    In this guide, we will demonstrate the installation and configurations using an 
    Azure VM server Datacenter 2016  and sql 2016 express. 
    
    

### **Index**

- [Step 1 - Install Java JRE](#step-1)

- [Step 2 - Configure SQL Server](#step-2)

- [Step 3 - Install SonarQube](#step-3)

- [Step 4 - Connect to SonarQube Server from outside the machine](#step-4)

---


> ### **STEP 1**

## Install Java JRE

**As mentioned in the Prerequisites section, a Java virtual machine (JVM) is required.
If the installed JVM meets the version requirements listed, you can skip this section. Otherwise, follow the steps below to install Java.**

- Download [Java SE Runtime Environment](http://www.oracle.com/technetwork/java/javase/downloads/jre8-downloads-2133155.html) and make sure you select the one corresponding to your current operation system.
	
 > <img src="/Images/12-sonar/sonar1.PNG" width="400"/> 
		
	NOTE: 
	SonarQube does not require the full Java JDK (Java SE Development Kit) 
	to run- you only need the JRE (Java SE Runtime Environment).

**Install Java JRE**
- Install **Java SE Runtime Environment** on the destination server.
 > <img src="/Images/12-sonar/sonar2.png" width="400"/> 	


---
>
> ### **STEP 2**

[UP to Index](#index) | [Back to Main Menu](README.md)

## Configure SQL Server 2016

		Before you get to the task of creating a new database for SonarQube, you need to complete a few preparations.

### Prepare Environment.

- **Launch **SQL Server Management Studio** (SSMS).**
	- Connect to the SQL Server instance on which you plan to create the database.
	
- Right click on the server instance and select **properties** => **Security**. 
> <img src="/Images/12-sonar/00-Sonar.png" width="400"/>  

- Select the **SQL Server and Windows Authentication**
> <img src="/Images/12-sonar/01-Sonar.png" width="400"/>   

 

 
- Create a user with SQL Server authentication, called **sonar** with a password.

- **Security** > right click on **Logins** > **New Login**.

 > <img src="/Images/12-sonar/sonar3.PNG" width="400"/> <img src="/Images/12-sonar/sonar4.PNG" width="400"/> 
- Open Sql Server Configuration Manager, and enable the TCP Procol.

 > <img src="/Images/12-sonar/sonar5.PNG" width="400"/> 
- Open Properties for TCP/IP protocol. 

- IPAll: Disable dynamic ports(delete 0 if any) and specify 1433 as TCP Port.

 > <img src="/Images/12-sonar/sonar6.PNG" width="400"/> 


### Create Sonar Database.

Back to **SQL Server Management Studio** (SSMS).

- Create a new database called Sonar with sonar user as owner
> <img src="/Images/12-sonar/sonar7.PNG" width="400"/> 

Now be sure to select the correct Collation. 

- SQL_Latin1_General_CP1_CS_AS.

		NOTA: Specify the right Collation for the database. It should be CS and AS.


 > <img src="/Images/12-sonar/sonar8.PNG" width="400"/> 

		Now, just to be sure that everything is ok, 
		try to connect from Management Studio using the port 1433 and with user sonar. 
		To specify port you should use a comma between server name and the port.


 > <img src="/Images/12-sonar/sonar9.PNG" width="400"/>  
 
 		Verify that you can see Sonar database. 
 		If you are able to connect and see Sonar Db you have everything ready. 














---
>
> ### **STEP 3**

[UP to Index](#index) | [Back to Main Menu](README.md)

## Install SonarQube

**Download and Install**

- Download **SonarQube 6.3.1** from the SonarQube [downloads](https://www.sonarqube.org/downloads/).
- Right-click on sonarqube-x.x.zip, select Properties and then select the Unblock box. 
 > <img src="/Images/12-sonar/sonar10.PNG" width="400"/> 


- Unzip SonarQube-x.x.zip on to a drive, for example use C:\SonarQube\
 > <img src="/Images/12-sonar/sonar11.PNG" width="400"/> 


- At this point, the installation is complete.


**Configure SonarQube**

- Basic configuration of SonarQube consists of making a few updates to the sonar.properties file.

- This file is located in the conf folder located under the SonarQube installation folder. 
	Example: C:\SonarQube\SonarQube-6.3.1\conf\sonar.properties
> <img src="/Images/12-sonar/sonar12.PNG" width="400"/>


> <img src="/Images/12-sonar/02-Sonar.png" width="400"/>    

- Run InstallNTServices.bat in C:\SonarQube\sonarqube-6.3.1\bin\windows-x86-64 

To start the Service:

- Run StartNTService.bat in C:\SonarQube\sonarqube-6.3.1\bin\windows-x86-64

or

- In run prompt type services.msc and search for SonarQube service and **start** the service.


> <img src="/Images/12-sonar/03-Sonar.png" width="600"/> 

		You can now browse SonarQube at http://localhost:9000 
		(the default System administrator credentials are admin/admin). 










---
>
> ### **STEP 4**

[UP to Index](#index) | [Back to Main Menu](README.md)

## Connect to SonarQube Server from outside the machine

###### Allow firewall inbound port 9000 to make http://<YOUR SONARQUBE>.westeurope.cloudapp.azure.com work.

Now open ports on the Server Windows firewall so we can access the SonarQube server and SQL from outside the machine. 
- Go to the command prompt and simply run the following commands to add the firewall rules.

```cmd
C:\xxxx\xxxx> netsh advfirewall firewall add rule name="SQL" dir=in action=allow protocol=TCP localport=1433

C:\xxxx\xxxx> netsh advfirewall firewall add rule name="Sonar" dir=in action=allow protocol=TCP localport=9000
```

The final step is to open ports to the virtual machine with the Azure portal.

If You followed Step 8, then you've done it already.

- Go to the **Network Security Group**(NSG-Sonar) in the Azure portal.
- Check if you have the Inbound security rule **Allow_SonarQube_In** on port **TCP/9000**

> <img src="/Images/08-SNG/03-CreateNSG.png" width="600"/> 

If the rule is missing, then go to [Step 8](Step08.md) section **Create rules in an existing NSGs**

Connect with the sonarQube server: http://xxxxxxxxxx.westeurope.cloudapp.azure.com:9000

[UP to Index](#index) | [Back to Main Menu](README.md)
