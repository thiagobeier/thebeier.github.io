---
layout: post
title: Microsoft Teams – PowerShell #2
date: 2020-04-27 15:00
author: beierca
comments: true
categories: [Administration, Automation, Exchange Online, Microsoft Teams, Office365, Powershell]
---
Hi there

At this post I'm covering basic tasks on Microsoft Teams using PowerShell.

1. Connecting to Microsoft Teams - <a href="https://docs.microsoft.com/en-us/powershell/module/teams/?view=teams-ps">Available</a> commands.
<pre>#Microsoft Teams Management

#install module
Install-Module -Name MicrosoftTeams -Force

#import module
Import-Module MicrosoftTeams

#connect teams
Connect-MicrosoftTeams</pre>
2. Creating New Teams
<pre>#create a private team name Team-01
New-Team -DisplayName “Team-01” -Visibility Private

#create a public team named Team-02
New-Team -DisplayName “Team-02” -Visibility Public</pre>
<img src="https://thiagobeierblog.blob.core.windows.net/posts/o365/teams/9.png" />

3. Creating New Teams Channel (create a team channel on Team-01), you need to retrieve Team-01 groupid on powershell
<pre>#create a new team channel under "Team-01" 
Get-AzureADGroup -SearchString "Team-01"

New-TeamChannel -GroupId 126b90a5-e65a-4fef-98e3-d9b49f4acf12 -DisplayName "Engineering" -MembershipType Private</pre>
<img src="https://thiagobeierblog.blob.core.windows.net/posts/o365/teams/10.png" />
<img src="https://thiagobeierblog.blob.core.windows.net/posts/o365/teams/11.png" />

4. Creating a New Application Setup Policy

TIP: when you create a new application policy Microsoft Teams use Org-wide Default as template. (all teams apps enabled on your current Org-wide default policy will copied over to the new policy)
<pre>#create a new teams application setup policy
New-CsTeamsAppSetupPolicy -Description Full-Experience -Identity App-Setup-Policy-01 -Confirm:$true</pre>
<img src="https://thiagobeierblog.blob.core.windows.net/posts/o365/teams/13.png" /><img style="color:var(--color-text);" src="https://thiagobeierblog.blob.core.windows.net/posts/o365/teams/12.png" />
<img style="color:var(--color-text);" src="https://thiagobeierblog.blob.core.windows.net/posts/o365/teams/14.png" />
<img style="color:var(--color-text);" src="https://thiagobeierblog.blob.core.windows.net/posts/o365/teams/15.png" />

5. Creating a New Live Events Policy
<pre>#List all current live events policies
Get-CsTeamsMeetingBroadcastPolicy -identity Global

#Create a new Live Event policy (Teams Meeting Broadcast Policy)
New-CSTeamsMeetingBroadcastPolicy -identity AllowLiveEvents

#Set this policy to allow live events (True)
Set-CsTeamsMeetingBroadcastPolicy -identity AllowLiveEvents -AllowBroadcastScheduling $true

#Assign this policy to a user
Grant-CsTeamsMeetingBroadcastPolicy -Identity tgermano@collabcan.com -PolicyName AllowLiveEvents -Verbose
#Clear the live event policy from a user
Grant-CsTeamsMeetingBroadcastPolicy -Identity thiago.beier@thebeier.com -PolicyName $null -Verbose
</pre>
<img src="https://thiagobeierblog.blob.core.windows.net/posts/o365/teams/8.png" />

<span style="color:#ff0000;"><strong>Download</strong> </span>the powershell content file from <a href="https://thiagobeierblog.blob.core.windows.net/posts/o365/teams/powershell2.txt">here</a>.

<strong>References</strong>

Microsoft Teams <a href="https://www.powershellgallery.com/packages/MicrosoftTeams/1.0.5">Powershell</a> module.
Microsoft Skype for <a href="https://www.microsoft.com/en-us/download/details.aspx?id=39366">Business</a> Powershell module.

Thanks,

Thiago Beier
<a href="https://twitter.com/thiagobeier"><img title="Twitter" src="https://socialmediawidgets.files.wordpress.com/2014/03/twitter1.png" alt="Twitter" width="35" height="35" /></a><a href="https://www.linkedin.com/in/tbeier/"><img title="LinkedIn" src="https://socialmediawidgets.files.wordpress.com/2014/03/linkedin1.png" alt="LinkedIn" width="35" height="35" /></a><a href="https://www.facebook.com/TheBeier/"><img title="Facebook" src="https://socialmediawidgets.files.wordpress.com/2014/03/facebook1.png" alt="Facebook" width="35" height="35" /></a><a href="https://thiagobeier.wordpress.com/feed/"><img title="RSS" src="https://socialmediawidgets.files.wordpress.com/2014/03/rss1.png" alt="RSS" width="35" height="35" /></a>
