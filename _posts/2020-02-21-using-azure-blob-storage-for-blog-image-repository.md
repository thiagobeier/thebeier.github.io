---
layout: post
title: Using Azure blob storage for blog image repository
date: 2020-02-21 01:08
author: beierca
comments: true
categories: [Azure, Blog, storage account, Uncategorized]
---
<header class="post-header">
<h1 class="post-title p-name"><a style="font-size:16px;font-weight:400;" href="https://docs.microsoft.com/azure/azure-portal?WT.mc_id=docs-azuredevtips-micrum">Azure Portal Documentation</a><span style="color:var(--color-text);font-size:16px;font-weight:400;">.</span></h1>
</header>
<div class="post-content e-content">

<a href="https://www.youtube.com/watch?v=A0uXwdLDzf4&amp;list=PLLasX02E8BPCNCK8Thcxu-Y-XcBUbhFWC&amp;index=1?WT.mc_id=youtube-azuredevtips-micrum">How to use keyboard shortcuts in the Azure portal</a>.
<ol>
	<li>Create a Free Azure account - <a href="https://azure.microsoft.com/en-ca/free/">click here</a></li>
	<li>Create your first Resource Group on <a href="https://portal.azure.com/">Azure portal</a>
<ol>
	<li>On Azure Portal click on <em><strong>Create a Resource
<img class="alignnone size-full wp-image-428" src="https://thiagobeier.files.wordpress.com/2020/02/1.png" alt="1" width="794" height="247" /></strong></em></li>
	<li>Search for Resource Group on Azure marketplace and select it
<img class="alignnone size-full wp-image-429" src="https://thiagobeier.files.wordpress.com/2020/02/2.png" alt="2" width="637" height="400" /><img class="alignnone size-full wp-image-430" src="https://thiagobeier.files.wordpress.com/2020/02/3.png" alt="3" width="946" height="405" /></li>
	<li>Name the Resource "MyBlog" and click create
<img class="alignnone size-full wp-image-431" src="https://thiagobeier.files.wordpress.com/2020/02/4.png" alt="4" width="784" height="900" /></li>
	<li>Wait until the Resource is created then Access it from the Home Button
<img class="alignnone size-full wp-image-432" src="https://thiagobeier.files.wordpress.com/2020/02/5.png" alt="5" width="961" height="202" /></li>
</ol>
</li>
	<li>Create your Azure Storage Account
<ol>
	<li>go the Azure marketplace and search for "Storage Account" and select it from drop down menu
<img class="alignnone size-full wp-image-433" src="https://thiagobeier.files.wordpress.com/2020/02/6.png" alt="6" width="811" height="283" /></li>
	<li>Click <em><strong>create </strong></em>on the next screen<img class="alignnone size-full wp-image-434" src="https://thiagobeier.files.wordpress.com/2020/02/7.png" alt="7" width="904" height="435" /></li>
	<li>Give a <strong>name</strong> for the storage account i.e.: fielandfoldersblog , define <strong>Account kind</strong>: Storage (general purpose v1) and <strong>Replication</strong>: LRS and click on <strong>review-create</strong>
<img class="alignnone size-full wp-image-435" src="https://thiagobeier.files.wordpress.com/2020/02/8.png" alt="8" width="862" height="900" /></li>
	<li>On <strong>Review + Create</strong>, select <strong>Create </strong>and wait until this process is complete
<img class="alignnone size-full wp-image-437" src="https://thiagobeier.files.wordpress.com/2020/02/9.png" alt="9" width="792" height="893" />
<img class="alignnone size-full wp-image-438" src="https://thiagobeier.files.wordpress.com/2020/02/10.png" alt="10" width="957" height="418" /></li>
	<li>Go to the <strong>Storage Account resource</strong> and select the option "<strong>Containers</strong>" on main screen
<img class="alignnone size-full wp-image-439" src="https://thiagobeier.files.wordpress.com/2020/02/11.png" alt="11" width="957" height="683" /></li>
	<li>click on <strong>"+" Container</strong> to add a container - please add 02 containers (one for files one for posts)
<img class="alignnone size-full wp-image-440" src="https://thiagobeier.files.wordpress.com/2020/02/12.png" alt="12" width="965" height="269" />
<img class="alignnone size-full wp-image-441" src="https://thiagobeier.files.wordpress.com/2020/02/13.png" alt="13" width="955" height="462" />
<img class="alignnone size-full wp-image-442" src="https://thiagobeier.files.wordpress.com/2020/02/14.png" alt="14" width="954" height="460" /></li>
</ol>
</li>
</ol>
Great thanks,

I hope you like this post.

</div>
