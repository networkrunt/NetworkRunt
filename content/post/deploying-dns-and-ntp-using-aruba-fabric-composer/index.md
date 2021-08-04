---
title: Deploying DNS and NTP using AFC
subtitle: ""
date: 2021-08-04T06:35:51.807Z
summary: In this article, I will demonstrate how to deploy DNS and NTP services
  to a managed fabric using Aruba Fabric Composer.
draft: false
featured: false
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
<!-- Google Tag Manager -->

<script>(function(w,d,s,l,i){w[l]=w[l]||[];w[l].push({'gtm.start':
new Date().getTime(),event:'gtm.js'});var f=d.getElementsByTagName(s)[0],
j=d.createElement(s),dl=l!='dataLayer'?'&l='+l:'';j.async=true;j.src=
'https://www.googletagmanager.com/gtm.js?id='+i+dl;f.parentNode.insertBefore(j,f);
})(window,document,'script','dataLayer','GTM-NWHJDNP');</script>

<!-- End Google Tag Manager -->

Deploying NTP and DNS services is definitely not a hot topic but it is a useful one. This section will review deploying both services to the managed network using Fabric Composer. 

## Deploying NTP

To deploy the services, we can use the guided setup. Select "NTP configuration" from the wizard.

![](screenshot-2021-07-08-at-11.52.46.png "Launch NTP Wizard")

Enter your NTP server address details.

![](screenshot-2021-07-08-at-11.54.05.png "Enter NTP Details")

Scroll down and select "Add" to add the server configuration. Hit next to proceed.

![](screenshot-at-jul-08-11-54-35.png "Add NTP Details")

I can now choose how to apply the NTP configuration. The configuration can be applied to individual switches or to an entire fabric. I will push the configuration to the entire fabric so all switches use the same config.

![](screenshot-2021-07-08-at-11.55.38.png "NTP Deployment Options")

A summary of the configuration is now displayed. Once confirmed, you can go ahead and click apply to push the configuration.

![](screenshot-2021-07-08-at-11.55.48.png "NTP Summary")

You will now return to the configuration screen. The window shows the NTP pool has been configured and applied to the fabric DC1_F1 as shown below.

![](screenshot-2021-07-08-at-11.56.19.png "NTP Configuration Page")

## Deploying DNS

To proceed with the DNS configuration, I return to the wizard. Select the "DNS configuration" option.

![](screenshot-2021-07-08-at-11.56.31.png "Launch DNS Wizard")

Specify the domain name and list of DNS servers and proceed to the next screen. 

![](screenshot-2021-07-08-at-11.58.11.png "DNS Settings")

I can now apply the config on individual switches or to the entire fabric. I will proceed with the entire fabric.

![](screenshot-2021-07-08-at-11.58.21.png "DNS Deployment Options")

A summary of the configuration is shown. Select Apply when you are ready to continue.

![](screenshot-2021-07-08-at-11.58.39.png "DNS Summary")

I am now redirected to the DNS configuration page which displays my configuration.

![](screenshot-2021-07-08-at-11.58.50.png "DNS Configuration Page")

## Verification

Before moving onto the next section I would just like to show what's going on under the hood. As part of the deployment, AFC will communicate with the switches using the API and SSH. If we log in to a switch, you can view the configuration which has been applied to the device. The wizard is applying CLI commands as part of its workflows. 

![](screenshot-2021-07-08-at-12.21.55.png "CLI Configuration")

This is one of the things I like about AFC -  the fact I can still go into the CLI and perform changes. I am not locked out or restricted from the CLI in an AFC deployment. I have full CLI access so I can go ahead and run all of the commands I am familiar with. 

You can also perform the relevant show commands on the CLI to run further validation as per the example below.

![](screenshot-2021-07-08-at-21.58.42.png "NTP Verification")

![](screenshot-2021-07-08-at-21.59.25.png "DNS Ping Test")

## Summary

* Deployed DNS and NTP using the wizard.
* Reviewed the configuration from the CLI perspective.
* Verified each service is working correctly.