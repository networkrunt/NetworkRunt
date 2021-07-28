---
title: An Introduction into Aruba Fabric Composer
subtitle: ""
date: 2021-07-28T13:52:59.793Z
summary: ""
draft: true
featured: false
authors: []
tags:
  - AFC
  - data_centre
categories:
  - data_centre
image:
  filename: featured
  focal_point: Smart
  preview_only: false
---
# Introduction

The blog series is intended to provide an introduction to the Aruba Fabric Composer (AFC). The series will cover a range of topics involving AFC without diving into the fundamentals of the underlying protocols and technologies. Think of them as more of a how-to guide. The articles are mainly for my own learning purposes and consist of my own thoughts and interpretations. Hopefully, it will prove useful to others whilst also providing readers with a taste of how Aruba fabric composer could be used in your own environment.

Anyone who has been involved in the design, implementation or day to day operations of a Data Centre network knows how much of a complex task it can be. Regardless of the deployment size, the amount of effort can be rather substantial, and this may be for only a single site! Times the number of sites by many and you could be in for a whole world of pain.

Many organisations continue to create and implement network changes manually using the CLI. This can become a laborious time consuming task which prolongs project timelines. Factor in how you will perform network changes during your day to day operations and the amount of effort can roll into the weeks or months per change alone. Anything we can do to help mitigate or reduce some of these issues is welcomed.

## What is AFC?

The Aruba fabric composer is a Data Centre orchestration tool which aims to simplify and automate the deployment of network changes, assisting with troubleshooting complex topologies and providing visibility into the network and the connected devices.  With support  for third party integrations, AFC provides a great end-to-end platform to help manage your Aruba network fabric.

From a high level view, the AFC solution is made up of several components as per the following diagram.

 

DIAGRAM here

 

AFC is typically deployed with three nodes for high availability. In the event of a node down situation, the remaining nodes can continue to function and maintain the services of the cluster whilst the node is restored. The cluster is the brains of AFC and allows network operators access to the orchestration interface.

 The network operator can access the cluster using a web page. From there, they can perform network changes and monitor the environment accordingly. AFC with component using API and HTTPS calls.  This allows the cluster to communicate with the managed network fabric in the DC as well as integrating and leveraging third party products in the ecosystem.

 This blog series will focus on AFC version 6.1.