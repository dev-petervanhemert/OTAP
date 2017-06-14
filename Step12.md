###### **Top**

    Deployment Type:
    
    - TFS Services and SQL Server are hosted on a single computer and SonarQube (all components) on a separate machine.
    - Suitable for evaluation in production or near-production environments.

# Install SonarQube on VM-Sonar.

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

[Go to Top](#top)

## Configure SQL Server 2016

		Before you get to the task of creating a new database for SonarQube, you need to complete a few preparations.

1. **Launch SSMS**
	- Launch **SQL Server Management Studio** (SSMS).
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

- Disable dynamic ports(delete 0 if any) and specify 1433 as TCP Port.

 > <img src="/Images/12-sonar/sonar6.PNG" width="400"/> 
 
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

[Go to Top](#top)

## Install SonarQube



---
>
> ### **STEP 4**

[Go to Top](#top)

## Connect to SonarQube Server from outside the machine


