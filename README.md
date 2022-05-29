# Active-Directory-Purple-Teaming
This repository is aimed at sharing the cliff notes for performing Red Teaming of Active Directory System combined with  Detection Engineering part of  AD Attacks

# Assumed Breach Methodology
![image](https://user-images.githubusercontent.com/53171887/170877039-2d596dca-ebc5-4f35-a3b8-f59ce3cffdef.png)

# Insider Attack Simlation Model
![image](https://user-images.githubusercontent.com/53171887/170877115-d198699a-7788-4cc4-a68e-b7a6435a6a65.png)


# AD Red Teaming Ops

# Domain Enumeration Commands 

C:\Users\Windows-Machine> whoamii /priv
C:\Users\Windows-Machine> $ADClass = [System.DirectorServices.ActiveDirectory.Domain]
C:\Users\Windows-Machine> $ADClass::GetCurrentDomain()

C:\Users\Windows-Machine> cd C:\AD\PowerView
C:\AD\PowerView> ..\Powerview.ps1
C:\AD\PowerView> Get-NetDomain

C:\Users\Windows-Machine> cd C:\AD\Pentesting\ADModule-master\
C:\AD\Pentesting\ADModule-master> .\Microsoft.ActiveDirectory.Management.dll
C:\AD\Pentesting\ADModule-master> .\ActiveDirectory\ActiveDirectory.psd1
C:\AD\Pentesting\ADModule-master> Get-ADDomain
C:\AD\Pentesting\ADModule-master> Get-NetDomain -Domain moneycorp.local
C:\AD\Pentesting\ADModule-master> Get-ADDomain -Identity corp.local

Get Domain SID for current domain
C:\AD\Pentesting\ADModule-master> Get-DomainSID
C:\AD\Pentesting\ADModule-master> (Get-ADDomain).DomainSID

Get Domain Policy for the current domain
C:\AD\PowerView> Get-DomainPolicy

Get domain policy for another domain
*Domain Password Policy

C:\AD\PowerView> (Get-DomainPolicy)."system access"

Domain Kerberos Policy 
C:\AD\PowerView> (Get-DomainPolicy)."Kerberos Policy"

C:\AD\Pentesting\ADModule-master> Get-NetDomainController
C:\AD\Pentesting\ADModule-master> Get-ADDomainController
C:\AD\Pentesting\ADModule-master> Get-ADDomainController -Domain corp2.local

Get List of Users in Current Domain

C:\AD\Pentesting\ADModule-master> Get-NetUser
C:\AD\Pentesting\ADModule-master> Get-NetUser -Username student1
C:\AD\Pentesting\ADModule-master> Get-ADUser -Filter * -Properties *
C:\AD\Pentesting\ADModule-master> Get-ADUser -Identity student1 -Properties*
C:\AD\Pentesting\ADModule-master> Get-NetUser | select cn
C:\AD\Pentesting\ADModule-master> Get-NetUser | select Name

Get list of all properties for users in the current domain

C:\AD\Pentesting\ADModule-master> Get-UserProperty
C:\AD\Pentesting\ADModule-master> Get-UserProperty -Properties pwdlastset
C:\AD\Pentesting\ADModule-master> Get-ADUser -Filter * -Properties * | select -First 1 | Get-Member - MemberType *Property | select Name
C:\AD\Pentesting\ADModule-master> Get-ADUser -Filter * -Properties * | select name,@{expression={[dateime]::fromFileTime($_.pwdlastset)]}

Additional Resources: 

https://github.com/PowerShellMafia/PowerSploit/blob/master/Recon/PowerView.ps1

https://docs.microsoft.com/en-us/powershell/module/activedirectory/?view=windowsserver2022-ps
