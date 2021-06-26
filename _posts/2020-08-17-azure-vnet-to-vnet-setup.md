---
layout: post
title: Azure: VNET-to-VNET setup
date: 2020-08-17 00:00
author: beierca
comments: true
categories: [Azure, Networking, Peering, subscription, VNET]
---
<p></p>

<!-- wp:paragraph -->
</p><p>Hi there</p><p>In this article I'm demonstrating how to configure vnet-to-vnet peering setup between 02 (two) different companies / subscriptions.</p><p>Company A:<br />subscription A:<br />Resource Group:<br />VNET-A name:<br />Address space:<br />subnet1:<br />gateway subnet:<br />user: thiago.beier@mydomain.com invite as guest with "network contributor' role<br />VNET resource id:</p><p>Company B:<br />subscription B:<br />Resource Group:<br />VNET-B name:<br />Address space:<br />subnet1:<br />gateway subnet:<br />user: thiago.beier@mydomain.com invite as guest with "network contributor' role<br />VNET resource id:</p><p>Steps</p><ol><li>after you have all resource groups fine, all users to manage each subscription and the vnet resourceids you can proceed</li><li>add userB (from subscription B) on VNET-A as "network contributor" role</li><li>accept invitation on userB email and log on Azure directory to make sure you can see CompanyB vnet info</li><li>add userA (from subscription A) on VNET-B as "network contributor" role</li><li>accept invitation on userB email and log on Azure directory to make sure you can see CompanyA vnet info</li><li>log on Company A:</li><li>go to VNET \ peerings</li><li>click + add</li><li>fill the following<ol><li><div id="_tsx_e_14156" class="azc-form-labelcontainer azc-text-label azc-text-sublabel-neighbor" aria-hidden="false">Name of the peering from og-cac-vnet1 to remote virtual network:<div id="_tsx_e_14158" class="azc-required-balloon fxc-base azc-control azc-dockedballoon-requiredwidget azc-dockedballoon-required"> </div></div><div class="azc-formElementSubLabelContainer"> </div></li><li>check "I know my resource id" and paste the target vnet resource id (company B)</li><li>on Directory, search and select the "target subscription / directory" from where you accepted the invitation as userA</li><li>click Authenticate (blue button) and go through the new browser tab that'll open, go through the authentication process using userA</li><li>click Ok to finish</li><li>repeat the same steps 1 to 5 above in this section at Company B, with logged as userB, using VNET-A resource id when you're finished you'll have the peering as connected and not as initiated (waiting one side of the settings)</li></ol></li><li>go to a VM on source or target subscription<ol><li>check default route</li><li>check ip address</li><li>ping target ip address</li><li>ssh or rdp on the target vm</li></ol></li></ol><p>&nbsp;</p><p>References<br />https://docs.microsoft.com/en-us/azure/virtual-network/create-peering-different-subscriptions</p><p>&nbsp;</p><p><strong><span style="color:#ff0000;">Check my <a style="color:#ff0000;" href="https://github.com/thiagobeier/scripts/blob/master/README.md"><span style="color:#0000ff;">Github</span></a> repository</span></strong></p><p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
</p><p>Thanks,</p><p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
</p><p>Thiago Beier<br /><a href="https://twitter.com/thiagobeier"><img title="Twitter" src="https://socialmediawidgets.files.wordpress.com/2014/03/twitter1.png" alt="Twitter" width="35" height="35" /></a><a href="https://www.linkedin.com/in/tbeier/"><img title="LinkedIn" src="https://socialmediawidgets.files.wordpress.com/2014/03/linkedin1.png" alt="LinkedIn" width="35" height="35" /></a><a href="https://www.facebook.com/TheBeier/"><img title="Facebook" src="https://socialmediawidgets.files.wordpress.com/2014/03/facebook1.png" alt="Facebook" width="35" height="35" /></a><a href="https://thiagobeier.wordpress.com/feed/"><img title="RSS" src="https://socialmediawidgets.files.wordpress.com/2014/03/rss1.png" alt="RSS" width="35" height="35" /></a></p><p>
<!-- /wp:paragraph -->


