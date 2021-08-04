---
title: AFC GUI Overview
date: 2021-08-01T12:28:46.926Z
summary: In this blog post, I will review the layout of the GUI. The aim is to
  allow new users to become familiar with the interface structure.
draft: false
featured: false
authors:
  - admin
tags:
  - afc
  - aruba_fabric_composer
  - aruba_networks
  - data_centre
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

I would like to pause here to review the GUI. To be honest, the GUI is quite straight forward but I thought it would be useful to review the layout for new users.

By default, the AFC dashboard will be displayed when you log in. The dashboard is the home page and provides you with a high-level overview of the system.

At the top of the page, we have the menu bar. The menu provides access to the dashboard, configuration, network visualisations and the guided setup as shown below in red. Initially, the GUI will not contain much information. Information is populated once we begin onboarding switches.

![](screenshot-at-jul-06-22-39-55.png "AFC Menu Bar")

In the middle of the screen, you are presented with several tiles. The aim of the tiles is to display useful information such as device status, fabric information, syslog events, device info, and integration information. The tiles can be customised to your preference. This area of the page will change as you work your way through the menu items. It will be your main work area in AFC.

![](screenshot-at-jul-06-22-41-00.png "AFC Main Workspace")

To the right of the page, you have the guided setup. The guided setup provides simplified workflows for common tasks in the fabric. Click the item in the setup to launch a workflow task.

![](screenshot-at-jul-06-22-42-32.png "AFC Guided Setup")

As a side note, you can hide the guided setup at any time by selecting the button shown below.

![](screenshot-at-jul-06-22-56-21.png "AFC Guided Setup Button")

As we progress through the series, we will begin to see more of the AFC interface and its components.

Now let's begin onboarding some devices onto the cluster.

[Next Article: AFC Fabric Initialisation](/post/afc-fabric-initialisation/)