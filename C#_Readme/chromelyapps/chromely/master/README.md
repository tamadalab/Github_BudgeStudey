# ** Announcement ** - Chromely is no longer being maintained! 

For those who would like to continue working on the project via forks or alternative approaches, please send mattkol the appropriate links and they will be added here.

Thanks to all the contributors over the years for making the platform a great learning place.

Thank you all.
------------------------------------------------------------------------------------------------------------------------------------------
<p align="center"><img src="https://github.com/chromelyapps/Chromely/blob/master/nugets/chromely.ico?raw=true" /></p>
<h1 align="center">Chromely</h1>

<br />

For developers who are interested in [WebView2](https://docs.microsoft.com/en-us/microsoft-edge/webview2/) there is [EdgeSharp](https://github.com/edgesharp/EdgeSharp), an offshoot of Chromely.

Chromely is a lightweight alternative to <a href="https://github.com/ElectronNET/Electron.NET">Electron.NET</a>, <a href="https://github.com/electron/electron">Electron</a> for .NET/.NET Core developers.

Chromely is a .NET/.NET Core HTML5 Chromium desktop framework. It is focused on building apps based on [Xilium.CefGlue](https://gitlab.com/xiliumhq/chromiumembedded/cefglue), [CefSharp](https://github.com/chromelyapps/CefSharp) implementations of  embedded Chromium ([CEF](https://bitbucket.org/chromiumembedded/cef)) **without WinForms or WPF**, but can be extended to use WinForms or WPF. Chromely uses **Windows**, **Linux** and **MacOS** native GUI API as "thin" chromium hosts.

With Chromely you can build Single Page Application (SPA) HTML5 desktop apps with or without Node/npm. Building SPA apps using Blazor or javascript frameworks like Angular, React, Vue or similar is easy. You can use Visual Studio Code or any IDE you are familiar with as long as Chromely knows the entry html file from the compiled/bundled files. For more info please see - [Blazor-Demos](https://github.com/chromelyapps/demo-projects/tree/master/blazor) and [Chromely-Apps](https://github.com/chromelyapps/demo-projects/tree/master/angular-react-vue).

Options of communicating (IPC) with rendering process are via:

- Generic Message Routing - more info @ [Generic Message Routing](https://github.com/chromelyapps/Chromely/blob/master/Documents/generic_message_routing.md).
- Ajax HTTP/XHR -  more info @ [Custom Scheme Handling](https://github.com/chromelyapps/Chromely/blob/master/Documents/ajax_xhr_request_handling.md).

##### If you like Chromely, please give it a star - it helps! #####

Have a quick question? Wanna chat? Connect on  [![Join the chat at https://gitter.im/chromely_/Lobby](https://badges.gitter.im/chromely_/Lobby.svg)](https://gitter.im/chromely_/Lobby?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)

Have an app/project/tool using Chromely - [please share!](https://github.com/chromelyapps/Chromely/issues/63)

### Platforms
Cross-platform -**Windows**, **Linux**, **MacOS**. Built on CEF, CefGlue, NET Standard 2.0, .NET Core 3.0, .NET Framework 4.61 and above.

- Windows<sup>(1)</sup> 32-bit 
- Windows<sup>(1)</sup> 64-bit 
- Linux<sup>(2)</sup> 32-bit   
- Linux<sup>(2)</sup> 64-bit   
- MacOSX<sup>(3)</sup> 64-bit  
- Linux ARM<sup>(4)</sup>  [Raspberry Pi](Documents/raspberrry_pi.md)      

&nbsp;<sup>(1)</sup>&nbsp; Windows 7, Service Pack 1 and newer    
&nbsp;<sup>(2)</sup>&nbsp; Ubuntu 16.04 and newer    
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;(Mono currently not working)    
&nbsp;<sup>(3)</sup>&nbsp; Tested on macOS Mojave 10.14.6  (Other versions will likely work too)     
&nbsp;<sup>(4)</sup>&nbsp; i.e. Raspberry Pi 3+   (starting with v5.x)    
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;(for v4.x - manual download of CEF builds for ARM required,  available on http://chromely.org/cefbuilds/index.html) 

[![Chromely.Core](http://img.shields.io/nuget/vpre/Chromely.Core.svg?style=flat&label=Chromely.Core)](https://www.nuget.org/packages/Chromely.Core)
[![Chromely](http://img.shields.io/nuget/vpre/Chromely.svg?style=flat&label=Chromely)](https://www.nuget.org/packages/Chromely)
[![Chromely.Owin](http://img.shields.io/nuget/vpre/Chromely.Owin.svg?style=flat&label=Chromely.Owin)](https://www.nuget.org/packages/Chromely.Owin)

[![Chromely + Angular](https://img.shields.io/badge/Chromely%20Apps-Built%20with%20Angular%202%2B-green.svg)](https://github.com/chromelyapps/demo-projects/tree/master/angular-react-vue/ChromelyAngular)
<br>[![Chromely + React](https://img.shields.io/badge/Chromely%20Apps-Built%20with%20React-green.svg)](https://github.com/chromelyapps/demo-projects/tree/master/angular-react-vue/ChromelyReact)
<br>[![Chromely + Vue](https://img.shields.io/badge/Chromely%20Apps-Built%20with%20Vue-green.svg)](https://github.com/chromelyapps/demo-projects/tree/master/angular-react-vue/ChromelyVue) 

### Creating a Simple App
For more info see - [Getting Started](https://github.com/chromelyapps/Chromely/blob/master/Documents/getting_started.md) or [Wiki](https://github.com/chromelyapps/Chromely/wiki)

A basic Chromely project requires:

````csharp
ThreadApt.STA();

AppBuilder
    .Create(args)
    .UseApp<ChromelyBasicApp>()
    .Build()
    .Run();
````

### Chromely Demos 
Get started with our [demos](https://github.com/chromelyapps/demo-projects). 
![](https://github.com/chromelyapps/Chromely/blob/master/Screenshots/chromely_screens_n3.gif)

### References
* CEF - https://bitbucket.org/chromiumembedded/cef
* Xilium.CefGlue - https://gitlab.com/xiliumhq/chromiumembedded/cefglue
* Chromium.AspNetCore.Bridge - https://github.com/amaitland/Chromium.AspNetCore.Bridge

Contributing
---
Contributions are always welcome, via PRs, issues raised, or any other means. To become a dedicated contributor, please [contact the Chromely team](https://github.com/orgs/chromelyapps/people) or [raise an issue](https://github.com/chromelyapps/Chromely/issues) mentioning your intent.

License
---
Chromely is MIT licensed. For dependency licenses [please see](https://github.com/chromelyapps/Chromely/blob/master/LICENSE.md).

