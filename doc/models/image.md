
# Image

*This model accepts additional fields of type object.*

## Structure

`Image`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `Type` | [`ImageType?`](../../doc/models/image-type.md) | Optional | Image type:<br><br>- `DNI_NIE`: Front of the ID card.<br>- `DNI_NIE_BACK`: Back of the ID card.<br>- `PASSPORT`: Passport image.<br>- `DRIVER_LICENSE`: Driver's license image.<br>- `SELFIE`: Selfie.<br>- `SELFIE_LIFE`: Selfie with liveness proof.<br>- `PHOTOCUT`: Cropped face image from the document.<br>- `SIGNATURE`: Cropped handwritten signature from the document.<br>- `FINGERPRINT`: Cropped fingerprint image from the document. |
| `ContentType` | `string` | Optional | MIME type of the image (e.g. `image/jpg`, `image/png`). |
| `Content` | `string` | Optional | Image content encoded in Base64. |
| `Hash` | `string` | Optional | Hash of the image content. |
| `AdditionalProperties` | `object this[string key]` | Optional | - |

## Example (as JSON)

```json
{
  "type": "PASSPORT",
  "contentType": "contentType2",
  "content": "content0",
  "hash": "hash2",
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

