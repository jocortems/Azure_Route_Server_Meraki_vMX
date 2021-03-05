# Azure Route Server and Cisco Meraki vMX Deployment Guide (Preview not production ready)

Authors: Simarbir Singh, Mitchell Gulledge

# Solution Overview

This document encompasses a detailed step by step guide on deploying the Azure Route Server (Currently in Preview) and Cisco Meraki vMXs hosted in the Azure cloud. BGP is utilized to provide resiliency, symmetry and load sharing across vMXs in the Azure cloud.

# Solution Architecture
![Test Image 1](RouteServerTopology.png)

In the above diagram, the branch MX connects to a pair of vMXs deployed in the same VNET across different Availability Zones for redundancy. EBGP has been configured across the vMXs to the route server virtualRouterIps that will be discussed further later. IBGP is formed on top of Auto VPN directly from the Branch to the respective vMXs in the Azure cloud. AS Path manipulation is used to ensure symmetry for the route to Azure and the route back from Azure, this is done in accordance with the concentrator priority that is configured at the branch MX site to site vpn settings. 

# Step 1) Deploy Cisco Meraki Network Virtual Appliances (vMXs) from Azure Marketplace

The steps for deploying virtual MXs from the Azure marketplace are out of scope for this document. For more information on deploying virtual MXs from the Azure marketplace please reference the following link:
https://documentation.meraki.com/MX/MX_Installation_Guides/vMX_Setup_Guide_for_Microsoft_Azure

