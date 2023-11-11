SDN decouples the logic of **managing network topology** from the **logic of routing actual packets** in our datacenters. This decoupling turns a previously decentralized, static, and complex networking architecture into a centralized, flexible, and virtualized architecture.

Here's how our organization's high level architecture document describes it:

_"SDN enables Azure customers to declare and deploy virtual networks in the cloud in real time. This includes ability for customers to declare subnets (from whatever IP address space they desire) for **deploying VMs** (and containers), **link these subnets** via virtual networks, declare **load balancers** to load balance VMs and specify load balancing policies, define routes to chain services, declare network security groups (ACLs), define DNS names etc. These abilities are exposed as network resources and network resource policies in the Azure Resource Management (ARM) model that customers can instantiate and manage."_

### Resources exposed by Azure SDN

1.  Virtual Networks 
2.  NICs
3.  Routes 
4.  Public IPs 
5.  Load Balancers 
6.  Network Security Groups (NSGs)

The SDN stack is made up of many different components, each of which is its own distributed application. Taken together, the SDN stack is an engine which takes a desired customer network topology expressed through ARM resources (e.g. VMs 1, 2, and 3 deployed in VNET A, VM 1 has public IP address xx.xx.xx.xx but does not listen on port 80, VMs 2 and 3 are load balanced behind a second public IP yy.yy.yy.yy) and translates this into the actual programming of switches/routers/FPGAs/NICs in our physical datacenters.

![[Goal State]]


![[RNM in SDN]]


