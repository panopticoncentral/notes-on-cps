Build Services
==============

# Building

The `IBuildProject` and `IBuildProjectInternal` interfaces are exposed as part of the services of a `ConfiguredProject`. They allow callers to:

* Request a build for the project.
* Subscribe to a block that contains design-time build properties.
* Get build properties for full build and design-time build
* Check whether the project is considered up-to-date.

The result of a build is contained in a `IBuildResult`. The `IBuildSupport` interface can be used to determine information about a project's build, such as what targets are run for a particular `BuildAction`, the current status of the project's build (represented as `BuildStatus`), and whether the project supports particular `BuildAction`s.

A `ConfiguredProject` may support compiling individual files rather than the whole project at once. If it supports this, it exports the `IBuildFiles` interface, with the result returned in a `PrepareBuildFilesResult` structure.

# Build Hosts

When a project is built, a _build manager host_ is the component that actually does the build, managing an instance of a MSBuild build manager. Build manager hosts export the `IBuildManagerHost` interface, and build manager hosts that support batching of build requests export the `IBatchingBuildManagerHost` interface. Build manager hosts derive from the `BuildManagerHostBase` class. Batching build manager hosts can use the project service `IBuildManagerHostBatchingService` to schedule batched builds.

Build manager hosts represent build requests using the `IBuildRequest` interface.

# Design-time Builds

A _design-time build_ is a build that the project system runs to determine information about the output of the project without actually executing the full build. (For example, the design-time build only collects the input to a compiler like `csc`, it doesn't actually execute the compiler itself.)

The internal `IDesignTimeBuilderService` is a `ConfiguredProject` service that manages the relationship between the Common Project System and the underlying Project Services design-time builder. The internal `IDesignTimeBuildManagerService` and `IDesignTimeBuildManagerServiceInternal` interfaces are `ConfiguredProject` services that can be used to initiate design-time builds. The result of a design-time build is returned as a `ProjectDesignTimeBuildResult` instance. 

If a project supports caching the result of a design-time build, it can provide a `IDesignTimeBuildCacheParticipant` instance and use the `DesignTimeBuildCacheState` enum to indicate cache state.

# Host Objects

For compatibility with existing Visual Studio extensions, specifically [single file generators](https://docs.microsoft.com/en-us/visualstudio/extensibility/internals/implementing-single-file-generators), MSBuild host objects can be provided at the `UnconfiguredProject` level through the `IHostObjectProvider` and `IHostObject` interfaces.

# Deploying and Publishing

Projects that want to suport deploy and publish actions can export `IDeployProvider` and `IPublishProvider` at the `ConfiguredProject` level.

# Up-to-date Checking

A project system can export a `IBuildUpToDateCheckProvider` interface, which is tied to an instance of a `ConfiguredProject`. The interface will them be called to determine whether a project is known to be up-to-date and the build can be skipped.

The `IFileTimestampCache` service can be imported and used to cache file timestamps across all projects. Be aware, though, that the only updating the project system does for the cache is clearing it when a build happens.

# Scratch

* Dataflow
* ICommandLinePreviewProvider.cs
* Logging
* OutputGroup
* Properties
* Utilities
