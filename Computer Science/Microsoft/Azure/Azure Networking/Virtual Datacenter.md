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

