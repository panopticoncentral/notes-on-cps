Build Services
==============

# Building

The `IBuildProject` and `IBuildProjectInternal` interfaces are exposed as part of the services of a `ConfiguredProject`. They allow callers to:

* Request a build for the project.
* Subscribe to a block that contains design-time build properties.
* Get build properties for full build and design-time build
* Check whether the project is considered up-to-date.

The result of a build is contained in a `IBuildResult`.

# Design-time Builds

A _design-time build_ is a build that the project system runs to determine information about the output of the project without actually executing the full build. (For example, the design-time build only collects the input to a compiler like `csc`, it doesn't actually execute the compiler itself.)

The internal `IDesignTimeBuilderService` is a `ConfiguredProject` service that manages the relationship between the Common Project System and the underlying Project Services design-time builder. The internal `IDesignTimeBuildManagerService` and `IDesignTimeBuildManagerServiceInternal` interfaces are `ConfiguredProject` services that can be used to initiate design-time builds. The result of a design-time build is returned as a `ProjectDesignTimeBuildResult` instance. If a project supports caching the result of a design-time build, it can provide a `IDesignTimeBuildCacheParticipant` instance.

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
* IBuildRequest.cs
* IBuildSupport.cs
* ICommandLinePreviewProvider.cs
* IHostObject.cs
* IHostObjectProvider.cs
* Logging
* OutputGroup
* Properties
* Utilities
