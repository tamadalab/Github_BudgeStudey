# RoslynPad

![RoslynPad](src/RoslynPad/Resources/RoslynPad.png)

A cross-platform C# editor based on Roslyn and AvalonEdit

[![Downloads](https://img.shields.io/github/downloads/aelij/RoslynPad/total.svg?style=flat-square)](https://github.com/aelij/RoslynPad/releases)

Also available to download in the Microsoft Store:

<a href="https://www.microsoft.com/store/apps/9nctj2cqwxv0?ocid=badge"><img src="https://get.microsoft.com/images/en-us%20light.svg" height="50" alt="Microsoft Store badge logo" /></a>

## Packages

RoslynPad is also available as NuGet packages which allow you to use Roslyn services and the editor in your own apps.

|Package Name|Description|
|------------|-----------|
|[![NuGet](https://img.shields.io/nuget/v/RoslynPad.Roslyn.svg?style=flat-square)](https://www.nuget.org/packages/RoslynPad.Roslyn) `RoslynPad.Roslyn`|Exposes many Roslyn editor services that are currently internal|
|[![NuGet](https://img.shields.io/nuget/v/RoslynPad.Roslyn.Windows.svg?style=flat-square)](https://www.nuget.org/packages/RoslynPad.Roslyn.Windows) `RoslynPad.Roslyn.Windows`|Provides platform-specific (WPF) implementations for UI elements required by the `RoslynPad.Roslyn` package|
|[![NuGet](https://img.shields.io/nuget/v/RoslynPad.Roslyn.Avalonia.svg?style=flat-square)](https://www.nuget.org/packages/RoslynPad.Roslyn.Avalonia)` RoslynPad.Roslyn.Avalonia`|Provides platform-specific (Avalonia) implementations for UI elements required by the `RoslynPad.Roslyn` package|
|[![NuGet](https://img.shields.io/nuget/v/RoslynPad.Editor.Windows.svg?style=flat-square)](https://www.nuget.org/packages/RoslynPad.Editor.Windows) `RoslynPad.Editor.Windows`|Provides a Roslyn-based code editor using AvaloniaEdit (WPF platform) with completion, diagnostics, and quick actions|
|[![NuGet](https://img.shields.io/nuget/v/RoslynPad.Editor.Avalonia.svg?style=flat-square)](https://www.nuget.org/packages/RoslynPad.Editor.Avalonia) `RoslynPad.Editor.Avalonia`|Provides a Roslyn-based code editor using AvalonEdit (Avalonia platform) with completion, diagnostics, and quick actions|

`RoslynPad.Roslyn*` package versions must correspond to Roslyn's.

[Code samples](https://github.com/aelij/RoslynPad/tree/main/samples)

## Building

Open `src\RoslynPad.sln` in Visual Studio 2022.

## Running the cross-platform .NET Core Avalonia version (on Mac or Linux)

* Install .NET Core SDK 7.0
* Download and unzip `RoslynPadAvalonia.zip` from the latest release
* Run `dotnet RoslynPad.dll`

## Features

### Completion

![Completion](docs/Completion.png)

### Signature Help

![Signature Help](docs/SignatureHelp.png)

### Diagnostics

![Diagnostics](docs/Diagnostics.png)

### Code Fixes

![Code Fixes](docs/CodeFixes.png)
