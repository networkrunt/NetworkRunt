---
title: AFC Integration with Aruba NetEdit
date: 2021-08-10T10:57:39.354Z
summary: In this blog post, I will show you how to configure integration between
  Aruba Fabric Composer and Aruba Netedit.
draft: false
featured: false
authors:
  - admin
tags:
  - aruba_networks
  - data_centre
  - afc
  - aruba_fabric_composer
categories:
  - data_centre
image:
  filename: featured
  focal_point: Smart
  preview_only: false
---
Aruba NetEdit provides automation and workflows using a traditional CLI-like environment. For those users who wish to continue to use NetEdit alongside AFC, then you will be glad to know you can easily integrate the two tools. The AFC and Netedit integration allow you to open Netedit directly from AFC. This gives you seamless functionality of both tools in your environment.

In this post, I will quickly run through how to set up the integration between the two.

## NetEdit Integration Configuration

Go into Configuration > Integrations > Aruba NetEdit.

![](screenshot-at-jul-19-21-28-30.png "NetEdit Integration Menu")

Now select Actions > Add.

![](screenshot-at-jul-19-22-24-36.png "Add Integration")

Provide the NetEdit server IP address and login credentials.

![](screenshot-at-jul-19-22-25-31.png "NetEdit Server Details")

Apply the settings to complete the integration.

![](screenshot-at-jul-19-22-25-51.png "Integration Summary")

The NetEdit integration has successfully connected as seen on the integration page.

![](screenshot-at-jul-19-22-26-20.png "NetEdit Integration Status")

At this point, the integration has been successfully completed. Now, I can go into the Visualizations menu to view the network topology. From there, I can right-click on any network device and choose the "Launch Netedit..." options to load Netedit for use. 

![](screenshot-at-jul-19-22-35-43.png "Aruba NetEdit")

This will then allow you access to your NetEdit environment to perform tasks.

## Summary

In this blog post, I have covered the following;

* Configuring AFC and Netedit Integration.
* Verifying the Integration.
* Demonstrating how to access Aruba NetEdit via AFC.