
### Azure v.s. AutoPilot

There was always autopilot network at the beginning, like MSIT, backbone. This is where Bing works. Azure is craeted for completing product, face customer.

An effort has been put to merge them

### Cloud

- Public cloud
-  National cloud (need escelate access)
	- Mooncake -China
	- Fairfax - Federal
	- Blackforest - Germany
	- USGov - LX
	- USSec - EX

### Regions

50+ regions, available in 140+ countries (2022)

#### Geo-pairing
Geo-pairing: if people has deployment in two different regions and those regions are Geo-paired then it will not update those two regions at the same time. So we're not shut down his machines at the same time.

see https://learn.microsoft.com/en-us/azure/reliability/cross-region-replication-azure for pairs

### Availability Zone

-  provides High Availability (HA) in case of localized Data Center (DC) or software failures
- Aim to have 3 Availability Zone in each region

### Data Center

Data Center is a collection of Clusters in a Region

### Cluster and Racks

-  Cluster is a collection of Racks (usually 20 racks)
-  Cluster is managed by Fabric Controller (FC)
-  Single Rack has size of 40U
-   Example
	- BN1PrdApp01
	- AM3PrdApp05
![[Cluster_and_Racks.png]]


### Node/Blade
Node/Blade = -   Single Machine in a Rack
We don't run customer VMS natively on a node. But for some infrastructure service like storage or in autopilot, the machine are taking the entire node
![[Inside_a_node.png]]


This is not normal windows server OS in each node. This special version is called reddogOS (previously azure was called reddog). There's no .net or anything like that on the ndoe, so it can run only native code and no garbage collector, which makes it high performace



