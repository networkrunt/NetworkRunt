---
title: Introduction to Aruba Fabric Composer
subtitle: ""
date: 2021-07-29
summary: A very high level overview of Aruba Fabric Composer.
draft: false
featured: false
authors:
  - admin
tags:
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
<!-- Google Tag Manager -->

<script>(function(w,d,s,l,i){w[l]=w[l]||[];w[l].push({'gtm.start':
new Date().getTime(),event:'gtm.js'});var f=d.getElementsByTagName(s)[0],
j=d.createElement(s),dl=l!='dataLayer'?'&l='+l:'';j.async=true;j.src=
'https://www.googletagmanager.com/gtm.js?id='+i+dl;f.parentNode.insertBefore(j,f);
})(window,document,'script','dataLayer','GTM-NWHJDNP');</script>

<!-- End Google Tag Manager -->

The blog series intends to provide an introduction to the Aruba Fabric Composer (AFC). The series will cover a range of topics in AFC. Think of the posts as more of a how-to guide without deep-diving into the underlying protocols. The articles are for my own learning purposes. I hope they will prove useful to others.

Data Centre architects and engineers know how complex design and implementation can be. Regardless of the deployment size, the amount of effort can be large. And this may be for only a single site! Multiply the number of sites by many and you start to wonder what is the best way to manage it.

Many organisations continue to implement network changes using the CLI. This can become a laborious, time-consuming task that prolongs project and BAU timelines. The amount of effort can roll into weeks or months per change. Anything we can do to help mitigate or reduce some of these issues is welcome. Customers are starting to look towards automation and orchestration tools for help.

## What is AFC?

Aruba Fabric Composer is a data centre orchestration tool that simplifies the deployment of network changes and day-to-day operations. Preconfigured workflows automate complex tasks with minimal input.

From a high-level view, the AFC solution is made up of several components. This includes the AFC cluster, third-party integration packs, and the managed networks.

They say a picture is worth a thousand words so I have included the following solution diagram from Aruba.

![](afc-1-sol-overview.png "AFC Solution Overview")

The cluster is deployed using three nodes for high availability. In the event of a node down situation, the remaining nodes can continue to function. This helps maintain the services of the cluster whilst the node is restored.

The cluster is the management plane and provides access to the orchestration GUI. From the interface, you can perform network changes and monitor the environment.

Changes between AFC, third-party integrations, and the managed fabric(s) are API-driven. The config is pushed to the managed switches without an engineer logging into the device.

AFC supports third-party integration. The integrations provide visibility into workloads and assists with troubleshooting complex topologies. Event-driven workflow automation is also supported. The integration packs provide integration with solutions from vendors such as Aruba, HPE, VMware, Nutanix and StackStorm.

In the next article, I will take a look at the cluster installation.

[Next Article: AFC Cluster Installation](https://www.networkrunt.com/post/afc-cluster-installation/)