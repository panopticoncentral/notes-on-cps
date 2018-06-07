# Project System

## Services

|Service                                                              |Description                                         |
|---------------------------------------------------------------------|----------------------------------------------------|
|[`IBuildManagerHostBatchingService`](building.md#build-manager-hosts)|Allows batching builds                              |
|[`IFileTimestampCache`](building.md#up-to-date-checking)             |Allows caching file timestamps for up-to-date checks|

## Extensions

|Extension                                             |Description                                                             |
|------------------------------------------------------|------------------------------------------------------------------------|
|[`IBuildManagerHost`](building.md#build-manager-hosts)|Defines a build manager (can also implement `IBatchingBuildManagerHost`)|

# `UnconfiguredProject`

## Host Services

|Service                                          |Description                      |
|-------------------------------------------------|---------------------------------|
|[`IHostObjectProvider`](building.md#host-objects)|Provides host objects for builds.|

# `ConfiguredProject`

## Services

|Service                                                           |Description                                   |
|------------------------------------------------------------------|----------------------------------------------|
|[`IBuildProject`](building.md#building)                           |Allows building the project                   |
|[`IBuildSupport`](building.md#building)                           |Information about building the project        |
|[`IDesignTimeBuildManagerService`](building.md#design-time-builds)|Allows doing design-time builds (**internal**)|

## Host Services

|Service                                                      |Description                                      |
|-------------------------------------------------------------|-------------------------------------------------|
|[`IDesignTimeBuilderService`](building.md#design-time-builds)|Provides design-time build service (**internal**)|

## Extensions

|Extension                                                           |Description                                                      |
|--------------------------------------------------------------------|-----------------------------------------------------------------|
|[`IBuildFiles`](building.md#building)                               |Allows building individual files in project                      |
|[`IBuildUpToDateCheckProvider`](building.md#up-to-date-checking)    |Allows projects to be checked for up-to-date status before build |
|[`IDeployProvider`](building.md#deploying-and-publishing)           |Allows Deploy action to be performed on project                  |
|[`IDesignTimeBuildCacheParticipant`](building.md#design-time-builds)|Allows caching the result of design-time builds (**internal**)   |
|[`IPublishProvider`](building.md#deploying-and-publishing)          |Allows Publish action to be performed on project              |
