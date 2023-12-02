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

## Getting Started

[Contact us](https://www.shiftiq.com/contact) to request a **Developer API Token Secret**. This is a random cryptographic base-64 encoded secret key. Store it in a safe place! 

Your secret will look something like this:

* `ZtkO1K/XhUYNIJRut0XnQzNp2c2r7hUFW459GrvYP+TPpwo90IhpFnvHN0otnQ3j8LMPowaw9soVcs3jabGvAg==`

The Shift iQ team will provide you with a **Developer API Endpoint URL**. This is a URL assigned to your organization for access to the API. Your endpoint will look something like this:

* `https://dev.shiftiq.com:12345`

"12345" identifies a secure port number on the API server. Your port number will differ.

## Authentication

To identify yourself to the API, send a POST request to the `token` endpoint with your Secret in the body of your request. The API validates your secret and returns a Bearer Token. You'll use this token in all your subsequent API requests.

The token will look something like this:

* `eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6IkpvaG4gRG9lIiwiaWF0IjoxNTE2MjM5MDIyfQ.SflKxwRJSMeKKF2QT4fwpMeJf36POk6yJV_adQssw5c`

The Shift API uses open, industry-standard [JSON Web Tokens](https://jwt.io) exclusively. Each JSON Web Token (JWT) generated by the Shift API includes the following information:

* The unique identifier assigned to your developer account.
* The unique identifier assigned to your organization account.
* The roles assigned to your account. These determine the permissions granted to your API requests.
* Your name and email address.
* Your language preference and time zone.
* The IP address from which your token was requested. For security reasons, subsequent API requests must originate from the same IP.
* The expected lifetime (in minutes) for your token, after which your token will expire. You'll need to request a new token before sending new API requests.
* The exact date and time when your token will expire, regardless of the its expected lifetime.
* A digital signature generated using [Hash-based Message Authentication Code](https://www.techtarget.com/searchsecurity/definition/Hash-based-Message-Authentication-Code-HMAC) (HMAC) with a [SHA256](https://www.simplilearn.com/tutorials/cyber-security-tutorial/sha-256-algorithm) hash. This signature is verified by the server for every API request to ensure your token is valid; this also guarantees no third-party has tampered with it or intercepted it.

## Authorization

The Shift API uses the Bearer Token authorization scheme. 

Use the JWT authentication token generated by the API for all your subsequent API requests. 

We recommend using Postman to experiment with the API. Here are the steps to do this if you are using [Postman](https://learning.postman.com/docs/sending-requests/authorization/authorization-types/#bearer-token):

* In the request Authorization tab, select Bearer Token from the Type dropdown list.
* In the Token field, enter your API key value.
* For added security, store it in a variable and reference the variable by name.

Please note that each API endpoint has an [access-control list](https://en.wikipedia.org/wiki/Access-control_list) managed by the Shift iQ development team. The access-control list for a given endpoint determines the permissions associated with it. If you send a request to an endpoint and your account is not granted access to it, then you will receive an 403 Forbidden response. Contact our DevOps team if you need an update to your account permissions.
