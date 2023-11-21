


### 11/16

modify UT for code coverage




### Note



RemovePrivateLinkConnectionIdTrackerDebug



RnmClient.cs

Router.cs'

PrivateLinkInventoryManagementClient.cs

RnmChannelProxy.cs

IPrivateLinkInventory.cs in two places

RemovePrivateLinkConnectionIdTrackerDebug

            int availableTrackersCountBeforeOperation = CountValidTrackers(privateLinkServiceName);

            // Removing all trackers for private link service created
            AddRangeToTracker(privateLinkServiceName);

            // Getting count of available trackers for private link service
            int availableTrackersCount = CountValidTrackers(privateLinkServiceName);

            Assert.True(availableTrackersCount == 0, $"Not all trackers removed properly original availble tracker{availableTrackersCountBeforeOperation} now: {availableTrackersCount}");