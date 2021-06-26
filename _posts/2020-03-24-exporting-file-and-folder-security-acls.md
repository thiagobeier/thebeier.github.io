---
layout: post
title: Exporting File and Folder security ACLs
date: 2020-03-24 13:00
author: beierca
comments: true
categories: [acls, Active Directory, Administration, export permissions, file security, file server, file share, folder security, permissions, Powershell, Security, security info, Storage, Windows Desktop, Windows Server]
---
Hi there

Have you ever to export file and folder security ACLs from a specific folder on disk or remote network path on a server?

The following approach it's kind old school but works.

cd c:\temp
cacls . to list current dir only
cacls *.* to list all folder and subfolders from the current folder (root folder)

<img src="https://thiagobeierblog.blob.core.windows.net/posts/o365/tips/59.png" />

However, you can have a better and filtered result using the following PowerShell file.
<pre>###############################################################################################################################################################################################################################################
# Author Thiago Beier thiago.beier@gmail.com 
# Version: 1.0 - 2020-03-10
# Export disk permissions (folder permissions to CSV)
# Toronto, CANADA 
# Email: thiago.beier@gmail.com 
# https://www.linkedin.com/in/tbeier/ 
# https://twitter.com/thiagobeier
# thiagobeier.wordpress.com
###############################################################################################################################################################################################################################################

#folter to scan - retrieve security information from
$FolderPath = Get-ChildItem -Directory -Path 'C:\temp' -Recurse -Force -ErrorAction SilentlyContinue

#get date time and adds to the log file
$gt=Get-Date -Format "dddd-mm-dd-yyyy-HH-mm-ss"

$Report = @()
Foreach ($Folder in $FolderPath) {
$Acl = Get-Acl -Path $Folder.FullName
foreach ($Access in $acl.Access)
{
$Properties = [ordered]@{'FolderName'=$Folder.FullName;'ADGroup or User'=$Access.IdentityReference;'Permissions'=$Access.FileSystemRights;'Inherited'=$Access.IsInherited}
$Report += New-Object -TypeName PSObject -Property $Properties
}
}
#expor tto CSV with date and time on CSV file
$Report | Export-Csv -path "c:\temp\FolderPermissions-$gt.csv"</pre>
<strong>Feel free </strong>to change <strong>c:\temp</strong> under <strong>$FolderPath</strong> variable and filename at <strong>line #28</strong> for the CSV file path

<img src="https://thiagobeierblog.blob.core.windows.net/posts/o365/tips/62.png" />

<strong>c:\temp folder content with all files exported</strong> (different exports)

<img src="https://thiagobeierblog.blob.core.windows.net/posts/o365/tips/60.png" />

<strong>CSV file content output</strong>

<img src="https://thiagobeierblog.blob.core.windows.net/posts/o365/tips/61.png" />

<strong><span style="color:#ff0000;">Tip!</span></strong> - you can <strong>download</strong> this script from GitHub <a href="https://github.com/thiagobeier/scripts/blob/master/README.md">repository</a>.

thanks,

Thiago Beier
<a href="https://twitter.com/thiagobeier"><img title="Twitter" src="https://socialmediawidgets.files.wordpress.com/2014/03/twitter1.png" alt="Twitter" width="35" height="35" /></a><a href="https://www.linkedin.com/in/tbeier/"><img title="LinkedIn" src="https://socialmediawidgets.files.wordpress.com/2014/03/linkedin1.png" alt="LinkedIn" width="35" height="35" /></a><a href="https://www.facebook.com/TheBeier/"><img title="Facebook" src="https://socialmediawidgets.files.wordpress.com/2014/03/facebook1.png" alt="Facebook" width="35" height="35" /></a><a href="https://thiagobeier.wordpress.com/feed/"><img title="RSS" src="https://socialmediawidgets.files.wordpress.com/2014/03/rss1.png" alt="RSS" width="35" height="35" /></a>
