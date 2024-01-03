[Incident-428737782 Details - IcM (microsofticm.com)](https://portal.microsofticm.com/imp/v3/incidents/details/428737782/home)

Resource Group Deletion not happenning in correct order

ARM will use "managed by" property to determine the order of deletion

It's only supported in 2023 API version



### Can we resolve this?

customer is already mitigated?

EEE reactivate this saying still active

I think this will only be resolved after we switch to new API version

### Which team is responsible to fix this

Portal/Bicep team to switch to newer version of API

Is API version backwards compatible? Any concern to switch to newer api version


### What to do for resource created before 2023

Backfilling? Or at least a tsg helping with deletion


1. check with protal
2. check with pranshu about backfill

# **ping packets from local could pass FW , but TCP traffic from local to PE bypass FW**

[Incident-452952646 Details - IcM (microsofticm.com)](https://portal.microsofticm.com/imp/v3/incidents/details/452952646/home)

They want to enable network policy to use UDR

Are they able to enable PE network policies for Mooncake


### since pl nsg is not allowed

is udr not supported in MoonCake

### What happens when they try to enable network policy

Cx hit error PrivateEndpointNetworkPoliciesCannotBeEnabledOnPrivateEndpointSubnet when enabling PE network policies
IsPrivateEndpointNSGAllowed is false on the subs and
it pl nsg is not supported in the region


q: Why can ICMP traffic reach the firewall while TCP traffic might not