Build Services
==============

# Building

The `IBuildProject` interface is exposed as part of the services of a `ConfiguredProject`. It allows callers to:

* Request a build for the project.
* Subscribe to a block that contains design-time build properties.
* Get build properties for full build and design-time build
* Check whether the project is considered up-to-date.

The result of a build is contained in a `IBuildResult`.

# Up-to-date Check

A project system can export a `IBuildUpToDateCheckProvider` interface 

# Scratch

BuildAction.cs
BuildManagerHostBase.cs
Dataflow
DesignTimeBuildCacheState.cs
IBatchingBuildManagerHost.cs
IBuildFiles.cs
IBuildManagerHost.cs
IBuildManagerHostBatchingService.cs
IBuildProjectInternal.cs
IBuildRequest.cs
IBuildSupport.cs
IBuildUpToDateCheckProvider.cs
ICommandLinePreviewProvider.cs
IDeployProvider.cs
IDesignTimeBuildCacheParticipant.cs
IDesignTimeBuilderService.cs
IDesignTimeBuildManagerService.cs
IDesignTimeBuildManagerServiceInternal.cs
IFileTimestampCache.cs
IHostObject.cs
IHostObjectProvider.cs
IPublishProvider.cs
Logging
OutputGroup
ProjectDesignTimeBuildResult.cs
Properties
Utilities
