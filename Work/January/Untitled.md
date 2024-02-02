
PLS alias:

PUT https://eastus.network.azure.com:30037/22442a4a-2e6e-4df7-81b1-679a014da20a/133466729836186393/subscriptions/e05dbbce-79c2-45a2-a7ef-f1058856feb3/resourcegroups/testPE-erlicai/providers/Microsoft.Network/privateEndpoints/pe2?api-version=2021-05-01


{"location":"eastus","tags":{},"properties":{"subnet":{"id":"/subscriptions/e05dbbce-79c2-45a2-a7ef-f1058856feb3/resourceGroups/64kPrivateEndpointsPLS/providers/Microsoft.Network/virtualNetworks/TestVnet/subnets/default"},"customNetworkInterfaceName":"pe-nic","manualPrivateLinkServiceConnections":[{"name":"pe2","properties":{"privateLinkServiceId":"pe.ccac7d05-28a1-4a5c-9276-52c1166ce864.eastus.azure.privatelinkservice","groupIds":[],"requestMessage":""}}]}}

PLS uri:

PUT https://eastus.network.azure.com:30022/22442a4a-2e6e-4df7-81b1-679a014da20a/133466688736257674/subscriptions/e05dbbce-79c2-45a2-a7ef-f1058856feb3/resourcegroups/testPE-erlicai/providers/Microsoft.Network/privateEndpoints/pe-erlicai?api-version=2021-05-01

{"location":"eastus","tags":{},"properties":{"subnet":{"id":"/subscriptions/e05dbbce-79c2-45a2-a7ef-f1058856feb3/resourceGroups/testPE-erlicai/providers/Microsoft.Network/virtualNetworks/vnet-pe/subnets/subnet-pe"},"customNetworkInterfaceName":"pe-erlicai-nic","privateLinkServiceConnections":[{"name":"pe-erlicai","properties":{"privateLinkServiceId":"/subscriptions/e05dbbce-79c2-45a2-a7ef-f1058856feb3/resourceGroups/testPE-erlicai/providers/Microsoft.Network/privateLinkServices/pe","groupIds":[]}}]}}