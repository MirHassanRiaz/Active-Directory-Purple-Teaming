# Active-Directory-Purple-Teaming
This repository is aimed at sharing the cliff notes for performing Red Teaming of Active Directory System combined with  Detection Engineering part of  AD Attacks

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

* Get Domain SID for current domain
C:\AD\Pentesting\ADModule-master> Get-DomainSID
C:\AD\Pentesting\ADModule-master> (Get-ADDomain).DomainSID

* Get Domain Policy for the current domain
C:\AD\PowerView> Get-DomainPolicy

* Get domain policy for another domain
*Domain Password Policy

C:\AD\PowerView> (Get-DomainPolicy)."system access"

*Domain Kerberos Policy 
C:\AD\PowerView> (Get-DomainPolicy)."Kerberos Policy"



Additional Resources: 

https://github.com/PowerShellMafia/PowerSploit/blob/master/Recon/PowerView.ps1

https://docs.microsoft.com/en-us/powershell/module/activedirectory/?view=windowsserver2022-ps
