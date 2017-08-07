# ID4WithClientsOpenIDConnect

## Important Notices:
!!! THIS REPO IS JUST STARTING AND FOR NOW SHOULD BE CONSIDERED WORK IN PROGRESS!!!
I will remove this notice when the code is complete. 

!!! THIS REPO IS DEPENDENT on other github repositories for much of the source code of this project:
https://github.com/IdentityServer/IdentityServer4 - IdentityServer4 Authentication WebAPI.
https://github.com/IdentityServer/IdentityServer4.Quickstart.UI - MVC UI for "Login" and "Claims Consent"
https://github.not/AngularOpenIDConnectClient
https://github.not/WebApiResource

I will create a "WebForms project" from scratch that will connect to the IdentityServer4 UI and Authorization WebAPI via OWIN Middleware.

## Purpose of this repo:

The IdentityServer4 repo on its own does not have any UI Components, so the first 2 repos must be combined. I  decided to combine them into 1 project, although this is not necessary. Also the default IdentityServer4 sloution shows all Authentication FLows. I wioll focus only on Authorization Code and Hybrid Authorization Flows:

## To start:
... the IdentityServer4 Authentication WebAPI and MVC UI for "Login" and "Claims Consent":

open a PowerShell prompt and build the solution:
```cmd
cd \YourLocalFolder\IdentityServer4
build.ps1
cd \YourLocalFolder\IdentityServer4\src\Host
```
Make sure program.cs is set to UseUrls:
```csharp
  var host = new WebHostBuilder()
          .UseKestrel()
          .UseUrls("http://localhost:5000")
          .etc
```
```cmd
dotnet run
  Hosting environment: Production
  Content root path: C:\Github\IdentityServer4\src\Host
  Now listening on: http://localhost:5000
  Application started. Press Ctrl+C to shut down.
```

## To Login:

http://localhost:5000/account/login


## The purpose of this demo: 
This demo allows you to see project differences, via repo history, between a WebForms Application with no Authentication, and one that connects to Identity Server 4. It will also show you how to modify the default Identity Server 4 application so only WebFoem, MVC, and Angular Clients can connect in a secure fashion.

The theory is, if you already know how to remove your existing Membership Provider from a WebForms app leaving you with no Authentication, then by examining the before and after project differences, you should be able to see how to replace an existing Authentication and Authorization Membership Provider with ASP.Net Identity 4 and Identity Server 4.

## Running this demo:

Prerequisite repo "ID4-Server-Applications": https://github.com/boaldave/ID4-Server-Applications Once you realize that Identity Server 4 can be implemented as one or more applications, you may decide to split "Identity Server 4" into the 3 individual applications and host them on separate servers. For the purpose of this demo, the 3 applications have been packaged and are intended to be deployed as one. This repo contains forks of other projects that serve as base code for those applications with modifications, so breaking changes in those dependencies will not be a factor.
The 3 applications "ID4-Server-Applications" deployed as one application include:

ASP.Net Core MVC Login UI
ASP.Net Core WebApi Authorization Services
ASP.Net Core WebApi Token Services
You will need a server hosting the ID4-Server-Applications, which by default configuration, hosts the deployment at http://localhost:5000/

When you start this ID4-OpenIDClient-Webform WebForms application, its default configuration hosts the deployment at http://localhost:4000/.
