
# Getting Started with Logalty Certificate Issuance API (Certy)

## Introduction

API for certificate issuance through Logalty's "Certy" service.

### Authentication

This API uses OAuth2 client credentials flow. A pair of keys (`client_id` / `client_secret`)
per environment must be requested from the Logalty integration team at **integration@logalty.com**.

### Flow overview

1. Authenticate against the OAuth2 server to obtain a Bearer token.
2. Create a certificate issuance transaction.
3. Query the transaction status.
4. Download evidences (images, video, OCR) when available.
5. Perform operations (resend access, cancel) if needed.
6. Receive event notifications via the Feedback webhook.

## Install the Package

If you are building with .NET CLI tools then you can also use the following command:

```bash
dotnet add package ApimaticLogaltySDK --version 0.0.1
```

You can also view the package at:
https://www.nuget.org/packages/ApimaticLogaltySDK/0.0.1

## Initialize the API Client

**_Note:_** Documentation for the client can be found [here.](https://www.github.com/sdks-io/apimatic-logalty-dotnet-sdk/tree/0.0.1/doc/client.md)

The following parameters are configurable for the API Client:

| Parameter | Type | Description |
|  --- | --- | --- |
| CertyServer | `string` | Hostname of the Certy API server<br>*Default*: `"certy_server"` |
| Oauth2Server | `string` | Hostname of the OAuth2 server<br>*Default*: `"oauth2_server"` |
| Environment | [`Environment`](https://www.github.com/sdks-io/apimatic-logalty-dotnet-sdk/tree/0.0.1/README.md#environments) | The API environment. <br> **Default: `Environment.Production`** |
| Timeout | `TimeSpan` | Http client timeout.<br>*Default*: `TimeSpan.FromSeconds(30)` |
| HttpClientConfiguration | [`Action<HttpClientConfiguration.Builder>`](https://www.github.com/sdks-io/apimatic-logalty-dotnet-sdk/tree/0.0.1/doc/http-client-configuration-builder.md) | Action delegate that configures the HTTP client by using the HttpClientConfiguration.Builder for customizing API call settings.<br>*Default*: `new HttpClient()` |
| LogBuilder | [`LogBuilder`](https://www.github.com/sdks-io/apimatic-logalty-dotnet-sdk/tree/0.0.1/doc/log-builder.md) | Represents the logging configuration builder for API calls |
| BearerAuthCredentials | [`BearerAuthCredentials`](https://www.github.com/sdks-io/apimatic-logalty-dotnet-sdk/tree/0.0.1/doc/auth/oauth-2-bearer-token.md) | The Credentials Setter for OAuth 2 Bearer token |
| BasicAuthCredentials | [`BasicAuthCredentials`](https://www.github.com/sdks-io/apimatic-logalty-dotnet-sdk/tree/0.0.1/doc/auth/basic-authentication.md) | The Credentials Setter for Basic Authentication |

The API client can be initialized as follows:

### Code-Based Initialization

```csharp
using LogaltyCertificateIssuanceApiCerty.Standard;
using LogaltyCertificateIssuanceApiCerty.Standard.Authentication;
using Microsoft.Extensions.Logging;

namespace ConsoleApp;

LogaltyCertificateIssuanceApiCertyClient client = new LogaltyCertificateIssuanceApiCertyClient.Builder()
    .BearerAuthCredentials(
        new BearerAuthModel.Builder(
            "AccessToken"
        )
        .Build())
    .BasicAuthCredentials(
        new BasicAuthModel.Builder(
            "Username",
            "Password"
        )
        .Build())
    .HttpClientConfig(httpClientConfig =>
        httpClientConfig.Timeout(TimeSpan.FromSeconds(100)))
    .Environment(LogaltyCertificateIssuanceApiCerty.Standard.Environment.Production)
    .CertyServer("certy_server")
    .Oauth2Server("oauth2_server")
    .LoggingConfig(config => config
        .LogLevel(LogLevel.Information)
        .RequestConfig(reqConfig => reqConfig.Body(true))
        .ResponseConfig(respConfig => respConfig.Headers(true))
    )
    .Build();
```

### Configuration-Based Initialization

```csharp
using LogaltyCertificateIssuanceApiCerty.Standard;
using Microsoft.Extensions.Configuration;

namespace ConsoleApp;

// Build the IConfiguration using .NET conventions (JSON, environment, etc.)
var configuration = new ConfigurationBuilder()
    .AddJsonFile("config.json")
    .AddEnvironmentVariables() // [optional] read environment variables
    .Build();

// Instantiate your SDK and configure it from IConfiguration
var client = LogaltyCertificateIssuanceApiCertyClient
    .FromConfiguration(configuration.GetSection("LogaltyCertificateIssuanceApiCerty"));
```

See the [Configuration-Based Initialization](https://www.github.com/sdks-io/apimatic-logalty-dotnet-sdk/tree/0.0.1/doc/configuration-based-initialization.md) section for details.

## Environments

The SDK can be configured to use a different environment for making API calls. Available environments are:

### Fields

| Name | Description |
|  --- | --- |
| Production | **Default** Certy API server |
| Environment2 | OAuth2 authentication server |

## Authorization

This API uses the following authentication schemes.

* [`bearerAuth (OAuth 2 Bearer token)`](https://www.github.com/sdks-io/apimatic-logalty-dotnet-sdk/tree/0.0.1/doc/auth/oauth-2-bearer-token.md)
* [`basicAuth (Basic Authentication)`](https://www.github.com/sdks-io/apimatic-logalty-dotnet-sdk/tree/0.0.1/doc/auth/basic-authentication.md)

## List of APIs

* [Certificate Requests](https://www.github.com/sdks-io/apimatic-logalty-dotnet-sdk/tree/0.0.1/doc/controllers/certificate-requests.md)
* [Authentication](https://www.github.com/sdks-io/apimatic-logalty-dotnet-sdk/tree/0.0.1/doc/controllers/authentication.md)
* [Evidence](https://www.github.com/sdks-io/apimatic-logalty-dotnet-sdk/tree/0.0.1/doc/controllers/evidence.md)
* [Operations](https://www.github.com/sdks-io/apimatic-logalty-dotnet-sdk/tree/0.0.1/doc/controllers/operations.md)

## SDK Infrastructure

### Configuration

* [Configuration-Based Initialization](https://www.github.com/sdks-io/apimatic-logalty-dotnet-sdk/tree/0.0.1/doc/configuration-based-initialization.md)
* [HttpClientConfiguration](https://www.github.com/sdks-io/apimatic-logalty-dotnet-sdk/tree/0.0.1/doc/http-client-configuration.md)
* [HttpClientConfigurationBuilder](https://www.github.com/sdks-io/apimatic-logalty-dotnet-sdk/tree/0.0.1/doc/http-client-configuration-builder.md)
* [LogBuilder](https://www.github.com/sdks-io/apimatic-logalty-dotnet-sdk/tree/0.0.1/doc/log-builder.md)
* [LogRequestBuilder](https://www.github.com/sdks-io/apimatic-logalty-dotnet-sdk/tree/0.0.1/doc/log-request-builder.md)
* [LogResponseBuilder](https://www.github.com/sdks-io/apimatic-logalty-dotnet-sdk/tree/0.0.1/doc/log-response-builder.md)
* [ProxyConfigurationBuilder](https://www.github.com/sdks-io/apimatic-logalty-dotnet-sdk/tree/0.0.1/doc/proxy-configuration-builder.md)

### HTTP

* [HttpCallback](https://www.github.com/sdks-io/apimatic-logalty-dotnet-sdk/tree/0.0.1/doc/http-callback.md)
* [HttpContext](https://www.github.com/sdks-io/apimatic-logalty-dotnet-sdk/tree/0.0.1/doc/http-context.md)
* [HttpRequest](https://www.github.com/sdks-io/apimatic-logalty-dotnet-sdk/tree/0.0.1/doc/http-request.md)
* [HttpResponse](https://www.github.com/sdks-io/apimatic-logalty-dotnet-sdk/tree/0.0.1/doc/http-response.md)
* [HttpStringResponse](https://www.github.com/sdks-io/apimatic-logalty-dotnet-sdk/tree/0.0.1/doc/http-string-response.md)

### Utilities

* [ApiException](https://www.github.com/sdks-io/apimatic-logalty-dotnet-sdk/tree/0.0.1/doc/api-exception.md)
* [ApiResponse](https://www.github.com/sdks-io/apimatic-logalty-dotnet-sdk/tree/0.0.1/doc/api-response.md)
* [ApiHelper](https://www.github.com/sdks-io/apimatic-logalty-dotnet-sdk/tree/0.0.1/doc/api-helper.md)

