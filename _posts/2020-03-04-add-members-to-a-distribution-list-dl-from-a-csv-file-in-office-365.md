---
layout: post
title: Add members to a Distribution List (DL) from a CSV file in Office 365
date: 2020-03-04 06:30
author: beierca
comments: true
categories: [Administration, Exchange &amp; Office Server, Exchange Online, import from csv, Office365, Powershell, scripts]
---
Hi There,

This script will help you to add members to a Distribution Lists (DL) from a CSV file

You just need a csv file with two columns: distribution list name (dlistname) and member (members)

<img id="226396" src="https://gallery.technet.microsoft.com/site/view/file/226396/1/5.png" alt="" width="372" height="133" />

You can also combine this script with another one to add members to DL (Distribution Lists) as well.

<strong>Testing the csv file:</strong>

<em>Import-Csv .\create-dl.csv </em>

<strong>You should see the following</strong>

<img id="226395" src="https://gallery.technet.microsoft.com/site/view/file/226395/1/4.png" alt="" width="418" height="109" />

&nbsp;

<strong><span style="color:var(--color-text);">PowerShell code</span></strong>
<div class="scriptcode">
<div class="pluginEditHolder">
<pre class="powershell"><span class="powerShell__com">###########################################################################################    </span> 
<span class="powerShell__com"># Author Thiago Beier thiago.beier@gmail.com    </span> 
<span class="powerShell__com"># Version: 1.0 - 2020-FEB-28   </span> 
<span class="powerShell__com"># Adding user to a DL (Distribution List on Office 365) from CSV file</span> 
<span class="powerShell__com"># Toronto,CANADA    </span> 
<span class="powerShell__com"># Email: thiago.beier@gmail.com  </span> 
<span class="powerShell__com"># https://www.linkedin.com/in/tbeier/  </span> 
<span class="powerShell__com"># https://thigobeier.wordpress.com</span> 
<span class="powerShell__com">########################################################################################### </span> 
 
<span class="powerShell__com">#</span> 
<span class="powerShell__cmdlets">Import-Csv</span> .\add<span class="powerShell__operator">-</span>members<span class="powerShell__operator">-</span>to<span class="powerShell__operator">-</span>dl01.csv <span class="powerShell__operator">|</span> <span class="powerShell__keyword">foreach</span> {  
 
write<span class="powerShell__operator">-</span>host <span class="powerShell__string">"Adding user"</span> <span class="powerShell__variable">$_</span>.members <span class="powerShell__string">"to"</span> <span class="powerShell__variable">$_</span>.dlistname <span class="powerShell__string">"DL"</span> <span class="powerShell__operator">-</span>ForegroundColor Yellow 
 
Add<span class="powerShell__operator">-</span>DistributionGroupMember <span class="powerShell__operator">-</span>Identity <span class="powerShell__variable">$_</span>.dlistname <span class="powerShell__operator">-</span>Member <span class="powerShell__variable">$_</span>.members  
 
} 
</pre>
</div>
</div>
<div class="endscriptcode"><a href="https://thiagobeierblog.blob.core.windows.net/files/add-members-to-dl01.csv">Download</a> the csv file.

<a href="https://gallery.technet.microsoft.com/Add-members-to-a-1ab7b651?redir=0">Download</a> the file from Technet Gallery.</div>
<div></div>
<div><strong>Follow Me
</strong><a href="https://twitter.com/thiagobeier"><img title="Twitter" src="https://socialmediawidgets.files.wordpress.com/2014/03/twitter1.png?w=35&amp;h=35" alt="Twitter" width="35" height="35" /></a><a href="https://www.linkedin.com/in/tbeier/"><img title="LinkedIn" src="https://socialmediawidgets.files.wordpress.com/2014/03/linkedin1.png?w=35&amp;h=35" alt="LinkedIn" width="35" height="35" /></a><a href="https://www.facebook.com/TheBeier/"><img title="Facebook" src="https://socialmediawidgets.files.wordpress.com/2014/03/facebook1.png?w=35&amp;h=35" alt="Facebook" width="35" height="35" /></a><a href="https://thiagobeier.wordpress.com/feed/"><img title="RSS" src="https://socialmediawidgets.files.wordpress.com/2014/03/rss1.png?w=35&amp;h=35" alt="RSS" width="35" height="35" /></a></div>
