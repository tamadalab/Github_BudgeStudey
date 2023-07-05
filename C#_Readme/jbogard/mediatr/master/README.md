MediatR
=======

![CI](https://github.com/jbogard/MediatR/workflows/CI/badge.svg)
[![NuGet](https://img.shields.io/nuget/dt/mediatr.svg)](https://www.nuget.org/packages/mediatr) 
[![NuGet](https://img.shields.io/nuget/vpre/mediatr.svg)](https://www.nuget.org/packages/mediatr)
[![MyGet (dev)](https://img.shields.io/myget/mediatr-ci/v/MediatR.svg)](https://myget.org/gallery/mediatr-ci)

Simple mediator implementation in .NET

In-process messaging with no dependencies.

Supports request/response, commands, queries, notifications and events, synchronous and async with intelligent dispatching via C# generic variance.

Examples in the [wiki](https://github.com/jbogard/MediatR/wiki).

### Installing MediatR

You should install [MediatR with NuGet](https://www.nuget.org/packages/MediatR):

    Install-Package MediatR
    
Or via the .NET Core command line interface:

    dotnet add package MediatR

Either commands, from Package Manager Console or .NET Core CLI, will download and install MediatR and all required dependencies.

### Using Contracts-Only Package

To reference only the contracts for MediatR, which includes:

- `IRequest` (including generic variants)
- `INotification`
- `IStreamRequest`

Add a package reference to [MediatR.Contracts](https://www.nuget.org/packages/MediatR.Contracts)

This package is useful in scenarios where your MediatR contracts are in a separate assembly/project from handlers. Example scenarios include:
- API contracts
- GRPC contracts
- Blazor

### Registering with `IServiceCollection`

MediatR supports `Microsoft.Extensions.DependencyInjection.Abstractions` directly. To register various MediatR services and handlers:

```
services.AddMediatR(cfg => cfg.RegisterServicesFromAssemblyContaining<Startup>());
```

or with an assembly:

```
services.AddMediatR(cfg => cfg.RegisterServicesFromAssembly(typeof(Startup).Assembly));
```

This registers:

- `IMediator` as transient
- `ISender` as transient
- `IPublisher` as transient
- `IRequestHandler<,>` concrete implementations as transient
- `IRequestHandler<>` concrete implementations as transient
- `INotificationHandler<>` concrete implementations as transient
- `IStreamRequestHandler<>` concrete implementations as transient
- `IRequestPreProcessor<>` concrete implementations as transient
- `IRequestPostProcessor<,>` concrete implementations as transient
- `IRequestExceptionHandler<,,>` concrete implementations as transient
- `IRequestExceptionAction<,>)` concrete implementations as transient

This also registers open generic implementations for:

- `INotificationHandler<>`
- `IRequestPreProcessor<>`
- `IRequestPostProcessor<,>`
- `IRequestExceptionHandler<,,>`
- `IRequestExceptionAction<,>`

To register behaviors:

```csharp
services.AddMediatR(cfg => {
    cfg.RegisterServicesFromAssembly(typeof(Startup).Assembly);
    cfg.AddBehavior<IPipelineBehavior<Ping, Pong>, PingPongBehavior>();
    cfg.AddOpenBehavior(typeof(GenericBehavior<,>));
    });
```
