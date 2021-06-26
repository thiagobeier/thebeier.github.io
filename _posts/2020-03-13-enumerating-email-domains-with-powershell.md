---
layout: post
title: Enumerating email domains with PowerShell
date: 2020-03-13 20:00
author: beierca
comments: true
categories: [Administration, Exchange Online, export to csv, import from csv, Management, Office365, Powershell]
---
Hi there

After working on a project where we had 30 domains to be migrated over between two different Office 365 tenants I picked one of the tasks and I'm posting there the challenge and its PowerShell script that might be helpful

We had to identity from an exported email domains data with DisplayName, UserPrincipalName, PrimarySmtpAddress and EmailAddresses
<pre>Get-Mailbox -ResultSize Unlimited |Select-Object DisplayName,UserPrincipalName,PrimarySmtpAddress, @{Name=“EmailAddresses”;Expression={$_.EmailAddresses |Where-Object {$_.PrefixString -ceq “smtp”} | ForEach-Object {$_.SmtpAddress}}} | Export-CSV C:\blog\allupnlist.csv</pre>
&nbsp;

<span style="color:#ff0000;"><strong>Script</strong> </span>- <a href="https://gallery.technet.microsoft.com/Read-domain-list-from-CSV-911b0dff">download</a> from Technet Gallery
<pre>###############################################################################################################################################################################################################################################
# Author Thiago Beier thiago.beier@gmail.com 
# Version: 1.0 - 2020-03-09 
# Read all upn, email address, proxysmtpaddress and primarysmtpaddress from a CSV file and breaks into current users with specified domain name and users with different upn who have email on specified domain
# Toronto, CANADA 
# Email: thiago.beier@gmail.com 
# https://www.linkedin.com/in/tbeier/ 
# https://twitter.com/thiagobeier
# thiagobeier.wordpress.com
############################################################################################################################################################################################################################################### 
#Redirects all powershell output to a file

#define reprot folder
$reportfolder = "report1"

#start transcript
Start-Transcript -Path "C:\temp\$reportfolder\Log-$(get-date -format 'MM_dd_yyyy-HH-mm').txt"

#domain list file
$domainlist1 = Get-Content .\domainlist.txt

#loop
foreach ($domain in $domainlist1) {
write-host $domain -ForegroundColor Blue
#define variable for the search domain
$searchdomain = $domain
write-host "users with domain:" $searchdomain "in PrimarySmtpAddress" -ForegroundColor Yellow
$find1 = (import-csv .\test-fulllist.csv | Where-Object {$_.primarysmtpaddress -like "*@$searchdomain*"}).count
write-host $find1 -ForegroundColor Red
#export current users on specified domain
import-csv .\test-fulllist.csv | Where-Object {$_.primarysmtpaddress -like "*@$searchdomain*"} | select DisplayName,UserPrincipalName,PrimarySmtpAddress | Export-Csv -NoTypeInformation -Encoding UTF8 C:\Temp\$reportfolder\current-users-on-$searchdomain.csv

#list users at different domains with this domain on proxysmtpaddress
write-host "users with domain:" "$searchdomain" "in EmailAddress that are from other domains" -ForegroundColor cyan
$find2 = (import-csv .\test-fulllist.csv | Where-Object {$_.emailaddresses -like "*$searchdomain*" -and $_.UserPrincipalName -notlike "*$searchdomain*"} | select UserPrincipalName).count #| measure
#export users on specified domain with different upn
import-csv .\test-fulllist.csv | Where-Object {$_.emailaddresses -like "*$searchdomain*" -and $_.UserPrincipalName -notlike "*$searchdomain*"} | select DisplayName,UserPrincipalName,PrimarySmtpAddress | Export-Csv -NoTypeInformation -Encoding UTF8 C:\Temp\$reportfolder\$searchdomain.csv
write-host "found" $find2 "users with" $domain "as proxysmtpaddress" -ForegroundColor Green
}</pre>
&nbsp;

thanks,

Thiago Beier
<a href="https://twitter.com/thiagobeier"><img title="Twitter" src="https://socialmediawidgets.files.wordpress.com/2014/03/twitter1.png" alt="Twitter" width="35" height="35" /></a><a href="https://www.linkedin.com/in/tbeier/"><img title="LinkedIn" src="https://socialmediawidgets.files.wordpress.com/2014/03/linkedin1.png" alt="LinkedIn" width="35" height="35" /></a><a href="https://www.facebook.com/TheBeier/"><img title="Facebook" src="https://socialmediawidgets.files.wordpress.com/2014/03/facebook1.png" alt="Facebook" width="35" height="35" /></a><a href="https://thiagobeier.wordpress.com/feed/"><img title="RSS" src="https://socialmediawidgets.files.wordpress.com/2014/03/rss1.png" alt="RSS" width="35" height="35" /></a>
