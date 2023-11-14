
### Add debug API to update range

- sorted list since original data struct is sorted
- add test coverage for catching exception
- remove unexecuted lines in test for coverage 

### host pls on iplb sync 

### help review code

#### resolve Update RnmUploadGoalSetting failure

rnm ignored setting need to be in format:
```
        <Setting Name="name">
          <Region Name="region"/>
        </Setting>
```

### bucketization
86 total incidents

33 about first party
[Incident-415965881 Details - IcM (microsofticm.com)](https://portal.microsofticm.com/imp/v3/incidents/details/415965881/home)

7 PopulateDnsPropertiesOnPrivateEndpoint
[Incident-415966113 Details - IcM (microsofticm.com)](https://portal.microsofticm.com/imp/v3/incidents/details/415966113/home)

primary Failover
6 FabricNotPrimaryException
3 FabricNotReadableException
[Incident-423437563 Details - IcM (microsofticm.com)](https://portal.microsofticm.com/imp/v3/incidents/details/423437563/home)

4 PerformWithRetryAsync
[Incident-428018792 Details - IcM (microsofticm.com)](https://portal.microsofticm.com/imp/v3/incidents/details/428018792/home)

3 ValidatePrivateEndpointCustomNicName
[Incident-415966124 Details - IcM (microsofticm.com)](https://portal.microsofticm.com/imp/v3/incidents/details/415966124/home)
3 ValidatePutPecProxyResponse
[Incident-395366079 Details - IcM (microsofticm.com)](https://portal.microsofticm.com/imp/v3/incidents/details/395366079/home)

3 nullref
[Incident-415965926 Details - IcM (microsofticm.com)](https://portal.microsofticm.com/imp/v3/incidents/details/415965926/home)

3 PutPrivateEndpointConnectionProxyToRemoteHiddenPrivateLinkServiceAsync
[Incident-415966278 Details - IcM (microsofticm.com)](https://portal.microsofticm.com/imp/v3/incidents/details/415966278/home)


2 IncompatibleCacheItemException
[Incident-415966241 Details - IcM (microsofticm.com)](https://portal.microsofticm.com/imp/v3/incidents/details/415966241/home)

2 ArgumentException@AddOrUpdateNewIpConfigurationFromStaticIpConfigs|
[Incident-441479395 Details - IcM (microsofticm.com)](https://portal.microsofticm.com/imp/v3/incidents/details/441479395/home)

2 ReachedRegionalNetworkManagerThroughputLimit
[Incident-423437547 Details - IcM (microsofticm.com)](https://portal.microsofticm.com/imp/v3/incidents/details/423437547/home)

others don't have more than 1 occurence