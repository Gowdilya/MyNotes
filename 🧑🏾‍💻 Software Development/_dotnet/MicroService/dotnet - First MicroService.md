---
tags:
  - dotnet
  - MicroService
---
### What do these commands mean?

The `dotnet` command creates a new application of type `webapi` (that's a REST API endpoint).

- The `-o` parameter creates a directory named `MyMicroservice` where your app is stored.
- The `--no-https` flag creates an app that will run without an HTTPS certificate, to keep things simple for deployment.

```shell
dotnet new webapi -o MyMicroservice --no-https
```

### The generated code

Several files were created in the `MyMicroservice` directory, to give you a simple service that is ready to run, including the following files:

- `Program.cs` is the entry point file and contains all the settings and configuration that are loaded when the app starts and has code for a simple API that returns the weather forecast for the next five days. It also starts the application.
- `MyMycroservice.http` is used for testing ASP.NET Core projects.
- `MyMicroservice.csproj` defines the version of .NET the app is targeting, what libraries the project references, etc.
- `MyMicroservice.sln` defines the solution file that organizes projects in Visual Studio.
- The `launchSettings.json` file inside the `Properties` directory defines different profile settings for the local development environment. A port number ranging between 5000-5300 is automatically assigned at project creation and saved on this file.