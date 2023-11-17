[The virtual datacenter: A network perspective](https://learn.microsoft.com/en-us/azure/cloud-adoption-framework/resources/networking-vdc)

### What is virtual datacenter

Cloud solutions were `initially designed to host single,` relatively isolated applications in the public spectrum, which worked well for a few years. As the benefits of cloud solutions became clear, `multiple large-scale workloads` were hosted on the cloud. `Addressing security, reliability, performance, and cost concerns` is vital for the deployment and lifecycle of your cloud service.

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

- Identity and directory service: to ensure that only authorized users and processes access your Azure resource
- Security infrastructure
- Connectivity to the cloud
- Connectivity within the cloud