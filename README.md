# Zabbix-iis-template
upgrade the defualt zabbix iis template

In this template, I add the current request item for each app pool

I use system.run command to get data. you must enable the AllowKey=system.run[\*] in your zabbix agent configuration file and add this to iis Item prototypes in Application pools discovery : system.run["cd C:\Windows\System32\WindowsPowerShell\v1.0\ && powershell.exe (Get-WebRequest -AppPool '{#APPPOOL}').count"]

Also you can use this user parameter : UserParameter=AppPoolReq[\*],powershell.exe (Get-WebRequest -AppPool '$1').count and then you must add this to iis Item prototypes in Application pools discovery: AppPoolReq[{#APPPOOL}]

I put The template in there if you want to use it.
