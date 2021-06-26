---
layout: post
title: Create a Distribution List (DL) from CSV on Office 365
date: 2020-03-01 11:00
author: beierca
comments: true
categories: [Administration, Exchange &amp; Office Server, Exchange Online, import from csv, Office365, Powershell, scripts]
---
Hi There,

This script will help you to create Distribution Lists (DL) from a CSV file and will hide all those DLs (Distribution Lists) from the GAL (Global Address List).

We had to use a similar script to create Temporary DLs during a migration process (with similar names however with -Mig on its name).

You can also combine this script with another one to add members to DL (Distribution Lists) as well.

<strong>Testing the csv file:</strong>

<em>Import-Csv .\create-dl.csv </em>

<strong>You should see the following</strong>

<img src="https://github.com/thiagobeier/scripts/raw/master/5/media/b5ede4ca5c29a1b1eba72555ac9d1af9.png" />

<img src="https://github.com/thiagobeier/scripts/raw/master/5/media/99d72939e87113c8aed6959980dc11a2.png" />
<div class="scriptcode">
<div class="pluginEditHolder">
<div class="title"><strong>PowerShell</strong></div>
<pre>###########################################################################################     

# Author Thiago Beier <a href="mailto:thiago.beier@gmail.com">thiago.beier@gmail.com</a>     

# Version: 2.0 - 2020-MAI-01    

# Create a DL (Distribution List on Office 365) from CSV file 

# Toronto,CANADA     

# Email: <a href="mailto:thiago.beier@gmail.com">thiago.beier@gmail.com</a>   

# <a href="https://www.linkedin.com/in/tbeier/%C2%A0%C2%A0%C2%A0" rel="nofollow">https://www.linkedin.com/in/tbeier/   </a>

# <a href="https://thigobeier.wordpress.com%20/" rel="nofollow">https://thigobeier.wordpress.com </a>

###########################################################################################  

Import-Csv .\create-dl.csv | foreach {

write-host "Creating DL:" $_.dlistname -ForegroundColor Blue

write-host $_.dlistname -ForegroundColor green

New-DistributionGroup -Name $<em>.dlistname -Alias $</em>.dlalias -DisplayName $<em>.dldisplayname -PrimarySmtpAddress $</em>.dlsmtpaddress -Type security

write-host $_.dlalias -ForegroundColor Yellow

Set-DistributionGroup $_.dlistname -HiddenFromAddressListsEnabled $True

}</pre>
</div>
</div>
&nbsp;

<a href="https://github.com/thiagobeier/scripts/blob/master/5/create-dl.csv">Download</a> the csv file.

<a href="https://github.com/thiagobeier/scripts/blob/master/5/create-dl.csv">Download</a> the script from Gihub Repo.

<strong>Thiago Beier</strong>
<a href="https://twitter.com/thiagobeier"><img title="Twitter" src="https://socialmediawidgets.files.wordpress.com/2014/03/twitter1.png" alt="Twitter" width="35" height="35" /></a><a href="https://www.linkedin.com/in/tbeier/"><img title="LinkedIn" src="https://socialmediawidgets.files.wordpress.com/2014/03/linkedin1.png" alt="LinkedIn" width="35" height="35" /></a><a href="https://www.facebook.com/TheBeier/"><img title="Facebook" src="https://socialmediawidgets.files.wordpress.com/2014/03/facebook1.png" alt="Facebook" width="35" height="35" /></a><a href="https://thiagobeier.wordpress.com/feed/"><img title="RSS" src="https://socialmediawidgets.files.wordpress.com/2014/03/rss1.png" alt="RSS" width="35" height="35" /></a>
