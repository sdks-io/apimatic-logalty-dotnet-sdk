
# Client Class Documentation

The following parameters are configurable for the API Client:

| Parameter | Type | Description |
|  --- | --- | --- |
| CertyServer | `string` | Hostname of the Certy API server<br>*Default*: `"certy_server"` |
| Oauth2Server | `string` | Hostname of the OAuth2 server<br>*Default*: `"oauth2_server"` |
| Environment | [`Environment`](../README.md#environments) | The API environment. <br> **Default: `Environment.Production`** |
| Timeout | `TimeSpan` | Http client timeout.<br>*Default*: `TimeSpan.FromSeconds(30)` |
| HttpClientConfiguration | [`Action<HttpClientConfiguration.Builder>`](../doc/http-client-configuration-builder.md) | Action delegate that configures the HTTP client by using the HttpClientConfiguration.Builder for customizing API call settings.<br>*Default*: `new HttpClient()` |
| LogBuilder | [`LogBuilder`](../doc/log-builder.md) | Represents the logging configuration builder for API calls |
| BearerAuthCredentials | [`BearerAuthCredentials`](auth/oauth-2-bearer-token.md) | The Credentials Setter for OAuth 2 Bearer token |
| BasicAuthCredentials | [`BasicAuthCredentials`](auth/basic-authentication.md) | The Credentials Setter for Basic Authentication |

The API client can be initialized as follows:

## Code-Based Initialization

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

## Configuration-Based Initialization

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

See the [Configuration-Based Initialization](../doc/configuration-based-initialization.md) section for details.

## Logalty Certificate Issuance API (Certy)Client Class

The gateway for the SDK. This class acts as a factory for the Apis and also holds the configuration of the SDK.

### Controllers

| Name | Description |
|  --- | --- |
| AuthenticationApi | Gets AuthenticationApi. |
| CertificateRequestsApi | Gets CertificateRequestsApi. |
| EvidenceApi | Gets EvidenceApi. |
| OperationsApi | Gets OperationsApi. |

### Properties

| Name | Description | Type |
|  --- | --- | --- |
| HttpClientConfiguration | Gets the configuration of the Http Client associated with this client. | [`IHttpClientConfiguration`](../doc/http-client-configuration.md) |
| Timeout | Http client timeout. | `TimeSpan` |
| Environment | Current API environment. | `Environment` |
| CertyServer | Hostname of the Certy API server | `string` |
| Oauth2Server | Hostname of the OAuth2 server | `string` |
| BearerAuthCredentials | Gets the credentials to use with BearerAuth. | [`IBearerAuthCredentials`](auth/oauth-2-bearer-token.md) |
| BasicAuthCredentials | Gets the credentials to use with BasicAuth. | [`IBasicAuthCredentials`](auth/basic-authentication.md) |

### Methods

| Name | Description | Return Type |
|  --- | --- | --- |
| `GetBaseUri(Server alias = Server.Default)` | Gets the URL for a particular alias in the current environment and appends it with template parameters. | `string` |
| `ToBuilder()` | Creates an object of the Logalty Certificate Issuance API (Certy)Client using the values provided for the builder. | `Builder` |

## Logalty Certificate Issuance API (Certy)Client Builder Class

Class to build instances of Logalty Certificate Issuance API (Certy)Client.

### Methods

| Name | Description | Return Type |
|  --- | --- | --- |
| `HttpClientConfiguration(Action<`[`HttpClientConfiguration.Builder`](../doc/http-client-configuration-builder.md)`> action)` | Gets the configuration of the Http Client associated with this client. | `Builder` |
| `Timeout(TimeSpan timeout)` | Http client timeout. | `Builder` |
| `Environment(Environment environment)` | Current API environment. | `Builder` |
| `CertyServer(string certyServer)` | Hostname of the Certy API server | `Builder` |
| `Oauth2Server(string oauth2Server)` | Hostname of the OAuth2 server | `Builder` |
| `BearerAuthCredentials(Action<BearerAuthModel.Builder> action)` | Sets credentials for BearerAuth. | `Builder` |
| `BasicAuthCredentials(Action<BasicAuthModel.Builder> action)` | Sets credentials for BasicAuth. | `Builder` |

