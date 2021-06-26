---
layout: post
title: Exchange Online Export PST Tip.
date: 2021-02-18 22:41
author: beierca
comments: true
categories: [ediscovery, Exchange &amp; Office Server, Exchange Online, export pst, limits, registry key, tip]
---
Hi Everyone

Working on a client request to fix a retention policy that was setup wrongly we faced a PST limitation size during EXO export.

By default Exchange Online <strong>eDiscovery Export Tool</strong> limits PST size to 10 GB which means if your mailbox has more than 30 GB of size you'll have an export with 3 PST files of 10 GB each.

<img src="https://thiagobeierblog.blob.core.windows.net/posts/o365/tips/a3.png" />

&nbsp;

After first export we had the following:

<img src="https://thiagobeierblog.blob.core.windows.net/posts/o365/tips/a4.png" />

<strong>Fix - Registry File</strong>
<ol>
 	<li>close eDiscovery Export Tool</li>
 	<li>copy and paste registry key below and save as PstExportSize.reg , where "<strong>34359738368</strong>" corresponds to 32 GB mailbox (we exported all mailboxes sizes before we kicked this export to make sure we would have 1 PST file for the entire mailbox to be exported) - If you like Excel use <a href="https://thiagobeierblog.blob.core.windows.net/posts/o365/tips/pstExportSize-calc.xlsx">this spreadsheet</a> as cheat sheet.
Windows Registry Editor Version 5.00
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Exchange\Client\eDiscovery\ExportTool]
"PstSizeLimitInBytes"="34359738368"</li>
 	<li>double click on it as local admin on the workstation you're running this task
<ol>
 	<li>we tested on Edge and IE (Internet Explorer) to make sure the eDiscovery Export Tool was working fine before we used this fix.</li>
</ol>
</li>
</ol>
<strong>Registry key on <a href="https://notepad-plus-plus.org/downloads/">Notepad++</a></strong>

<img src="https://thiagobeierblog.blob.core.windows.net/posts/o365/tips/a5.png" />

<strong>References</strong>

https://docs.microsoft.com/en-us/microsoft-365/compliance/limits-for-content-search?view=o365-worldwide#export-limits

https://docs.microsoft.com/en-us/microsoft-365/compliance/change-the-size-of-pst-files-when-exporting-results?view=o365-worldwide

<strong><span style="color:#ff0000;">Check my <a style="color:#ff0000;" href="https://github.com/thiagobeier/scripts/blob/master/README.md"><span style="color:#0000ff;">Github</span></a> repository</span></strong>

Thanks,

<!-- /wp:paragraph -->

Thiago Beier

<a href="https://twitter.com/thiagobeier"><img title="Twitter" src="https://socialmediawidgets.files.wordpress.com/2014/03/twitter1.png" alt="Twitter" width="35" height="35" /></a><a href="https://www.linkedin.com/in/tbeier/"><img title="LinkedIn" src="https://socialmediawidgets.files.wordpress.com/2014/03/linkedin1.png" alt="LinkedIn" width="35" height="35" /></a><a href="https://www.facebook.com/TheBeier/"><img title="Facebook" src="https://socialmediawidgets.files.wordpress.com/2014/03/facebook1.png" alt="Facebook" width="35" height="35" /></a><a href="https://thiagobeier.wordpress.com/feed/"><img title="RSS" src="https://socialmediawidgets.files.wordpress.com/2014/03/rss1.png" alt="RSS" width="35" height="35" /></a>
