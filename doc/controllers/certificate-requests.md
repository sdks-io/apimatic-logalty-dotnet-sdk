# Certificate Requests

```csharp
CertificateRequestsApi certificateRequestsApi = client.CertificateRequestsApi;
```

## Class Name

`CertificateRequestsApi`

## Methods

* [Create Certificate Request](../../doc/controllers/certificate-requests.md#create-certificate-request)
* [Get Certificate Request by Code](../../doc/controllers/certificate-requests.md#get-certificate-request-by-code)
* [Get Certificate Request by External Id](../../doc/controllers/certificate-requests.md#get-certificate-request-by-external-id)


# Create Certificate Request

Registers a new certificate issuance request for an end-user.

A synchronous access URL (`accessUrl`) is always returned in the response.
An asynchronous access link is also generated and sent to the end-user when
`noticeMethod` is set to `EMAIL` or `SMS`.

```csharp
CreateCertificateRequestAsync(
    Models.TransactionRequest body)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `body` | [`TransactionRequest`](../../doc/models/transaction-request.md) | Body, Required | - |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [Models.TransactionResponse](../../doc/models/transaction-response.md).

## Example Usage

```csharp
TransactionRequest body = new TransactionRequest
{
    IdModel = CertificateModel.Personalhsmfortressqes,
    ProfileData = new Profile
    {
        Name = "Antonio",
        Phone = "+34666112233",
        Idnumber = "11111111H",
        Surname1 = "García",
        Surname2 = "González",
        Email = "pruebas@logalty.com",
    },
    DurationData = new Duration
    {
        CsrDuration = "3",
    },
};

try
{
    ApiResponse<TransactionResponse> result = await certificateRequestsApi.CreateCertificateRequestAsync(body);
}
catch (ApiException e)
{
    Console.WriteLine(e.Message);
    if (e is ErrorResponseException)
    {
       // TODO: Handle ErrorResponseException exception here
    }
}
```

## Example Response *(as JSON)*

```json
{
  "code": "<uuid>",
  "accessUrl": "https://<certy_server>/#/user/cert-request?jwt=<jwt>",
  "certId": "<certId>"
}
```

## Errors

| HTTP Status Code | Error Description | Exception Class |
|  --- | --- | --- |
| 400 | Invalid request parameters. | [`ErrorResponseException`](../../doc/models/error-response-exception.md) |


# Get Certificate Request by Code

Returns the status and details of a certificate issuance transaction by its UUID.

```csharp
GetCertificateRequestByCodeAsync(
    Guid code)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `code` | `Guid` | Template, Required | Transaction's unique identifier in Logalty (UUIDv4 format). |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [Models.TransactionStatus](../../doc/models/transaction-status.md).

## Example Usage

```csharp
Guid code = new Guid("00001962-0000-0000-0000-000000000000");
try
{
    ApiResponse<TransactionStatus> result = await certificateRequestsApi.GetCertificateRequestByCodeAsync(code);
}
catch (ApiException e)
{
    Console.WriteLine(e.Message);
    if (e is ErrorResponseException)
    {
       // TODO: Handle ErrorResponseException exception here
    }
}
```

## Errors

| HTTP Status Code | Error Description | Exception Class |
|  --- | --- | --- |
| 404 | Transaction not found. | [`ErrorResponseException`](../../doc/models/error-response-exception.md) |


# Get Certificate Request by External Id

Returns a list of certificate issuance transactions matching the provided external identifier.
Multiple transactions may share the same `externalId` if registered with the `duplicateKeyOff` flag.

```csharp
GetCertificateRequestByExternalIdAsync(
    string externalId)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `externalId` | `string` | Template, Required | Unique identifier in the client system external to Logalty. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [List<Models.TransactionStatus>](../../doc/models/transaction-status.md).

## Example Usage

```csharp
string externalId = "external-id2";
try
{
    ApiResponse<List<TransactionStatus>> result = await certificateRequestsApi.GetCertificateRequestByExternalIdAsync(externalId);
}
catch (ApiException e)
{
    Console.WriteLine(e.Message);
}
```

