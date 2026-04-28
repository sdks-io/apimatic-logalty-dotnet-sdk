# Authentication

OAuth2 token endpoint

```csharp
AuthenticationApi authenticationApi = client.AuthenticationApi;
```

## Class Name

`AuthenticationApi`


# Get Token

Authenticate using the OAuth2 `client_credentials` grant to obtain a Bearer token.
Credentials must be Base64-encoded as `Base64(<client_id>:<client_secret>)` and passed
in the `Authorization` header.

```csharp
GetTokenAsync(
    Models.GrantType grantType,
    Models.OauthScope scope)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `grantType` | [`GrantType`](../../doc/models/grant-type.md) | Form, Required | OAuth2 grant type. Fixed value `client_credentials`. |
| `scope` | [`OauthScope`](../../doc/models/oauth-scope.md) | Form, Required | OAuth2 scope for certificate issuance. Fixed value `certy/certificate-request`. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [Models.TokenResponse](../../doc/models/token-response.md).

## Example Usage

```csharp
GrantType grantType = GrantType.ClientCredentials;
OauthScope scope = OauthScope.EnumCertycertificaterequest;
try
{
    ApiResponse<TokenResponse> result = await authenticationApi.GetTokenAsync(
        grantType,
        scope
    );
}
catch (ApiException e)
{
    Console.WriteLine(e.Message);
}
```

## Example Response *(as JSON)*

```json
{
  "access_token": "<jwt>",
  "expires_in": 3600,
  "token_type": "Bearer"
}
```

