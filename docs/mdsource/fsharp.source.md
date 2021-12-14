# Usage in FSharp


## NullValueHandling

By default [DefaultValueHandling is Ignore](/docs/serializer-settings.md#default-settings). Since F# `Option.None` is treated as null, it will be ignored by default. To include `Option.None` use `VerifierSettings.AddExtraSettings` at module startup:

snippet: NullValueHandling


## Async Qwerks

F# does not respect implicit operator conversion. `SettingsTask` uses implicit operator conversion to provide a fluent api in combination with an instance that can be awaited. As such `SettingsTask.ToTask()` needs to be awaited when used inside F#.

snippet: FsTest

You can also use a `task` computation expression builder, such as the ones included in [Ply](https://github.com/crowded/ply), [TaskBuilder.fs](https://github.com/rspeele/TaskBuilder.fs), or starting with F# 6.0 the native one in FSharp.Core, to await tasks:

snippet: FsTestTask

## Full tests

snippet: FSharpTests/Tests.fs