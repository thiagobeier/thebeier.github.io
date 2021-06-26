---
layout: post
title: WMI filters on Windows 7 and Windows 10 – Case Sensitive
date: 2017-02-03 22:44
author: beierca
comments: true
categories: [Windows Desktop, Windows Server]
---
<span style="font-family:Times New Roman;font-size:12pt;">Hi again, after a long period without posting I'm here again.
</span>

<span style="font-family:Times New Roman;font-size:12pt;">Today I'm going to share with you a sing post about WMI filters on Windows 7 and 10
</span>

<span style="font-family:Times New Roman;font-size:12pt;">This week to solve a GPO issue related to "networking connectivity loss" affecting Windows 10 Workstations we deployed to different GPOs for Drive Mapping.
</span>

<span style="font-family:Times New Roman;font-size:12pt;">After a few minutes, we figured out that the GPO wasn't being applied.
</span>

<span style="font-family:Times New Roman;font-size:12pt;"><strong>GP Result </strong>
</span>

<img src="http://thiagobeier.files.wordpress.com/2017/02/020417_0311_wmifilterso1.jpg" alt="" /><span style="font-family:Times New Roman;font-size:12pt;">
</span>

<img src="http://thiagobeier.files.wordpress.com/2017/02/020417_0311_wmifilterso2.jpg" alt="" /><span style="font-family:Times New Roman;font-size:12pt;">
</span>

<span style="font-family:Times New Roman;font-size:12pt;"><strong>WMI filter created
</strong></span>

<span style="font-family:Times New Roman;font-size:12pt;">Windows 7<strong>
</strong></span>

<img src="http://thiagobeier.files.wordpress.com/2017/02/020417_0311_wmifilterso3.png" alt="" /><span style="font-family:Times New Roman;font-size:12pt;">
</span>

<span style="font-family:Times New Roman;font-size:12pt;">and Windows 10
</span>

<img src="http://thiagobeier.files.wordpress.com/2017/02/020417_0311_wmifilterso4.png" alt="" /><span style="font-family:Times New Roman;font-size:12pt;">
</span>

<span style="font-family:Times New Roman;font-size:12pt;"><strong>Resolution </strong>
</span>

<span style="font-family:Times New Roman;font-size:12pt;">As the WMI interpreter is Case Sensitive copy and past the appropriated commands to be executed as shown below respecting <span style="background-color:yellow;">Capitalized</span> and <span style="background-color:yellow;">UPPERCASED</span> words
</span>

<span style="font-family:Times New Roman;font-size:12pt;">Please, also have in mind that during the CTRL+C CTRL+V process the "" might change into another '' and this is also one more reason that causes WMI filters to fail.
</span>

<span style="font-family:Times New Roman;font-size:12pt;">Windows 7
<strong>select * from Win32_OperatingSystem WHERE Version like "6.1%" AND ProductType="1"</strong><em>
</em>
</span>

<span style="font-family:Times New Roman;font-size:12pt;"><em>Windows 10
</em><strong>select * from Win32_OperatingSystem WHERE Version like "10.%" AND ProductType="1" </strong>
</span>

<span style="font-family:Times New Roman;font-size:12pt;">Happy to have you here,
</span>
<p style="background:white;"><span style="color:#5b9bd5;"><span style="font-family:Arial;"><span style="font-size:9pt;"><strong>Thiago Beier</strong></span><span style="color:#222222;"><span style="font-size:12pt;">
</span><span style="font-size:9pt;"><strong>MCSA 2012 | MCSE: Private Cloud and Communication</strong>
<span style="color:red;"><strong>Totonro, ON – CANADA</strong><span style="color:#222222;">
skype thiagog-df
</span></span></span></span></span><span style="font-family:Times New Roman;font-size:9pt;">https://ca.linkedin.com/in/tbeier</span><span style="color:#222222;font-size:12pt;"><span style="font-family:Arial;">
</span><span style="font-family:Times New Roman;">
</span></span></span></p>
