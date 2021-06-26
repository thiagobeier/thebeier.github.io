---
layout: post
title: OneDrive for Business - Sync Settings
date: 2021-03-18 12:00
author: beierca
comments: true
categories: [M365, Management, Office365, OneDrive, Security, sync settings]
---
<!-- wp:paragraph -->
<p><strong>OneDrive sync settings</strong></p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>You can use these settings to control syncing files in OneDrive and SharePoint Online</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>Log into your M365 tenant</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>Go to OneDrive admin portal</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>All admin centers</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>https://admin.microsoft.com/Adminportal/Home?source=applauncher#/alladmincenters</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>click on OneDrive</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>https://admin.onedrive.com/</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>click on Sync (on the left tab menu) or go from here <a href="https://admin.onedrive.com/?v=SyncSettings">https://admin.onedrive.com/?v=SyncSettings</a></p>
<!-- /wp:paragraph -->

<!-- wp:image {"sizeSlug":"large"} -->
<figure class="wp-block-image size-large"><img src="https://thiagobeierblog.blob.core.windows.net/posts/o365/od4b/1/1.png" alt="" /></figure>
<!-- /wp:image -->

<!-- wp:paragraph -->
<p>By default any computer from any AD domain can sync OneDrive files</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>Select “allow syncing only on PCs joined to specific domains”</p>
<!-- /wp:paragraph -->

<!-- wp:image {"sizeSlug":"large"} -->
<figure class="wp-block-image size-large"><img src="https://thiagobeierblog.blob.core.windows.net/posts/o365/od4b/1/2.png" alt="" /></figure>
<!-- /wp:image -->

<!-- wp:paragraph -->
<p>To get your AD obejctGUID go to your Domain Controller</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>Run powershell as administrator</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>Run get-addomain &lt;enter&gt;</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>Copy the ObjectGUID value</p>
<!-- /wp:paragraph -->

<!-- wp:image {"sizeSlug":"large"} -->
<figure class="wp-block-image size-large"><img src="https://thiagobeierblog.blob.core.windows.net/posts/o365/od4b/1/3.png" alt="" /></figure>
<!-- /wp:image -->

<!-- wp:paragraph -->
<p>Or you can only run the following</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p><em>(get-addomain).objectguid</em></p>
<!-- /wp:paragraph -->

<!-- wp:image {"sizeSlug":"large"} -->
<figure class="wp-block-image size-large"><img src="https://thiagobeierblog.blob.core.windows.net/posts/o365/od4b/1/4.png" alt="" /></figure>
<!-- /wp:image -->

<!-- wp:paragraph -->
<p>Now proceed with your setup</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>Before</p>
<!-- /wp:paragraph -->

<!-- wp:embed {"url":"https:\/\/thiagobeierblog.blob.core.windows.net\/posts\/o365\/od4b\/1\/5.png","type":"rich","providerNameSlug":"embed","className":""} -->
<figure class="wp-block-embed is-type-rich is-provider-embed wp-block-embed-embed"><div class="wp-block-embed__wrapper">
https://thiagobeierblog.blob.core.windows.net/posts/o365/od4b/1/5.png
</div></figure>
<!-- /wp:embed -->

<!-- wp:paragraph -->
<p>After</p>
<!-- /wp:paragraph -->

<!-- wp:embed {"url":"https:\/\/thiagobeierblog.blob.core.windows.net\/posts\/o365\/od4b\/1\/6.png","type":"rich","providerNameSlug":"embed","className":""} -->
<figure class="wp-block-embed is-type-rich is-provider-embed wp-block-embed-embed"><div class="wp-block-embed__wrapper">
https://thiagobeierblog.blob.core.windows.net/posts/o365/od4b/1/6.png
</div><figcaption>Copy Objectguid from ADDS and paste it Click Save Go back to a non domain joined workstation and try to sync OneDrive from there </figcaption></figure>
<!-- /wp:embed -->

<!-- wp:paragraph -->
<p>Error when you try from a non-domain joined workstation</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>EN (English)</p>
<!-- /wp:paragraph -->

<!-- wp:embed {"url":"https:\/\/thiagobeierblog.blob.core.windows.net\/posts\/o365\/od4b\/1\/7.png","type":"rich","providerNameSlug":"embed","className":""} -->
<figure class="wp-block-embed is-type-rich is-provider-embed wp-block-embed-embed"><div class="wp-block-embed__wrapper">
https://thiagobeierblog.blob.core.windows.net/posts/o365/od4b/1/7.png
</div></figure>
<!-- /wp:embed -->

<!-- wp:paragraph -->
<p>FR (French)</p>
<!-- /wp:paragraph -->

