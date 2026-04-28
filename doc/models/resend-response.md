
# Resend Response

*This model accepts additional fields of type object.*

## Structure

`ResendResponse`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `AccessUrl` | `string` | Optional | Synchronous URL to redirect the end-user to the issuing process. |
| `AdditionalProperties` | `object this[string key]` | Optional | - |

## Example (as JSON)

```json
{
  "accessUrl": "accessUrl2",
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

