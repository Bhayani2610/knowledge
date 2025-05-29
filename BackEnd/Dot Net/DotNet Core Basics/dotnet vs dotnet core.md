# **NET Core vs .NET Framework – Detailed Description**

## 🔷**Difference between .Net Core and .Net Framework**
| Feature    | .NET Core | .NET Framework |
| -------- | ------- | ------- |
| Platform | Cross-platform (Windows, Linux, macOS) | Windows-only |
| Performance | High performance and optimized for modern workloads | Moderate, older architecture not optimized for all scenarios |
| App Types | Web, console, microservices, cloud, APIs, gRPC, Blazor | Web (ASP.NET), desktop (WinForms, WPF), Windows services |
| Deployment | Flexible (self-contained or framework-dependent) | Web (ASP.NET), desktop (WinForms, WPF), Windows services |
| Modularity | Modular, NuGet-based packages | Monolithic and bulky |
| Open Source | Fully open-source (.NET Foundation) | Partially open source |
| CLI Support | Powerful CLI tools (dotnet) | Limited or complex command-line tooling |
| Latest Development | Actively developed (.NET 6/7/8 and beyond) | Legacy, only minor updates (latest is 4.8) |
| Microservices Support | Built with containers, Docker, and microservices in mind | Difficult to adapt for modern cloud-native scenarios |
| Cross-Compatibility | Works on ARM, Linux, macOS | Strictly x86/x64 on Windows |


## 🔷**Cross-platform capabilities**
* .NET Core was designed to be platform-independent, unlike the older .NET Framework which only runs on Windows
* With .NET Core develop and run apps on 
  * Windows
  * Linux
  * macOS
* Use the same codebase across all supported platforms
* Package and run your apps in Docker containers for maximum portability

## 🔷**CoreCLR AND CoreFX**
  ### **CoreCLR**
  * **Think of CoreCLR as :** `"The engine that runs your .NET Core application"`
  * CoreCLR is the runtime component of .NET Core. It's responsible for executing your application code
  * Key Responsibilities:
    * **Just-In-Time (JIT) compilation** – Converts IL (Intermediate Language) to native machine code at runtime.
    * **Memory management** – Includes Garbage Collection (GC)
    * **Threading** – Manages threads and task scheduling
    * **Exception handling** – Handles runtime exceptions and errors
    * **Type safety and security** – Enforces security boundaries, type verification

  ### **CoreFX**
  * **Think of CoreFX as:** `"The toolbox of commonly used types and libraries that your code uses"`
  * CoreFX is the base class library (BCL) for .NET Core. It's a set of reusable code that developers use to build applications
  * What’s in CoreFX
    * Collections (e.g., `List<T>`, `Dictionary<K,V>`)
    * File I/O
    * Networking (e.g., `HttpClient`)
    * JSON/XML serialization
    * LINQ
    * String manipulation
    * Data types, DateTime, Math, Regex, etc.

  ### **How They Work Together**
  ```
  Your Code (C#) 
      ⬇️
  Compiler → Intermediate Language (IL)
      ⬇️
  CoreCLR → Executes the IL
      ↕️
  CoreFX → Provides standard libraries used in your code
  ```

  ### _NOTE_
  *  🔁 Evolution (as of .NET 5+ and .NET 6/7/8) With the release of .NET 5+, the .NET platform unified into a single runtime and library base:
  * CoreCLR + Mono runtimes merged into a unified .NET runtime.
  * CoreFX was folded into the .NET Base Class Library (BCL).

    | Component   | Role                            | Equivalent in .NET Framework           |
    | ----------- | ------------------------------- | -------------------------------------- |
    | **CoreCLR** | Runtime engine – runs the app   | CLR (Common Language Runtime)          |
    | **CoreFX**  | Libraries – what your code uses | .NET Framework Class Library (FCL/BCL) |


## 🔷**Typical Project Structure of a .NET Core Application**
###  **Project Root Overview**
```
/MyApp
├── Controllers/
├── Models/
├── Services/
├── wwwroot/
├── appsettings.json
├── Program.cs
├── Startup.cs       (only in .NET Core 3.1 / 5)
├── MyApp.csproj
├── Properties/
└── obj/ & bin/
```
| File                             | Role                                                   |
| -------------------------------- | ------------------------------------------------------ |
| `*.csproj`                       | Project metadata, dependencies                         |
| `Program.cs`                     | Entry point and app bootstrap                          |
| `Startup.cs`                     | Middleware & service configuration (pre-.NET 6)        |
| `appsettings.json`               | Config values and secrets                              |
| `Controllers/`                   | Holds MVC/Web API controllers                          |
| `Models/`                        | Data models (DTOs, entities)                           |
| `Services/`                      | Business logic/services (DI-registered classes)        |
| `wwwroot/`                       | Static files (JS, CSS, images)                         |
| `appsettings.json`               | Configuration file (connection strings, logging, etc.) |
| `Properties/launchSettings.json` | Local debug settings (profiles, environment)           |
| `obj/` & `bin/`                  | Build and compiled outputs (generated folders)         |
| `Controllers/Models/Services/`   | MVC pattern structure                                  |

