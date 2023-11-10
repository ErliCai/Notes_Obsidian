
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
2 IncompatibleCacheItemException
3 nullref
7 PopulateDnsPropertiesOnPrivateEndpoint

6 FabricNotPrimaryException
3 FabricNotReadableException
(8-3-3) primary Failover


4 PerformWithRetryAsync

3 ValidatePrivateEndpointCustomNicName
3 ValidatePutPecProxyResponse

others don't have more than 2 occurence