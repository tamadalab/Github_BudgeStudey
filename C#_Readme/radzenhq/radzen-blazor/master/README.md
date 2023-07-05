![Radzen Blazor Components](RadzenBlazorDemos/wwwroot/images/radzen-blazor-components.png)

<h1 align="center">
    Radzen Blazor Components
</h1>

<p align="center">
    A set of <strong>70+ free and open source</strong> native Blazor UI controls.
</p>

<div align="center">

[See Online Demos](https://blazor.radzen.com) or [Read the Docs](https://blazor.radzen.com/docs/)

</div>

---

<p align="center">
    <a href="https://github.com/radzenhq/radzen-blazor/blob/master/LICENSE">
        <img alt="License - MIT" src="https://img.shields.io/github/license/radzenhq/radzen-blazor?logo=github&style=for-the-badge" />
    </a>
    <a href="https://www.nuget.org/packages/Radzen.Blazor">
        <img alt="NuGet Downloads" src="https://img.shields.io/nuget/dt/Radzen.Blazor?color=%232694F9&label=nuget%20downloads&logo=nuget&style=for-the-badge" />
    </a>
    <img alt="Last Commit" src="https://img.shields.io/github/last-commit/radzenhq/radzen-blazor?logo=github&style=for-the-badge" />
    <a href="https://github.com/radzenhq/radzen-blazor/graphs/contributors">
        <img alt="Github Contributors" src="https://img.shields.io/github/contributors/radzenhq/radzen-blazor?logo=github&style=for-the-badge" />
    </a>
    <a href="https://blazor.radzen.com">
        <img alt="Radzen Blazor Components - Online Demos" src="https://img.shields.io/badge/demos-online-brightgreen?color=%232694F9&logo=blazor&style=for-the-badge" />
    </a>
    <a href="https://blazor.radzen.com/docs">
        <img alt="Radzen Blazor Components - Documentation" src="https://img.shields.io/badge/docs-online-brightgreen?color=%232694F9&logo=blazor&style=for-the-badge" />
    </a>
</p>

## Why choose Radzen Blazor Components?

### :sparkles: Free

Radzen Blazor Components are open source and free for commercial use. You can install them from [NuGet](https://www.nuget.org/packages/Radzen.Blazor) or build your own copy from source.

Paid support is available as part of the [Radzen Professional subscription](https://www.radzen.com/blazor-studio/pricing/).

### :computer: Native

The components are implemented in C# and take full advantage of the Blazor framework. They do not depend on or wrap existing JavaScript frameworks or libraries.

Blazor Server and Blazor WebAssembly are fully supported.

### :seedling: Growing

We add new components and features on a regular basis.

Short development cycle. We release as soon as new stuff is available. No more quarterly releases.

## Support exceeding your expectations

### :speech_balloon: Community Support
Everybody is welcome to visit the [Radzen Community forum](https://forum.radzen.com/). Join the growing community and participate in the discussions!

### :dart: Dedicated Support

The Radzen team monitors the forum threads, but does not guarantee a response to every question. For guaranteed responses you may consider the dedicated support option.

Dedicated support for the Radzen Blazor Components is available as part of the [Radzen Professional subscription](https://www.radzen.com/blazor-studio/pricing/).

Our flagship product [Radzen Blazor Studio](https://www.radzen.com/blazor-studio/) provides tons of productivity features for Blazor developers:
- An industry-leading WYSIWYG Blazor design time canvas
- Scaffolding a complete CRUD applications from a database
- Built-in security - authentication and authorization
- Visual Studio Code and Professional support
- Deployment to IIS and Azure
- Dedicated support with 24 hour guaranteed response time

## Get started with Radzen Blazor Components

### 1. Install

Radzen Blazor Components are distributed as a [Radzen.Blazor NuGet package](https://www.nuget.org/packages/Radzen.Blazor). You can add them to your project in one of the following ways
- Install the package from command line by running `dotnet add package Radzen.Blazor`
- Add the project from the Visual NuGet Package Manager
- Manually edit the .csproj file and add a project reference

### 2. Import the namespace

Open the `_Imports.razor` file of your Blazor application and add this line `@using Radzen.Blazor`.

### 3. Include a theme

Radzen Blazor components come with five free themes: Material, Standard, Default, Dark, Software and Humanistic.

To use a theme
1. Pick a theme. The [online demos](https://blazor.radzen.com/colors) allow you to preview the available options via the theme dropdown located in the header. The Material theme is currently selected by default.
1. Include the theme CSS file in your Blazor application. Open `Pages\_Layout.cshtml` (Blazor Server .NET 6), `Pages\_Host.cshtml` (Blazor Server .NET 7) or `wwwroot/index.html` (Blazor WebAssembly) and include a theme CSS file by adding this snippet
   ```html
   <link rel="stylesheet" href="_content/Radzen.Blazor/css/material-base.css">
   ```

To include a different theme (i.e. Standard) just change the name of the CSS file:
```
<link rel="stylesheet" href="_content/Radzen.Blazor/css/standard-base.css">
```

### 4. Include Radzen.Blazor.js

Open `Pages\_Layout.cshtml` (Blazor Server .NET 6), `Pages\_Host.cshtml` (Blazor Server .NET 7) or `wwwroot/index.html` (Blazor WebAssembly) and include this snippet:

```html
<script src="_content/Radzen.Blazor/Radzen.Blazor.js"></script>
```

### 5. Use a component
Use any Radzen Blazor component by typing its tag name in a Blazor page e.g.
```html
<RadzenButton Text="Hi"></RadzenButton>
```

#### Data-binding a property
```razor
<RadzenButton Text=@text />
<RadzenTextBox @bind-Value=@text />
@code {
  string text = "Hi";
}
```

#### Handing events

```razor
<RadzenButton Click="@ButtonClicked" Text="Hi"></RadzenButton>
@code {
  void ButtonClicked()
  {

  }
}
```
## Run demos locally

Use Radzen.Server.sln to open and run demos as Blazor server application or Radzen.WebAssembly.sln to open and run demos as Blazor WebAssembly application. Radzen.sln has reference to all projects including tests.
