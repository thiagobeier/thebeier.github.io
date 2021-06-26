---
layout: post
title: Dynamically Add members to a Team's Team.
date: 2020-04-29 12:30
author: beierca
comments: true
categories: [Administration, Automation, Azure AD, Microsoft Teams, security group]
---
Hi there

One simple task that turn into a nightmare when you're managing medium to large environments on Teams it's how you manage membership group assignment and Teams' Team membership assignment.

A company with 24.000 users with several Teams' Teams all over the company created by department globally asked to automate Team membership.

First things first I thought what's the goal if you can't add more than 5000 users to a Team's team? We checked with all departments if that information was true.
<ul>
	<li>retrieved all Security Groups membership list (departmental security groups)</li>
	<li>reported any group with more than 5000 users (count the owner + 4999 users for this math)</li>
	<li>got a Go / No Go from the client to try out dynamic Azure AD Groups membership for synced from On-premises AD - locally all Security Groups are managed by an IM (Identity Management) Tool.</li>
	<li>we determined group membership based on user attributes such as "Department, Security Group Name, etc.)</li>
</ul>
Have in mind that every Team's team creates a Office 365 Group then you need to go on Azure AD and for each Office 365 group and configure dynamic membership rules in order to add users dynamically to those groups.
<ol>
	<li>Create o New Team on Teams with no members - Name: Demo
<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/o365/teams/4/14.png" /></li>
	<li>Double check that you're the Owner and there's no additional member to this group
<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/o365/teams/4/15.png" /></li>
	<li>Open Azure Active Directory Admin Center - <a href="https://aad.portal.azure.com/#blade/Microsoft_AAD_IAM/GroupsManagementMenuBlade/AllGroups">link</a></li>
	<li>Select All services on Left Blade and select Groups on the right blade
<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/o365/teams/4/13.png" /></li>
	<li>Search for your Team Name "Demo"
<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/o365/teams/4/16.png" /></li>
	<li>check the Properties menu for this group, you should see Membership type: assigned and Group type: office
<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/o365/teams/4/18.png" /></li>
	<li>change the Membership type from assigned to Dynamic user then click on "Edit dynamic query" blue link under Dynamic user members *
<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/o365/teams/4/19.png" />
<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/o365/teams/4/20.png" /></li>
	<li>paste the following rule without the "" and click SAVE
"user.assignedPlans -any (assignedPlan.servicePlanId -eq "efb87545-963c-4e0d-99df-69c6916d9eb0" -and assignedPlan.capabilityStatus -eq "Enabled")"
<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/o365/teams/4/24.png" />
<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/o365/teams/4/21.png" /></li>
	<li>on the next screen click SAVE again confirm the changes and wait for the group to populate (it takes up to 15 min to finish)</li>
	<li><img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/o365/teams/4/22.png" />
<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/o365/teams/4/23.png" /></li>
	<li>click on Overview and check Membership processing status - you should see "Evaluating" and at Membership last updated will be "in progress" with 0 members and 0 group(s) and 0 Device(s)
<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/o365/teams/4/25.png" /></li>
	<li>wait for this process to finish and check if the group membership has been updated</li>
	<li>now you should be able to see <span style="text-decoration:underline;">Membership processing status</span> as Update complete and <span style="text-decoration:underline;">Membership last updated</span> with the time stamp format: <strong>4/22/2020, 12:58:02 AM
<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/o365/teams/4/26.png" />
</strong></li>
	<li>click on Audit logs to check its process status
<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/o365/teams/4/29.png" /></li>
	<li>click on members tab on left and check the users
<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/o365/teams/4/27.png" /></li>
	<li>all users who have the service plan id equals : efb87545-963c-4e0d-99df-69c6916d9eb0 corresponding to "<strong>Exchange Online (Plan 2)</strong>" are now members of this Team on Microsoft Teams. <span style="color:#ff0000;"><strong>!Click</strong></span> <a href="https://docs.microsoft.com/en-us/azure/active-directory/users-groups-roles/licensing-service-plan-reference">here</a> - to understand more about Product Names and service plan identifiers for licensing.</li>
	<li>Go back to Teams Admin Portal \ Teams \ Manage Teams <a href="https://admin.teams.microsoft.com/teams/manage">menu</a> click at Demo Team and check if the users are now showing as members on it.
<img style="max-width:100%;" src="https://thiagobeierblog.blob.core.windows.net/posts/o365/teams/4/28.png" /></li>
</ol>
<span style="color:#ff0000;"><strong>!TIPs</strong></span>
<ul>
	<li>you can use Azure AD synced security groups to retrieve its members then assign those users to a Teams' team.</li>
	<li>you can use cloud only groups members to assign the same rules to a Teams' team.</li>
</ul>
<strong>References</strong>
https://docs.microsoft.com/en-us/microsoftteams/limits-specifications-teams
https://docs.microsoft.com/en-us/microsoftteams/dynamic-memberships
https://docs.microsoft.com/en-ca/azure/active-directory/users-groups-roles/groups-dynamic-membership

<em><strong>My setup</strong></em>
OS Name Microsoft Windows 10 Enterprise
Version 10.0.18363 Build 18363
ADDS: Windows Server 2016/2019 Azure AD latest version for AD sync

Thanks,

Thiago Beier
<a href="https://twitter.com/thiagobeier"><img title="Twitter" src="https://socialmediawidgets.files.wordpress.com/2014/03/twitter1.png" alt="Twitter" width="35" height="35" /></a><a href="https://www.linkedin.com/in/tbeier/"><img title="LinkedIn" src="https://socialmediawidgets.files.wordpress.com/2014/03/linkedin1.png" alt="LinkedIn" width="35" height="35" /></a><a href="https://www.facebook.com/TheBeier/"><img title="Facebook" src="https://socialmediawidgets.files.wordpress.com/2014/03/facebook1.png" alt="Facebook" width="35" height="35" /></a><a href="https://thiagobeier.wordpress.com/feed/"><img title="RSS" src="https://socialmediawidgets.files.wordpress.com/2014/03/rss1.png" alt="RSS" width="35" height="35" /></a>
