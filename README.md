![Shift iQ](https://www.shiftiq.com/images/logos/shift-iq.png)

Shift iQ is a learning management system that specializes in the assessment of skills to align talent to career and training pathways. It features a comprehensive, competency-based approach, and it provides a credible record of demonstrated knowledge and achieved skills. 

Shift iQ is the technology behind many great online platforms and programs, including:

* [Competency Management and Development System](https://www.keyeracmds.com)
* [Cross-Trade Pathways](https://www.crosstrade.ca/)
* [Facility Access to Skilled Trades](https://fastcanada.ca)

## About this Software Development Kit

This repository contains free and open source code for a Software Development Kit (SDK) that can be used by third-party developers to integrate Shift iQ into their own applications, libraries, and business intelligence reporting tools.

> Please note this SDK is undergoing a significant overhaul to improve its performance and security, and to provide developers with a much wider and much richer set of features. Therefore, it is subject to change. This readme will be updated whenever updates to the SDK are posted.

The SDK communicates with the Shift platform through an open [REST API](https://restfulapi.net). It includes sample code for Microsoft [.NET 8.0](https://dotnet.microsoft.com/en-us) and [.NET Framework 4.8](https://dotnet.microsoft.com/en-us/download/dotnet-framework/net48). Of course, you are not limited to using Microsoft .NET in your implementations. The API is accessible using any programming language that supports [HTTPS](https://datatracker.ietf.org/doc/html/rfc2818) requests and [JSON](https://www.json.org/json-en.html) responses; for example: [cURL](https://curl.se), [Go](https://go.dev), [JavaScript](https://developer.mozilla.org/en-US/docs/Web/JavaScript), [Node.js](https://nodejs.org/en), [PHP](https://www.php.net), [Power Query M](https://learn.microsoft.com/en-us/powerquery-m), [PowerShell](https://learn.microsoft.com/en-us/powershell), [Python](https://www.python.org), and [Ruby](https://www.ruby-lang.org/en).

### Source Code

#### Shift.Contract

This is a .NET Standard 2.0 library that contains C# classes for all Request and Response objects supported by the API. It is not required in your applications, but may provide a useful reference for the design and implementation of your own request and response objects. 

Because this library is implemented using .NET Standard 2.0, you can reference it from a .NET Core application and/or a .NET Framework application.

#### Shift.Api.Sdk.Core

This is a .NET 8.0 library in which developers can define the inventory of API endpoints to be used by their application. It uses [Refit](https://github.com/reactiveui/refit) to dynamically generate the implementation for a REST API interface.

#### Shift.Api.Sdk.Core.Demo

This is a .NET 8.0 console application that demonstrates how to use the SDK in a .NET (Core) application.

* To run this demo, simply update the configurating settings in `AppSettings.json` with the Developer API Token Secret (and the API Endpoint URL) provided by Shift iQ to your organization.

#### Shift.Api.Sdk.Framework

This is a .NET Framework 4.8 library in which developers can define the inventory of API endpoints to be used by their application. It uses [Refit](https://github.com/reactiveui/refit) to dynamically generate the implementation for a REST API interface.

#### Shift.Api.Sdk.Core.Demo

This is a .NET 8.0 console application that demonstrates how to use the SDK in a .NET (Core) application.

* To run this demo, simply update the configurating settings in `App.config` with the Developer API Token Secret (and the API Endpoint URL) provided by Shift iQ to your organization.
