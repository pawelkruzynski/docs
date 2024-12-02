---
title: NSX - FAQ (EN)
excerpt: "Find frequently asked questions about the most common scenarios concerning the use of NSX within the Hosted Private Cloud ecosystem"
updated: 2024-12-02
---

## Objective

**Find below frequently asked questions and answers to your NSX usage**.

## Frequently asked questions - FAQ

> [!faq]
> What are the differences between support packs? <a name="diffencepack"></a> 
> > All packs are based on a day/hour count, e.g.: 1 day = 8 hours, 2 days = 16 hours (sometimes more).
> > The first approach is the same for all packs with a discovery phase, but the duration of the pack will depend on the complexity of the environment and the maturity of your current managed offer.
> > This issue will be explored with the [Professional Services](/links/professional-services) team in a first evaluation call.
> >
> How can I protect my virtual machines directly exposed on the internet with a Public IP? <a name="public ip"></a>
> > Secure your traffic with the NSX Distributed Firewall (North/South or East/West security), or use one of the Gateway Firewalls (North/South security).
> >
> What is the end-of-life date for NSX-v? <a name="eofnsxv"></a>
> > VMware has decided to initiate the end of life (EOL) of NSX-v since January 2022. OVHcloud has been granted an extension of support until 15 January 2025.
> >
> Is it possible to do Border Gateway Protocol (BGP)? <a name="bgp"></a>
> > It is impossible to do public BGP (peer with OVHcloud internet routers).
> > However, it is possible to do BGP (private) with a vRack via a Tier-0 gateway or a VRF level 0 gateway, or in an IPsec tunnel via a Tier-0 only.
> >
> Is NSX-T BGP compatible across IPSEC? <a name="bgpoveripsec"></a>
> > Yes, through a VRF.
> >
> What is the change regarding the BGP autonomous system (AS)?
> > It is possible to position different private AS numbers according to Tier-0 gateways or VRF level 0 gateways.
> >
> Can we put a virtual firewall in front of the Tier-0 in the same managed vSphere?
> > You can completely disconnect the public interfaces of the T0 and interconnect them via a private network or a security appliance exposed live on the internet. Note that there is an integrated firewall in T0 that can be configured via the NSX interface, Gateway Firewall.
> >
> What is the difference between a Tier-0 gateway and a Tier-1? <a name="t0vst1"></a>
> > In VMware design, a Tier-1 is always attached to a Tier-0.
> > Flows pass through a Tier-0 to go to the external network.
> > All elements that need to remain inside (locally) the managed Vsphere platform are routed by the Tier-1.
> >
> How can I add another Tier-0 Gateway? <a name="addt0gw"></a>
> > It is currently not possible to add a new Tier-0 Gateway.
> > Depending on your needs, you can create a virtual Tier-0 instance called VRF. This VRF will not be able to be connected on the internet.
> >
> The "Edit" button in NSX for a Tier-0 is disabled, how can I configure the public Gateway? <a name="publicgateway"></a>
> > This is not possible by default. The Tier-0 Gateways are each hosted on a different host, HA (High Availability) is activated and a virtual IP (VIP) is configured between the 2 EDGES to maintain service continuity. The HA section is already preconfigured by OVHcloud.
> >
> Can I configure an active-active Tier-0 Gateway to have double bandwidth ("guaranteed" 10+10=20Gb/s and "theoretical" 25+25=50Gb/s)?
> > No, this is not possible by default. The configuration is managed by OVHcloud and is active/passive with a VIP (10 Gbps guaranteed bandwidth).
> >
> Is it possible to connect to the Edge via SSH to perform diagnostics or packet capture? <a name="t0gwdoublebw"></a>
> > No, this is not possible, either for Tier-0 or Tier-1 information. There are troubleshooting tools in NSX.
> >
> What is the maximum number of interfaces (connected segments) on a Tier-1 Gateway? <a name="t1interface capacity"></a>
> > This information depends on the version of NSX in production on the infrastructure. The maximum values are on the dedicated Broadcom website: <https://configmax.broadcom.com/home>.
> >
> How can I add public IPs? <a name="addpublicicip"></a>
> > Additional public IPs can be added via "next hop" routing by specifying the VMware Hosted Private Cloud environment as a resource, and in `next hop` the public virtual IP (VIP) of the Tier-0 (T0).
> >
> Can IP address blocks be used/distributed between two VMware datacentres in the same Hosted Private Cloud? <a name="ipblockdistribution"></a>
> > IP address blocks are dependent on the VMware Hosted Private Cloud environment and not on the virtual datacentre. It is therefore possible to use the same IP address block between several virtual datacentres (without any modification).
> > Warning: if you have several virtual datacentres, a block of public IPs routed on the virtual IP (VIP) of your Tier-0 (T0) cannot be used in a `VM Network` of another virtual datacentre. It is attached to the VIP and no longer to the VM Network.
> >
> How are IPs managed during the migration? <a name="managemigrationip"></a>
> > In the [migration guide](/pages/hosted_private_cloud/hosted_private_cloud_powered_by_vmware/service-migration-vdc), you can find out how to move your existing IP from your NSX-v platform, and route it to the IP attached to the Tier-0 section (T0).
> > When an NSX-T Virtual Datacentre is delivered, we deploy and configure a new IP block for NSX Tier-0 (T0) that we dedicate to VIP. You can route the IP block to this VIP.
> >
> For vDC migration, you need to upgrade your datastore to a global version. Can I go back on this configuration? <a name="vdcmigration"></a>
> > The global datastore is managed via the OVHcloud Control Panel or API.
> > This allows you to globalize your datastore, which will be visible from your new vDC. It allows you to make a vMotion "Compute" and not a vMotion "Storage" of the virtual machines.
> > It is not possible to exit this mode. You will need to order a new datastore and apply a vMotion to globally release it.
> >
> Will you provide training and documentation to improve NSX-T skills? <a name="docandtrainingnsxt"></a>
> >
> > - [Getting started with NSX](/pages/hosted_private_cloud/hosted_private_cloud_powered_by_vmware/nsx-01-first-steps)
> > - [VMware on OVHcloud](/products/hosted-private-cloud-hosted-private-cloud-powered-by-vmware)
> >
> If an NSX-v migration has been planned to a third-party pfSense solution, should we restart with a request to create a new virtual Datacentre without NSX-v? Can this be done on the existing virtual datacentre? <a name="nsxtmigrationpfsense"></a>
> > In this case, you do not need to order a new vDC, but make sure to disable all your NSX-v features so that OVHcloud can disable the component.
> >
>
> Can IP migration be done IP by IP or by IP block? <a name="ipmigrationperblock"></a>
> > IP migration is done by block, you change the *next stop* of the IP block, the global block is transitioned to the NSX part.
> >
> Does this migration interrupt the services supported by NSX? If so, how long? <a name="ipmigrationinterruption"></a>
> > This will depend on the services you use. For example, if you use IPSEC tunnels and public IPs, you will need to move your workloads and reconfigure the IP block you had on your NSX-v infrastructure to your NSX-T infrastructure.
> > If you use NSX-v for firewalling, you can have the configuration on the 2 environments.
> > Downtime depends on the complexity of your environment.
> >
> How much bandwidth will the edge-node cards have, knowing that the Tier-0 (T0) will be shared? <a name="bandwidthedgenode"></a>
> > This will depend on which services are enabled (LoadBalancer/NAT/Firewall, etc.). The speed and maximum are dependent on the NSX version and available on the Broadcom website.
> >
> Does the vRack work with NSX-T?  <a name="vrackwithnsxt"></a>
> > Yes, the vRack works with NSX-T.
> > You can access it in the same way from vlan portgroups in vSphere or from VLAN segments in NSX-T.
> >
> Will the NSX Edge cluster have access to the OVHcloud vRack? <a name="vrackaccess"></a>
> > The NSX Edge cluster is compatible with an OVHcloud vRack. You can add your Virtual Datacentre that carries NSX-T in the vRack of your choice. Find more information on [this page](/pages/hosted_private_cloud/hosted_private_cloud_powered_by_vmware/vrack_and_hosted_private_cloud).
> >
> Can I configure high availability on the NSX Edge? <a name="ha"></a>
> > No, NSX Edge management is carried out by OVHcloud in Active Passive mode.
> >
> Is it possible to have multiple edge clusters? <a name="multipleedgeclusters"></a>
> > Today, only 1 Edge NSX-T cluster is deployed.
> >
> Currently, we have 300 edges and around 5000 simultaneous RDPs. Will the average configuration "4 vcpu / 8 GB RAM / 200 GB" hold for flows? <a name="averageconfiguration"></a>
> > Sizing will depend on the services you enable or consume on your edges (firewall or load balancing...).
> > Today, the Edge servers are Medium in size. The maximums and sizing are available on the Broadcom website.
> >
> I have just created a cluster and I would like to configure it for NSX in API. How do I do this?
> > Use this route after you have retrieved the cluster ID you have just created.
> >
> > > [!api]
> > >
> > > @api {v1} /dedicatedCloud POST /dedicatedCloud/{serviceName}/datacenter/{datacenterId}/cluster/{clusterId}/nsxt
> >
> Can I use the OVHcloud API to configure and use my NSX Edge API? <a name="api"></a>
> > Yes, it is possible to do this. Here is an example of the API calls that you can use within the **/dedicatedcloud** universe:
> > Retrieve the Edge ID:
> >
> > > [!api]
> > >
> > > @api {v1} /dedicatedCloud GET /dedicatedCloud/{serviceName}/datacenter/{datacenterId}/nsxtEdge/{nsxtEdgeId}
> > >
> >
> > For example, you can test resilience by simulating the failure of one of the cluster’s Edge nodes:
> >
> > > [!api]
> > >
> > > @api {v1} /dedicatedCloud POST /dedicatedCloud/{serviceName}/datacenter/{datacenterId}/nsxtEdge/{nsxtEdgeId}/resilience/enable
> > >
> >
> What do I do with my Veeam backup and Zerto replication options? Are they still compatible with NSX? <a name="veeamzerto"></a>
> > Yes, but you will need to reconfigure them after migrating your virtual Datacentre.
> >
> Is it possible to have NSX-v and NSX-T cohabit during the transition phase? <a name="nsxtwithnsxv"></a>
> > It is possible to get NSX-T if you order a new virtual Datacentre in your Hosted Private Cloud. Within the same infrastructure, you will have 2 virtual datacentres, one with NSX-v and the other with NSX-T.
> > Please note that ordering the new vDC will automatically trigger the refund mechanism for the coming month.
> >
> Can we use "migration coordinator" for migration between NSX-v and NSX-T? <a name="nsxmigrationcoordinator"></a>
> > This tool requires very strong administrative rights on the environment, the Professional Services team can validate the execution and the duplication. In this tool, it is important to note that many elements are not supported (options, existing rules in NSX-v).
> > The reproduction phase would require a lot of adaptations on your part, so it is not a recommended tool for migration at OVHcloud.
> >
> Why is the NSX management interface created via a separate `https://nsxt.pcc-xxx-xxx-xxx-xxx.ovh.com` endpoint? <a name="nsxterraform"></a>
> > The NSX interface is independent and not linked to the vSphere interface. This is why we have created a dedicated endpoint to reach it.
> >
> Is it possible to connect an NSX Edge router between 2 Hosted Private Cloud environments? <a name="nsxedge"></a>
> > Yes, it is possible, via the vRack for example, or via the public network and the Edge Cluster VIPs.
> >
> Do you carry out backups of the NSX-T configurations, including manual customer configuration? <a name="nsxbackupmanualconfiguration"></a>
> > Yes, OVHcloud performs backups.
> > This backup is not intended for restoration in the event of incorrect operation, but for support in the event of an incident involving the various NSX-T controllers.
> >
> Is it possible to have the delivery of a vDC NSX-T in a managed VMware vSphere managed from 2016? Will there be problems during the delivery? <a name="nsxtinto2016pcc"></a>
> > Yes, it is possible, there are no constraints currently.
> >
> Are there any additional limitations in a SecNumCloud context? <a name="sncliitations"></a>
> > There are no additional limitations compared to an unqualified SecNumCloud environment.
> >
> Is backup management different on a SecNumCloud qualified solution? <a name="semnumcloudbackupoutside"></a>
> > There is no difference between backups in SecNumCloud and non-SecNumCloud qualified environments.
> >
> During the migration phase, will we have to pay double for our platform for one month? <a name="priceduringmigration"></a>
> > OVHcloud will refund you 1 month for the virtual datacentre added to your next bill after the order (1 month = 30 days).
> >
> Can we use the Advanced Load Balancer (AVI) or the IDS/IPS Gateway? <a name="pricealbandipsids"></a>
> > No, these features are not included.
> >
> Can we use distributed IDS/IPS? <a name="pricealbandipsids"></a>
> > yes.

## Go further

[Getting started with NSX](/pages/hosted_private_cloud/hosted_private_cloud_powered_by_vmware/nsx-01-first-steps).

If you require training or technical support to implement our solutions, please contact your sales representative or click [this link](/links/professional-services) to get a quote and request a custom analysis of your project from our Professional Services team experts.

Join our [community of users](/links/community).
