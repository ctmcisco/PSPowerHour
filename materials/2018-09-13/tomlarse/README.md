* **Name**: Tom-Inge Larsen
* **Title**: Relearning the troubleshooting basics in Powershell
* **Abstract**: ping, nslookup, arp and traceroute all have PS equivalents. Time to start using them!
* **Twitter**: @ti83
* **SlackID**: @Tom-Inge
* **Blog**: https://blog.codesalot.com

# PS Equivalent troubleshooting commands

What | Traditional | Powershell | alias | module | comments
-----|-------------|------------|-------|--------|----------
Find IP addresses|`ipconfig`|`Get-NetIpConfiguration`|`gip`| NetTCPIP|
Find DNS servers|`ipconfig /all`|`Get-NetIPConfiguration`|`gip`| NetTCPIP|
DNS lookups|`nslookup`|`Resolve-DnsName`||DnsClient |
Clear local DNS cache|`ipconfig /flushdns`|`Clear-DnsClientCache`||DnsClient|
Check network connectivity|`ping`|`Test-NetConnection`|`tnc`|NetTCPIP|Test-Connection from PS core 6.1
Check TCP port connectivity|`telnet`|`Test-NetConnection`|`tnc`|NetTCPIP|Test-Connection from PS core 6.1
Find network route|`tracert`|`Test-NetConnection -traceroute`|`tnc`|NetTCPIP|Test-Connection from PS core 6.1
Find current listening and established network connections|`netstat -ano`|`Get-NetTcpConnection`||NetTCPIP|Will not list UDP connections as netstat does
Find active layer 2 neighbors|`arp -a`|`Get-NetNeighbor`||NetTCPIP|

These cmdlets are from modules currently only available in Windows PowerShell. With the exception of Test-NetConnection they are not yet ported to Powershell Core. Test-NetConnection has been ported as Test-Connection and will be available from PowerShell Core 6.1. There is an active issue on the subject in the PowerShell repo:

https://github.com/PowerShell/PowerShell/issues/6076
