Build Services
==============

# Building

The `IBuildProject` interface is exposed as part of the services of a `ConfiguredProject`. It allows callers to:

* Request a build for the project.
* Subscribe to a block that contains design-time build properties.
* Get build properties for full build and design-time build
* Check whether the project is considered up-to-date.

The result of a build is contained in a `IBuildResult`.

# Deploying and Publishing

Projects that want to suport deploy and publish actions can export `IDeployProvider` and `IPublishProvider` at the `ConfiguredProject` level.

# Up-to-date Checking

A project system can export a `IBuildUpToDateCheckProvider` interface, which is tied to an instance of a `ConfiguredProject`. The interface will them be called to determine whether a project is known to be up-to-date and the build can be skipped.

The `IFileTimestampCache` service can be imported and used to cache file timestamps across all projects. Be aware, though, that the only updating the project system does for the cache is clearing it when a build happens.

# Scratch

* BuildAction.cs
* BuildManagerHostBase.cs
* Dataflow
* DesignTimeBuildCacheState.cs
* IBatchingBuildManagerHost.cs
* IBuildFiles.cs
* IBuildManagerHost.cs
* IBuildManagerHostBatchingService.cs
* IBuildProjectInternal.cs
* IBuildRequest.cs
* IBuildSupport.cs
* ICommandLinePreviewProvider.cs
* IDesignTimeBuildCacheParticipant.cs
* IDesignTimeBuilderService.cs
* IDesignTimeBuildManagerService.cs
* IDesignTimeBuildManagerServiceInternal.cs
* IHostObject.cs
* IHostObjectProvider.cs
* Logging
* OutputGroup
* ProjectDesignTimeBuildResult.cs
* Properties
* Utilities
