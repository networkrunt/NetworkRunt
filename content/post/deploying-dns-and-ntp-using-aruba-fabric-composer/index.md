---
title: Deploying DNS and NTP using Aruba Fabric Composer
subtitle: ""
date: 2021-08-02T13:30:05.249Z
summary: In this article, i will demonstrate how to deploy DNS and NTP services
  to a managed fabric.
draft: true
featured: false
image:
  filename: featured
  focal_point: Smart
  preview_only: false
---
 

It is best practice to configure DNS and NTP as part of your DC deployment. Deploying these services is definitely not a hot topic but an important one. This section will review deploying both services to the fabric. 

Deploying NTP

To deploy the services, we can use the guided setup once again. Select "NTP configuration" from the wizard.

PIC

Enter your NTP server address details.

PIC

 
Scroll down and select "Add" to add the server configuration. Hit next to proceed to the next screen.

PIC

 
I can now choose how to apply the NTP configuration. The configuration can be applied to individual switches or to an entire fabric. I will push the configuration to the entire fabric so all switches use the same config.

PIC

 
A summary of the configuration is now displayed. Once confirmed, you can go ahead and click apply to push the configuration.

PIC

 

You will now return to the configuration screen. The window shows the NTP pool has been configured and applied to the fabric DC1_F1.

Deploying DNS

To proceed with the DNS configuration, I return to the wizard. Select the "DNS configuration" option.

PIC

Specify the domain name and list of DNS servers and proceed to the next screen. 

PIC

I can now apply the config on individual switches or to the entire fabric. I will proceed with the entire fabric.

PIC

A summary of the configuration is shown. Select apply when you are ready.

PIC

 
I am now taken back to the DNS configuration page. You can see in the screenshot DNS has been deployed.

Verification

Before moving onto the next section I would just like to show what's going on under the hood. As part of the deployment, AFC will communicate with the switches using the API and SSH. If we login to a switch, you can see the configuration which has been applied to the device as part of the wizard above.

PIC

The wizard is applying the relevant CLI commands as part of its workflows. This is one thing i like and appreciate about AFC. The fact i can still go into the CLI and perform changes. I still have full CLI access so i can go ahead and run all of the commands i am familiar with. I am not locked out or restricted from the CLI in a AFC deployment.

You can also perform the relevant show commands on the CLI to perform further validation as per the example below.

PIC