<!-- wp:embed {"url":"https:\/\/thiagobeierblog.blob.core.windows.net\/posts\/o365\/od4b\/1\/8.png","type":"rich","providerNameSlug":"embed","className":""} -->
<figure class="wp-block-embed is-type-rich is-provider-embed wp-block-embed-embed"><div class="wp-block-embed__wrapper">
https://thiagobeierblog.blob.core.windows.net/posts/o365/od4b/1/8.png
</div></figure>
<!-- /wp:embed -->

<!-- wp:paragraph -->
<p>What if you had synced OneDrive before IT department made changes on sync settings?</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>After the settings are saved and replicated on M365 tenant you’ll get the following warning</p>
<!-- /wp:paragraph -->

<!-- wp:image {"sizeSlug":"large"} -->
<figure class="wp-block-image size-large"><img src="https://thiagobeierblog.blob.core.windows.net/posts/o365/od4b/1/9.png" alt="" /></figure>
<!-- /wp:image -->

<!-- wp:image {"sizeSlug":"large"} -->
<figure class="wp-block-image size-large"><img src="https://thiagobeierblog.blob.core.windows.net/posts/o365/od4b/1/10.png" alt="" /></figure>
<!-- /wp:image -->

<!-- wp:paragraph -->
<p>Files previously synced will continue on users’ profile if you block sync settings after users had already set this up.</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>After settings are replicated at M365/O365 you should see the following screen popping up</p>
<!-- /wp:paragraph -->

<!-- wp:image {"sizeSlug":"large"} -->
<figure class="wp-block-image size-large"><img src="https://thiagobeierblog.blob.core.windows.net/posts/o365/od4b/1/11.png" alt="" /></figure>
<!-- /wp:image -->

<!-- wp:paragraph -->
<p>Additional settings (Next Article)</p>
<!-- /wp:paragraph -->

<!-- wp:list -->
<ul><li>Show the sync button on the OneDrive website</li><li>Block sync on Mac OS</li><li>Block syncing of specific file types (you have to specify them)</li></ul>
<!-- /wp:list -->

<!-- wp:paragraph -->
<p>References</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>https://docs.microsoft.com/en-us/onedrive/allow-syncing-only-on-specific-domains</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>manage sharepoint online</p>
<!-- /wp:paragraph -->

<!-- wp:table -->
<figure class="wp-block-table"><table><tbody><tr><td class="has-text-align-left" data-align="left">Get-Module -Name Microsoft.Online.SharePoint.PowerShell -ListAvailable | Select Name,Version Install-Module -Name Microsoft.Online.SharePoint.PowerShell   <br><br>Answer Y (yes) or A (yes to all)   <br><br>$sposite = "https://yourtenantname-admin.sharepoint.com/" <br><br>Connect-SPOService -Url $sposite -Credential admin@yourtenantname.onmicrosoft.com<br><br>get-SPOTenantSyncClientRestriction    </td></tr></tbody></table></figure>
<!-- /wp:table -->

<!-- wp:image {"sizeSlug":"large"} -->
<figure class="wp-block-image size-large"><img src="https://thiagobeierblog.blob.core.windows.net/posts/o365/od4b/1/12.png" alt="" /></figure>
<!-- /wp:image -->

<!-- wp:paragraph -->
<p><strong>Check my&nbsp;<a href="https://github.com/thiagobeier/scripts/blob/master/README.md">Github</a>&nbsp;repositoryf</strong></p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>Thanks,</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>Thiago Beier</p>
<!-- /wp:paragraph -->

<!-- wp:image {"linkDestination":"custom"} -->
<figure class="wp-block-image"><a href="https://twitter.com/thiagobeier"><img src="https://socialmediawidgets.files.wordpress.com/2014/03/twitter1.png?w=35&amp;h=35" alt="Twitter" title="Twitter" /></a></figure>
<!-- /wp:image -->

<!-- wp:image {"linkDestination":"custom"} -->
<figure class="wp-block-image"><a href="https://www.linkedin.com/in/tbeier/"><img src="https://socialmediawidgets.files.wordpress.com/2014/03/linkedin1.png?w=35&amp;h=35" alt="LinkedIn" title="LinkedIn" /></a></figure>
<!-- /wp:image -->

<!-- wp:image {"linkDestination":"custom"} -->
<figure class="wp-block-image"><a href="https://www.facebook.com/TheBeier/"><img src="https://socialmediawidgets.files.wordpress.com/2014/03/facebook1.png?w=35&amp;h=35" alt="Facebook" title="Facebook" /></a></figure>
<!-- /wp:image -->

<!-- wp:image {"linkDestination":"custom"} -->
<figure class="wp-block-image"><a href="https://thiagobeier.wordpress.com/feed/"><img src="https://socialmediawidgets.files.wordpress.com/2014/03/rss1.png?w=35&amp;h=35" alt="RSS" title="RSS" /></a></figure>
<!-- /wp:image -->
