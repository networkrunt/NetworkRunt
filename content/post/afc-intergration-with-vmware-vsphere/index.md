---
title: AFC Intergration with VMware vSphere
date: 2021-08-09T12:38:12.373Z
summary: In this blog post, I will review the integration configuration between
  AFC and vSphere.
draft: false
featured: false
authors:
  - admin
tags:
  - afc
  - aruba_networks
  - aruba_fabric_composer
  - data_centre
categories:
  - data_centre
image:
  filename: featured
  focal_point: Smart
  preview_only: false
---
As I touched on earlier, AFC includes support for several third-party integrations. This includes products from HPE/Aruba, Vmware, Nutanix and Pensando.

You may be thinking how could this be useful to me in my environment? Think about the complexity of troubleshooting network issues, the number of moving parts and how difficult it can be to verify the configuration, generating visualisations of the network or simply automating changes as your environment grows. These are the kind of things that can be achieved by using integrations.

Let's take an example. Say you wish to move VMs in your environment to several new hosts. Many organisations will need cross-collaboration between the server and network teams to ensure this can be implemented. This could take days, weeks or maybe more effort. By utilising the vSphere integration, AFC can detect virtualisation events to assist with the migration. By detecting the vMotion event, AFC can query the switches in the fabric to ensure they have the necessary VLAN configuration available to support the move and operations on the new hosts. If the VLANs do not exist then AFC can apply the configuration and part of the virtual machine integration.

## vSphere Integration Setup

To access the available integrations you can go to Configuration > Integrations.

![](screenshot-at-jul-19-21-28-30.png "Integration Packs")

As part of this example, I will now add a Vmware vSphere integration into AFC by selecting the vSphere integration option.

Now choose Actions > Add.

![](screenshot-at-jul-19-21-29-01.png "Adding a New Integration")

Provide details of the integration name, host IP and credentials. Before proceeding you can validate the connection. This performs a query to vSphere to ensure they can communicate.

![](screenshot-at-jul-19-21-31-59.png "VMware Details")

![](screenshot-at-jul-19-21-32-22.png "VMware Validation")

I define which VLANs can be provisioned in the environment to the directly connected hosts.

![](screenshot-at-jul-19-21-36-36.png "VLAN Assignment")

Enable discovery protocols using LLDP.

![](screenshot-at-jul-19-21-37-50.png "Enable LLDP")

Now complete the integration setup.

![](screenshot-at-jul-19-21-38-07.png "VMware Integration Summary")

The AFC cluster has successful connectivity with the vSphere environment.

![](screenshot-at-jul-19-21-38-39.png "Integration Success")

Compute hosts are added into AFC after the integration is complete. The example below shows a single ESXi host in my environment. You can see AFC is able to detect the full end-to-end path between the VM and the CX switches. The devices in the chain include lots of useful information regarding the configuration of each component. You can access this information by selecting the component in the visualisation. This can prove very helpful when trying to visualise the traffic path or assisting with various troubleshooting issues.

![](screenshot-at-jul-19-21-40-27.png "Host Visualisation")

Each element can be selected to show useful information for that particular component.

![](screenshot-at-jul-19-21-40-48.png "Interface Information")

![](screenshot-at-jul-19-21-53-35.png "VM Information")

The next part is completely optional. However, some people may wish to install AFC as a plugin on the vSphere console. To do so I will go back to the VMware integration page. Then go to Actions > Register plugin.

![](screenshot-at-jul-19-22-02-30.png "Register Plugin")

AFC already has the necessary Vmware credentials to communicate with vSphere. Now open your vSphere environment. When I log in, I can see a plugin notification.

![](screenshot-at-jul-19-22-06-10.png "Plugin Notification")

The AFC plugin is listed in vSphere.

![](screenshot-at-jul-19-22-06-54.png "VMware Plugin List")

I will need to configure the AFC credentials and certificate to complete the plugin installation. This must be completed in the vSphere console.

Under Administration, go to settings > authentication > update settings.

![](screenshot-at-jul-19-22-09-05.png "Authentication Page")

Enter the AFC credentials.

![](screenshot-at-jul-19-22-10-25.png "Credentials")

Under the AFC plugin, go to settings > certificates. Specify the AFC IP address to add the certificate.

![](screenshot-at-jul-19-22-11-29.png "Certificate Information")

Add the certificate.

![](screenshot-at-jul-19-22-11-56.png "Adding the Certificate")

The certificate has been added successfully.

![](screenshot-at-jul-19-22-55-29.png "Certificate Success!")

The connection has been successfully authenticated as shown below.

![](screenshot-at-jul-19-22-55-55.png "Authenticated")

The AFC console is now available for use within vSphere.

![](screenshot-at-jul-19-22-56-34.png "VMware / AFC Integration")

That concludes the setup between AFC and vSphere.

## Summary

During this post, I have covered the following;

* Configuring integration between AFC and vSphere.
* Installing the AFC plugin in the vSphere console.
* Verifying the configuration.

[Next Article: AFC Integration with Aruba NetEdit](/post/afc-integration-with-aruba-netedit/)