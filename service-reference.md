# Service Reference

## Project System

|Name                                                                 |Type     |Description                                                             |
|---------------------------------------------------------------------|---------|------------------------------------------------------------------------|
|[`IBuildManagerHost`](building.md#build-manager-hosts)               |Extension|Defines a build manager (can also implement `IBatchingBuildManagerHost`)|
|[`IBuildManagerHostBatchingService`](building.md#build-manager-hosts)|Service  |Allows batching builds                                                  |
|[`IFileTimestampCache`](building.md#up-to-date-checking)             |Service  |Allows caching file timestamps for up-to-date checks                    |

## Unconfigured Projects

|Name                                             |Type|Description                      |
|-------------------------------------------------|----|---------------------------------|
|[`IHostObjectProvider`](building.md#host-objects)|Host|Provides host objects for builds.|

## Configured Projects

|Name                                                                |Type     |Description                                                      |
|--------------------------------------------------------------------|---------|-----------------------------------------------------------------|
|[`IBuildFiles`](building.md#building)                               |Extension|Allows building individual files in project                      |
|[`IBuildProject`](building.md#building)                             |Service  |Allows building the project                                      |
|[`IBuildSupport`](building.md#building)                             |Service  |Information about building the project                           |
|[`IBuildUpToDateCheckProvider`](building.md#up-to-date-checking)    |Extension|Allows projects to be checked for up-to-date status before build |
|[`IDeployProvider`](building.md#deploying-and-publishing)           |Extension|Allows Deploy action to be performed on project                  |
|[`IDesignTimeBuildCacheParticipant`](building.md#design-time-builds)|Extension|Allows caching the result of design-time builds (**internal**)   |
|[`IDesignTimeBuilderService`](building.md#design-time-builds)       |Host     |Provides design-time build service (**internal**)                |
|[`IDesignTimeBuildManagerService`](building.md#design-time-builds)  |Service  |Allows doing design-time builds (**internal**)                   |
|[`IPublishProvider`](building.md#deploying-and-publishing)          |Extension|Allows Publish action to be performed on project                 |
