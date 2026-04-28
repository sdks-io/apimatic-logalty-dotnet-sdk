# Evidence

Download evidences associated with a transaction (images, video, OCR)

```csharp
EvidenceApi evidenceApi = client.EvidenceApi;
```

## Class Name

`EvidenceApi`

## Methods

* [Download Images](../../doc/controllers/evidence.md#download-images)
* [Get Video Link](../../doc/controllers/evidence.md#get-video-link)
* [Get Ocr](../../doc/controllers/evidence.md#get-ocr)


# Download Images

Returns a list of images captured during the certificate issuance process.

```csharp
DownloadImagesAsync(
    Guid code)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `code` | `Guid` | Template, Required | Transaction's unique identifier in Logalty (UUIDv4 format). |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [List<Models.Image>](../../doc/models/image.md).

## Example Usage

```csharp
Guid code = new Guid("00001962-0000-0000-0000-000000000000");
try
{
    ApiResponse<List<Image>> result = await evidenceApi.DownloadImagesAsync(code);
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
[
  {
    "type": "DNI_NIE",
    "contentType": "image/jpg",
    "content": "<contentB64>",
    "hash": "<hash>"
  },
  {
    "type": "DNI_NIE_BACK",
    "contentType": "image/jpg",
    "content": "<contentB64>",
    "hash": "<hash>"
  },
  {
    "type": "PHOTOCUT",
    "contentType": "image/png",
    "content": "<contentB64>",
    "hash": "<hash>"
  },
  {
    "type": "SIGNATURE",
    "contentType": "image/png",
    "content": "<contentB64>",
    "hash": "<hash>"
  },
  {
    "type": "SELFIE",
    "contentType": "image/jpg",
    "content": "<contentB64>",
    "hash": "<hash>"
  }
]
```

## Errors

| HTTP Status Code | Error Description | Exception Class |
|  --- | --- | --- |
| 404 | Transaction not found. | [`ErrorResponseException`](../../doc/models/error-response-exception.md) |


# Get Video Link

```csharp
GetVideoLinkAsync(
    Guid code)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `code` | `Guid` | Template, Required | Transaction's unique identifier in Logalty (UUIDv4 format). |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [Models.VideoResponse](../../doc/models/video-response.md).

## Example Usage

```csharp
Guid code = new Guid("00001962-0000-0000-0000-000000000000");
try
{
    ApiResponse<VideoResponse> result = await evidenceApi.GetVideoLinkAsync(code);
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
  "url": "<video_url>"
}
```

## Errors

| HTTP Status Code | Error Description | Exception Class |
|  --- | --- | --- |
| 404 | Transaction not found. | [`ErrorResponseException`](../../doc/models/error-response-exception.md) |


# Get Ocr

Returns data extracted from the identity document along with validation results.

```csharp
GetOcrAsync(
    Guid code)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `code` | `Guid` | Template, Required | Transaction's unique identifier in Logalty (UUIDv4 format). |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `Data` property of this instance returns the response data which is of type [Models.OcrResponse](../../doc/models/ocr-response.md).

## Example Usage

```csharp
Guid code = new Guid("00001962-0000-0000-0000-000000000000");
try
{
    ApiResponse<OcrResponse> result = await evidenceApi.GetOcrAsync(code);
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

