---
title: Deploying a static website to IIS
author: Adithya Vijay
date: 2022-02-18 12:41:00 +0800
categories: [Blogging, deployment]
tags: [web development deployment iis]     # TAG names should always be lowercase
---
### Introduction
Let's discuss on how we can deploy a static website to Microsofts web server IIS (Internet Information Services). Here we will be going thorugh the steps to successfully deploy our website onto IIS.

### Initial Setup
Provided you are using a windows machine, first you'll need to check if IIS is installed on the machine. Hit your windows key and search for windows features, this will pop up a list of windows features. Scroll down to find Internet Information Service and if the checkbox is checked, it means it's already installed and we are ready to go. Otherwise you can click on the checkbox and give OK.

### Overview of IIS
Now that the installation's out of the way, let's open up IIS. Clicking on the *Basic settings* we can get the physical path for our website on our local machine. On clicking the *Explore* option, we can open up the path of our website which will be something like this *inetpub/wwwroot*. It will contain 2 files iisstart.html and iisstart.png, this is for displaying a default page of IIS.
If you want, you can get rid of them.

### Deployment
Copy and paste our index.html file and the other html/css files to this folder *inetpub/wwwroot*. Browsing to localhost on the browser will display the contents of the index.html file. And that's how we deploy a static website to IIS.