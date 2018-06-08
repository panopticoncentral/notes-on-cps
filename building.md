# Build Services

## Building

The `ConfiguredProject` service `IBuildProject` allows callers to:

* Request a build for the project.
* Subscribe to a block that contains design-time build properties.
* Get build properties for full build and design-time build.
* Check whether the project is considered up-to-date.

The result of a build is contained in a `IBuildResult`. The `ConfiguredProject` service `IBuildSupport` can be used to determine information about a project's build, such as what targets are run for a particular `BuildAction`, the current status of the project's build (represented as `BuildStatus`), and whether the project supports a particular `BuildAction`.

The `ConfiguredProject` extension `IBuildFiles` supports compiling individual files rather than the whole project at once. The result is returned in a `PrepareBuildFilesResult` structure.

## Build Manager Hosts

When a project is built, a _build manager host_ is the component that actually does the build, managing an instance of a MSBuild build manager. The project system extension `IBuildManagerHost` defines a new build manager, and build manager hosts that support batching of build requests also implements the `IBatchingBuildManagerHost` interface. Batching build manager hosts can use the project system service `IBuildManagerHostBatchingService` to schedule batched builds.

Build manager hosts represent build requests using the `IBuildRequest` interface.

### Standard Hosts

Three standard build manager hosts are provided. The `IndependentBuildManagerHost` is provided by the base framework and builds using its own private MSBuild `BuildManager`, meaning that all projects have their own `BuildManager`. When running in Visual Studio, the `SolutionBuildManagerParticipant` builds using a `BuildManager` shared among all projects in the solution. The `BuildManagerAccessorDesignTime` builds using the Visual Studio `IVsBuildManagerAccessor3` interface and is used internally for design-time builds that cannot run out of process. 

## Design-time Builds

A _design-time build_ is a build that the project system runs to determine information about the output of the project without actually executing the full build. (For example, the design-time build only collects the input to a compiler like `csc.exe`, it doesn't actually execute the compiler itself.)

The internal `ConfiguredProject` host service `IDesignTimeBuilderService` manages the relationship between the Common Project System and the underlying Project Services design-time builder. The internal `ConfiguredProject` service `IDesignTimeBuildManagerService` can be used to initiate design-time builds. The result of a design-time build is returned as a `ProjectDesignTimeBuildResult` instance. 

The internal `ConfiguredProject` extension `IDesignTimeBuildCacheParticipant` allows a project to support caching the result of a design-time build. The `DesignTimeBuildCacheState` enum indicates cache state.

Note that if a project is dirty in memory, the `IDesignTimeBuilderService` cannot be used because it may run in another process (and therefore will not have access to the in-memory state of the project). In that situation, the project will be built in-process. (Regular builds always do a save of the project first, so this is not an issue for them.)

## Host Objects

For compatibility with existing Visual Studio extensions, specifically [single file generators](https://docs.microsoft.com/en-us/visualstudio/extensibility/internals/implementing-single-file-generators), the `UnconfiguredProject` host service `IHostObjectProvider` can provide MSBuild host objects as `IHostObject` instances.

## Deploying and Publishing

The `ConfiguredProject` extensions `IDeployProvider` and `IPublishProvider` provide the ability to support deploy and publish actions for projects.

## Up-to-date Checking

The `ConfiguredProject` extension `IBuildUpToDateCheckProvider` allows build manager hosts to determine whether a project is known to be up-to-date and the build of the project can be skipped.

An up-to-date check provider can choose whether it should be run before critical tasks are finished, or whether it has to wait until after all critical tasks have been finished. (A critical task is one that must complete before an operation can be started, for example NuGet restore must be completed before a Build operation can start.) This is controlled by the `ExportMetadata` Boolean value `BeforeDrainCriticalTasks`. It is better, if at all possible, to run before critical tasks are finished. 

The project system service `IFileTimestampCache` can be used to cache file timestamps across all projects. **NOTE** The only updating the project system does for the cache is clearing it when a build happens.
