
![[RNM_in_SDN.png]]

RNM's place in the SDN stack; note that **NRP (Network Resource Provider)** and RNM are both region-level components (as are CRP and SRP). RDFE (not pictured above) is a global-level component.

**PubSub** is a newer Networking component which is deployed at the **Availability Zone (AZ)** level. PubSub, as the name suggests, is a service which delivers goal state via a publisher-subscriber pattern, and is our preferred method for delivering control plane information across SDN components.

**AzSM** is an Azure Compute component with which we interact regularly for **Vip Spanning** scenarios, and similar to PubSub, is deployed on a per-AZ basis.

**Network Service Manager (NSM)** is deployed once for each cluster in our Datacenters, and is responsible for network programming on individual nodes in response to goal state sent from RNM.