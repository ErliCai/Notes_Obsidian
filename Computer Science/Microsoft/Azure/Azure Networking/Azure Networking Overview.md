
### key capabilities

-  `Connectivity services`
    Connect Azure resources and on-premises resources 
    
	Virtual Network (VNet), Virtual WAN, ExpressRoute, VPN Gateway, Virtual network NAT Gateway, Azure DNS, Peering service, Azure Virtual Network Manager, Route Server, and Azure Bastion.
-  `Application Protection Service`
    Protect your applications
    
    Load Balancer, Private Link, DDoS protection, Firewall, Network Security Groups, Web Application Firewall, and Virtual Network Endpoints.
-  `Application Delivery Service`
    Deliver applications in the Azure network
    
    Content Delivery Network (CDN), Azure Front Door Service, Traffic Manager, Application Gateway, Internet Analyzer, and Load Balancer
-  `Network Monitoring`
    Monitor your network resources
    
    Network Watcher, ExpressRoute Monitor, Azure Monitor, or VNet Terminal Access Point (TAP).

### Connectivity services

provide connectivity between Azure resources, connectivity from an on-premises network to Azure resources, and branch to branch connectivity in Azure

#### Virtual Network

- **Communicate between Azure resources**: [Service that can be deployed in vnet](https://learn.microsoft.com/en-us/azure/virtual-network/virtual-network-for-azure-services)
- **Communicate between each other** : Vnet Peering, Network Manager
- **Communicate to the internet**: All resources in a VNet can communicate outbound to the internet, by default. You can communicate inbound to a resource by assigning a `public IP address `or a `public Load Balancer`.
- **Communicate with on-premises networks** : VPN Gateway/ ExpressRoute

#### Azure Virtual Network Manager


Azure Virtual Network Manager is a management service that enables you to group, configure, deploy, and manage virtual networks globally across subscriptions.

- identify and logically segment your virtual networks
- determine the connectivity and security configurations to all selected vnet in a network group

#### ExpressRoute

- enables you to extend your on-premises networks into the Microsoft cloud over a private connection
- connection is private
- Traffic doesn't go over the internet

#### VPN Gateway

- create encrypted cross-premises connections to your virtual network from on-premises locations
- or create encrypted connections between VNets

Main features: Site-to-site VPN connectivity, Point-to-site VPN connectivity, VNet-to-VNet VPN connectivity

#### Virtual WAN

a networking service that brings many networking, security, and routing functionalities together to provide a single operational interface

#### Azure DNS

provides DNS hosting and resolution

 - `public DNS`: hosting service for DNS domains
     By hosting your domains in Azure, you can manage your DNS records by using the same credentials, APIs, tools, and billing as your other Azure services.
 - `private DNS`: a DNS service for your virtual networks
     Azure Private DNS manages and resolves domain names in the virtual network without the need to configure a custom DNS solution.
 - `DNS Private Resolver`
     enables you to query Azure DNS private zones from an on-premises environment and vice versa
#### Azure Bastion

- a service that you can deploy to let you connect to a virtual machine using your browser and the Azure portal, or via the native SSH or RDP client already installed on your local computer
- a fully platform-managed PaaS service
- secure and seamless RDP/SSH
- When you connect via Azure Bastion, your `virtual machines don't need a public IP address`, agent, or special client software.

#### Virtual network NAT Gateway

- simplifies outbound-only Internet connectivity for virtual networks
- all outbound connectivity uses your specified static public IP addresses.

#### Route Server
- simplifies dynamic routing


### Application protection services

networking services in Azure that help protect your network resources

#### DDoS Protection

- provides countermeasures against the most sophisticated DDoS threats
- provides enhanced DDoS mitigation capabilities

Two tiers:

- `DDoS Network Protection`: combined with application design best practices, provides enhanced DDoS mitigation features to defend against DDoS attacks
- `DDoS IP Protection`:  pay-per-protected IP model. Value-added services: DDoS rapid response support, cost protection, and discounts on WAF.

#### Azure Private Link

- enables you to access Azure PaaS Services and Azure hosted customer-owned/partner services over a private endpoint in your virtual network
- Traffic between your virtual network and the service travels through the Microsoft backbone network
-  Exposing your service to the public internet is no longer necessary

#### Azure Firewall

- a managed, cloud-based network security service
- create, enforce, and log application and network connectivity policies across subscriptions and virtual networks

#### Network security groups

filter network traffic to and from Azure resources in an Azure virtual network

#### Service endpoints

- extend your virtual network private address space and the identity of your VNet to the Azure services, over a direct connection
- secure your critical Azure service resources to only your virtual networks
- Traffic from your VNet to the Azure service always remains on the Microsoft Azure backbone network

### Application delivery services

networking services in Azure that help deliver applications

#### Azure Front Door

- define, manage, and monitor the global routing for your web traffic
- optimizing for best performance and instant global failover for high availability
- transform your global (multi-region) consumer and enterprise applications into robust, high-performance personalized modern applications, APIs, and content that reach a global audience

#### Traffic Manager

- DNS-based traffic load balancer that enables you to distribute traffic optimally to services across global Azure regions
- provides a range of traffic-routing methods to distribute traffic such as priority, weighted, performance, geographic, multi-value, or subnet.
#### Load Balancer

- provides high-performance, low-latency Layer 4 load-balancing for all UDP and TCP protocols
- manages inbound and outbound connections
- define rules to map inbound connections to back-end pool destinations
#### Application Gateway

- web traffic load balancer that enables you to manage traffic to your web applications
- offering various layer 7 load-balancing capabilities

#### Content Delivery Network

offers developers a global solution for rapidly delivering high-bandwidth content to users by caching their content at strategically placed physical nodes across the world.

### Network monitoring services

services in Azure that help monitor your network resources

#### Azure Network Watcher

monitor, diagnose, view metrics, and enable or disable logs

#### Azure Monitor

maximizes the availability and performance of your applications by delivering a comprehensive solution for collecting, analyzing, and acting on telemetry

#### ExpressRoute Monitor

#### Network Insights