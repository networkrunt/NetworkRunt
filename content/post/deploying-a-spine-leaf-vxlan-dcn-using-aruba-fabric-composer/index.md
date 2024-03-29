---
title: Deploying a Spine Leaf VXLAN DCN using AFC
date: 2021-08-09T10:25:11.464Z
summary: In this blog post, I will show you how to deploy a VXLAN network using
  Aruba Fabric Composers integrated workflows.
draft: false
featured: false
authors:
  - admin
tags:
  - afc
  - aruba_fabric_composer
  - data_centre
  - aruba_networks
categories:
  - data_centre
image:
  filename: featured
  focal_point: Smart
  preview_only: false
---
In this article, I will use AFC to deploy a spine leaf topology using VXLAN. For reference, the following topology will be used throughout this example.

![](spine-leaf-base-diagram.jpg)

The network is comprised of two spine switches and four leaf switches. Each pair of leaf switches has been deployed using VSX as shown in the previous article. Now I will use AFC to deploy VXLAN. 

Normally this would take a massive amount of effort. It can require a considerable amount of hours to generate the necessary config and perform the validation. Using AFC, you can have a complex topology deployed very quickly. Let's look at an example.

## Underlay Configuration

The first step is to implement the underlay configuration. To begin, select the Spine Leaf option from the wizard. From there, you can choose to automatically detect the devices or you can manually specify them. I will select automatic detection and proceed.

![](screenshot-at-jul-12-22-17-43.png "Creating Leaf-Spine Pairs")

Provide a relevant name and description for the task.

![](screenshot-at-jul-12-22-18-24.png "Job Task Information")

I will provide a subnet range for the underlay. The IP addresses will be assigned to the uplink interfaces between the spine and leaf switches.

![](screenshot-at-jul-12-22-20-09.png "Underlay IP Information")

Review the summary and hit apply to configure the uplink interfaces.

![](screenshot-at-jul-18-16-13-04.png "Underlay IP Address Summary")

Now go back to the wizard and select the underlays option.

![](screenshot-at-jul-12-22-33-54.png "Configure Underlay Using the Wizard")

Provide a name and description then move onto the next phase.

![](screenshot-at-jul-18-16-14-21.png "Underlay Task Information")

I will choose which routing protocol I wish to use for the underlay. eBGP is often considered for larger deployments where multi ASNs are required between the leaf and spine switches. For this example, I will choose OSPF for simplicity. 

![](screenshot-at-jul-18-16-14-42.png "Underlay Routing Options")

I will keep the default OSPF timers but I will enable BFD to help detect a failure. An authentication key will be used and I have assigned VLAN 10 for the transit VLAN.

![](screenshot-at-jul-18-16-16-17.png "OSPF Options")

![](screenshot-at-jul-18-16-16-44.png "OSPF Options Continued")

Next, I will use the default advertisement options.

![](screenshot-at-jul-18-16-17-09.png "LSA Options")

Review the configuration one last time to ensure everything is correct and hit apply to deploy the config.

![](screenshot-at-jul-18-16-17-44.png "OSPF Summary")

If we take a look at some of the devices, I can see the OSPF config has been applied.

![](screenshot-at-jul-18-16-20-37.png "OSPF Configuration")

OSPF adjacencies have been formed between the switches. Everything is looking good so far. 

![](screenshot-at-jul-18-16-21-06.png "OSPF Adjacencies")

Now lets move into the overlay configuration section.

## Overlay Configuration

Select the overlay option from the wizard to begin the overlay deployment. Next, give the task a name and description.

![](screenshot-at-jul-18-16-22-13.png "Job Details")

I now have the option to choose iBGP or eBGP for the overlay. In this example I will use iBGP.

![](screenshot-at-jul-18-16-22-32.png "BGP Options")

To support the iBGP deployment, I specify the ASN and configure both spine switches as route reflectors. I then create BGP groups for the leaf and spines. An authentication password is applied.

![](screenshot-at-jul-18-16-23-16.png "BGP Parameters")

An IP subnet is required for the overlay loopbacks.  I will use the subnet 10.1.3.0/24 for the interfaces.

![](screenshot-at-jul-18-16-23-43.png "Loopback Subnet Information")

I then keep the default timers and hit next.

![](screenshot-at-jul-18-16-23-59.png "BGP Timers")

Review the configuration and then deploy the config using the apply button.

![](screenshot-at-jul-18-16-24-19.png "Overlay Summary")

If you go into Configuration > Routing > VRF > Default, you can see the overlay has been deployed in the GUI.

![](screenshot-at-jul-18-16-26-45.png "Overlay Verification.")

Moving back over to the CLI, the BGP config has been deployed to each device.

![](screenshot-at-jul-18-16-27-07.png "BGP Configuration")

BGP adjacencies have been established.

![](screenshot-at-jul-18-16-27-32.png "BGP Adjacencies")

Lets proceed with the EVPN config.

## EVPN Configuration

I will deploy a single VLAN using EVPN. Choose the EVPN option from the wizard.

![](screenshot-at-jul-18-16-28-09.png "EVPN Wizard")

I will now deploy the EVPN configuration to all switches in the fabric.

![](screenshot-at-jul-18-16-28-30.png "Deployment Options")

Provide a name and description for the task.

![](screenshot-at-jul-18-16-29-08.png)

At this point, you can deploy a range of VLANs using EVPN. As mentioned, I will be deploying a single VLAN for this scenario. I will use VLAN 20 with a base L2VNI of 10000. 

![](screenshot-at-jul-18-16-29-44.png "VNI Mapping")

Specify the route target and system MAC address.

![](screenshot-at-jul-18-16-30-21.png "RT and System Mac Options")

Finally, verify your EVPN configuration before deploying the config.

![](screenshot-at-jul-18-16-30-41.png "EVPN Summary")

To verify the EVPN config, go to Configuration > Routing > EVPN as below.

![](screenshot-at-jul-18-16-32-02.png)

The EVPN configuration is also available using the CLI.

![](screenshot-at-jul-18-16-36-08.png "CLI Verification")

That's it for now! You can use this as a base and then start building out additional configurations for your environment.

## Summary

During this post, I have covered the following;

* Deploying the underlay using OSPF.
* Deploying the overlay using iBGP.
* Configuring EVPN and VNI mapping information.
* Verifying each stage of the deployment.

[Next Article: AFC Distributed Gateway SVI Configuration](/post/afc-svi-configuration/)