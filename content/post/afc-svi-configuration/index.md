---
title: AFC Distributed Gateway SVI Configuration
date: 2021-08-09T11:05:05.017Z
summary: In this blog post, I will take a look at deploying a distributed
  gateway SVI in a VXLAN network using Aruba Fabric Composer.
draft: false
featured: false
authors:
  - admin
tags:
  - data_centre
  - aruba_networks
  - afc
  - aruba_fabric_composer
categories:
  - data_centre
image:
  filename: featured
  focal_point: Smart
  preview_only: false
---
In this post, I will create a VXLAN distributed gateway SVI using VLAN 20 from the previous article.

To create the SVI, I will move across to the configuration menu. IP configuration is performed in the relevant VRF. To add an SVI go into Configurations > Routing > VRF.

![](screenshot-at-jul-13-17-13-13.png "VRF Configuration Menu")

Select the VRF. In this example, I am working with the default VRF. Select actions > IP interfaces.

![](screenshot-at-jul-13-17-15-15.png "IP Interfaces")

Under the "IP Interfaces" section, choose Actions > Add.

![](screenshot-at-jul-13-17-15-58.png "Add a New Interface")

The first task is to define the SVI and necessary details. Here, I provide the VLAN ID and IP addressing. I also specify which devices I want to configure the SVI on.

![](screenshot-at-jul-13-17-17-32.png "SVI Parameters")

Then I provide the necessary VSX configuration for the VLAN interface. This includes the active gateway IP address and the gateway MAC address.

![](screenshot-at-jul-13-17-18-11.png "SVI VSX Parameters")

A name and description are then applied to the task.

![](screenshot-at-jul-13-17-18-48.png "SVI Name and Description")

And now the final summary page is shown. Hit apply when you are ready to push the config.

![](screenshot-at-jul-13-17-29-46.png "Summary Information")

## Verification

If I go back to the interfaces page, I can see the SVI interfaces in the GUI. In the example below, we can see the SVI for VLAN 20 has been deployed to all four of the leaf switches.

![](screenshot-at-jul-13-17-30-54.png "IP Interface Information")

Moving back across to the CLI on Leaf-01, the SVI has been deployed and is currently up.

![](screenshot-at-jul-13-17-32-45.png "SVI Config")

The VSX config has also been deployed.

![](screenshot-at-jul-13-17-33-05.png "VSX Configuration")

This article was short and sweet but it’s a task that will come up in your AFC environment.

## Summary

During this post, I have covered the following;

* Creating a distributed gateway SVI.
* Deploying the SVI to the devices.
* Configuring the VSX parameters.
* Verification examples.

[Next Article: AFC Configuring a VSX LAG](/post/afc-configuring-a-vsx-lag/)