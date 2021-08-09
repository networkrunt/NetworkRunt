---
title: "AFC Configuring a VSX LAG "
date: 2021-08-09T11:46:14.013Z
summary: In this blog post, I will show you how to create a VSX LAG using Aruba
  Fabric Composer.
draft: false
featured: false
authors:
  - admin
tags:
  - data_centre
  - afc
  - aruba_networks
  - aruba_fabric_composer
categories:
  - data_centre
image:
  filename: featured
  focal_point: Smart
  preview_only: false
---
Hosts can be connected to the leaf switches in multiple ways. This can include single or dual-homed links using active/active or active/standby NIC deployments. It is common to deploy a VSX LAG. This allows the host to connect to both VSX switches whilst actively forwarding on each link thus providing more bandwidth and resiliency to the connected device.

## Configuring a VSX LAG

To begin the configuration, go to Configuration > Ports > Link Aggregation Groups. Select Add from the Actions menu.

The first thing I need to do is assign the LAG name, description and ID number.

![](screenshot-at-jul-18-23-54-48.png "LAG Parameters")

I define the ports I wish to add to the LAG. Here I will add interface 1/1/5 on Leaf-01 and Leaf-02.

![](screenshot-at-jul-18-23-55-19.png "LAG Port Selection")

I then configure the LACP settings. I am using active mode with a slow interval rate.

![](screenshot-at-jul-18-23-55-39.png "LACP Options")

The VLAN configuration allows me to define which VLANs I want to allow across the link. In this example, I will use VLAN 1 as the native and allow VLAN 20 for data traffic.

![](screenshot-at-jul-18-23-55-58.png "VLAN Assignment")

A summary page is presented with the LAG information. Hit apply to push out the config.

![](screenshot-at-jul-18-23-56-13.png "LAG Summary")

Returning to Configuration > Ports > LAG. I can see LAG-1 has been deployed to the leaf switches.

![](screenshot-at-jul-18-23-56-56.png "LAG Configuration")

Moving over to the CLI, the output confirms the LAG has been deployed.

![](screenshot-at-jul-19-00-02-23.png "LAG Interface")

The VLAN is assigned to the correct interface.

![](screenshot-at-jul-19-00-02-42.png "VLAN Interface Assignment")

The lag is up and functional.

![](screenshot-at-jul-19-00-03-25.png "LAG Status")

I can also see the downstream host from the LLDP information.

![](screenshot-at-jul-19-00-03-43.png "LLDP Neighbour Information")

That concludes the configuring of a VSX LAG interface for this example!

## Summary

During this post, I have covered the following;

* Configuring a VSX LAG.
* Assigning the VLAN and LACP parameters.
* Verifying the configuration.

[Next Article: AFC Intergration with VMware vSphere](/post/afc-intergration-with-vmware-vsphere/)