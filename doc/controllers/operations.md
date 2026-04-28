# Operations

Perform operations on in-progress transactions

```csharp
OperationsApi operationsApi = client.OperationsApi;
```

## Class Name

`OperationsApi`


# Update Certificate Request

Performs an operation on an in-progress transaction. The `operation` field in the
request body determines the action:

- **`resend`** — Resend the access request to the end-user or generate a new synchronous access URL.
- **`cancel`** — Cancel the transaction. Returns HTTP 204 No Content on success.

```csharp
UpdateCertificateRequestAsync(
    Guid code,
    UpdateRequest body)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `code` | `Guid` | Template, Required | Transaction's unique identifier in Logalty (UUIDv4 format). |
| `body` | [`UpdateRequest`](../../doc/models/containers/update-request.md) | Body, Required | - |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [Models.ResendResponse](../../doc/models/resend-response.md).

## Example Usage

```csharp
Guid code = new Guid("00001962-0000-0000-0000-000000000000");
UpdateRequest body = UpdateRequest.FromResendRequest(
    new ResendRequest
    {
        Operation = "resend",
        NoticeMethod = NoticeMethod.None,
    }
);

try
{
    ApiResponse<ResendResponse> result = await operationsApi.UpdateCertificateRequestAsync(
        code,
        body
    );
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
  "accessUrl": "https://<certy_server>/#/user/cert-request?jwt=<jwt>"
}
```

## Errors

| HTTP Status Code | Error Description | Exception Class |
|  --- | --- | --- |
| 400 | Invalid request. | [`ErrorResponseException`](../../doc/models/error-response-exception.md) |
| 404 | Transaction not found. | [`ErrorResponseException`](../../doc/models/error-response-exception.md) |

