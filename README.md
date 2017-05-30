# OTAP in Azure

- Create or config Azure Active Directory.
    - Add goup AAD DC Administrators.
    - Create new User.
    - Add new User to Group.    
- Create AAD Domain Services.
- Create Virtual Network (Classic).
    - Add DNS server (ip from AAD Domain Services)
- Create Virtual Network (Resource Management).
    - Add DNS server (ip from AAD Domain Services)
- Peer the vNets.
- Create VM for Team Foundation Services 2017.
    - Connect to domain AD
    - Install TFS 2017 on VM.
- Create VM for SonarQube.
    - Connect to domain AD
    - Install SonarQUbe.
- Create VM for Development.
        -Install Visual Studio 2017.
