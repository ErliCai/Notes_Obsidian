[The virtual datacenter: A network perspective](https://learn.microsoft.com/en-us/azure/cloud-adoption-framework/resources/networking-vdc)

### What is virtual datacenter

Cloud solutions were `initially designed to host single, relatively isolated applications` in the public spectrum, which worked well for a few years. As the benefits of cloud solutions became clear, `multiple large-scale workloads` were hosted on the cloud. `Addressing security, reliability, performance, and cost concerns` is vital for the deployment and lifecycle of your cloud service.

Virtual datacenters help achieve the `scale` required for enterprise workloads. The scale must address the challenges introduced when running large-scale applications in the public cloud.

- A virtual datacenter implementation includes more than the application workloads in the cloud. It also provides network, security, management, DNS, and Active Directory services.
- The virtual datacenter concept provides recommendations and high-level designs for implementing a collection of separate but related entities
-  Viewing your workloads as a virtual datacenter helps realize reduced cost from economies of scale.
- `A virtual datacenter isn't a specific Azure service.` Rather, various Azure features and capabilities are combined to meet your requirements

A virtual datacenter helps enterprises deploy workloads and applications in Azure for the following scenarios:

- Host multiple related workloads.
- Migrate workloads from an on-premises environment to Azure.
- Implement shared or centralized security and access requirements across workloads.
- Mix DevOps and centralized IT appropriately for a large enterprise.

### Who should implement a virtual datacenter?

Depending on the size, even single applications can benefit from using the patterns and components used to build a VDC implementation.

- Some organizations have centralized teams or departments for IT, networking, security, or compliance. Implementing a VDC can help enforce policy points, separate responsibilities, and ensure the consistency of underlying common components. Application teams can retain the freedom and control that is suitable for their requirements.
- Organizations with a DevOps approach can also use VDC concepts to provide authorized pockets of Azure resources. This method ensures the DevOps groups have total control within that grouping, at either the subscription level or within resource groups in a common subscription. At the same time, network and security boundaries stay compliant. Compliance is defined by a centralized policy in the hub network and centrally managed resource group.

### pivotal issues

When designing a virtual datacenter, consider these pivotal issues:

- Identity and directory service: 
    to ensure that only authorized users and processes access your Azure resource,  Azure uses several types of credentials for authentication, including account passwords, cryptographic keys, digital signatures, and certificates
- Security infrastructure
    This infrastructure specifies how ingress and egress are controlled in a VDC implementation
- Connectivity to the cloud
    A virtual datacenter requires connectivity to external networks to offer services to customers, partners, or internal users. This need for connectivity refers not only to the Internet, but also to on-premises networks and datacenters
- Connectivity within the cloud

### Topologies

A virtual datacenter can be built using one of these high-level topologies, based on your needs and scale requirements:

#### Flat Topology

all resources are deployed in a single virtual network

![[Flat Topology.png]]

#### Mesh Topology

In a _Mesh topology_, virtual network peering connects all virtual networks directly to each other

![[Mesh Topology.png]]

#### Peering hub and spoke topology

A _Peering hub and spoke topology_ is well suited for distributed applications and teams with delegated responsibilities:

![[Peering hub and spoke topology.png]]

#### Azure Virtual WAN topology

An _Azure Virtual WAN topology_ can support large-scale branch office scenarios and global WAN services
![[Azure Virtual WAN Topology.png]]

#### hub and spoke design

The peering hub and spoke topology and the Azure Virtual WAN topology both use a hub and spoke design, which is optimal for:
- communication, 
- shared resources, 
- and centralized security policy

`the hub` is the central network zone that controls and inspects all traffic between different zones such as the internet, on-premises, and the spokes

The role of each `spoke` can be to host different types of workloads. The spokes also provide a modular approach for repeatable deployments of the same workloads.

The hub often contains common service components consumed by the spokes. The following examples are common central services:
- Windows Active Directory infrastructure
- Distributed Name System
- public key infrastructure
- Flow control of TCP and UDP traffi
- Flow control between the spokes and on-premises

A virtual datacenter reduces overall cost by using the shared hub infrastructure between multiple spokes

### Subscription limits and multiple hubs

A single VDC implementation can scale up a large number of spokes. Although, as with every IT system, there are `platform limits`

The hub deployment is bound to a specific Azure subscription, which has restrictions and limits (for example, a maximum number of virtual network peerings)

In cases where limits might be an issue, the architecture can `scale up further by extending the model from a single hub-spokes to a cluster of hub and spokes.` Multiple hubs in one or more Azure regions can be connected using virtual network peering, ExpressRoute, Virtual WAN, or Site-to-Site VPN

In scenarios requiring multiple hubs, all the hubs should strive to offer the same set of services for operational ease
![[Multi hubs.png]]
### Interconnection between spokes

An architect might want to deploy a multitier workload across multiple virtual networks. 
With virtual network peering, spokes can connect to other spokes in the same hub or different hubs. 

A typical example of this scenario is the case where application processing servers are in one spoke, or virtual network. The database deploys in a different spoke, or virtual network. In this case, it's easy to interconnect the spokes with virtual network peering, which avoids transiting through the hub. 

Complete a careful architecture and `security review` to ensure that bypassing the hub doesn't bypass important security or auditing points that might exist only in the hub.

Spokes can also interconnect to a spoke that acts as a hub. This approach creates a two-level hierarchy. The spoke in the higher level (level 0) becomes the hub of lower spokes (level 1) of the hierarchy.

`Although Azure allows complex topologies, one of the core principles of the VDC concept is repeatability and simplicity. To minimize management effort, the simple hub-spoke design is the VDC reference architecture that we recommend.`

### Components

The virtual datacenter is made up of four basic component types: **Infrastructure**, **Perimeter Networks**, **Workloads**, and **Monitoring**.

![[VDC Componenets.png]]


#### Access Right

As good practice in general, `access rights and privileges can be group-based`. Dealing with groups rather than individual users eases maintenance of access policies, by providing a consistent way to manage it across teams, which aids in minimizing configuration errors. Assigning and removing users to and from appropriate groups helps keep the privileges of a specific user up to date.

Many organizations use a variation of the following groups to provide a major breakdown of roles:
- The central IT team named **Corp** has the ownership rights to control infrastructure components
- The dev/test group named **AppDevOps** has the responsibility to deploy app or service workloads
- The operation and maintenance group called **CorpInfraOps** or **AppInfraOps** has the responsibility of managing workloads in production

The VDC is designed so that central IT team groups that manage the hub have corresponding groups at the workload level. In addition to managing hub resources, the central IT team can control external access and top-level permissions on the subscriptions

The virtual datacenter is partitioned to securely host multiple projects across different lines of business. All projects require different isolated environments (dev, UAT, and production). Separate Azure subscriptions for each of these environments can provide natural isolation

Typically in IT, an environment (or tier) is a system in which multiple applications are deployed and executed. Large enterprises use a development environment (where changes are made and tested) and a production environment (what end-users use). Those environments are separated, often with several staging environments in between them, to allow phased deployment (rollout), testing, and rollback if problems arise.