Project Service Serrvices
=========================

Services:

|Extension                                                            |Description           |
|---------------------------------------------------------------------|----------------------|
|[`IBuildManagerHostBatchingService`](building.md#build-manager-hosts)|Allows batching builds|

Extensions:

|Extension                                             |Description                                                             |
|------------------------------------------------------|------------------------------------------------------------------------|
|[`IBuildManagerHost`](building.md#build-manager-hosts)|Defines a build manager (can also implement `IBatchingBuildManagerHost`)|

`ConfiguredProject` Services
============================

Services:

|Service                                                      |Description                                     |
|-------------------------------------------------------------|------------------------------------------------|
|[`IBuildProject`](building.md#building)                      |Allows building the project                     |
|[`IBuildSupport`](building.md#building)                      |Information about building the project          |

Extensions:

|Extension                                                    |Description                                     |
|-------------------------------------------------------------|------------------------------------------------|
|[`IBuildFiles`](building.md#building)                        |Allows building individual files in project     |
