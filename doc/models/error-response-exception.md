
# Error Response Exception

*This model accepts additional fields of type object.*

## Structure

`ErrorResponseException`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `Error` | `string` | Optional | Identification code of the error type. |
| `MessageProperty` | `string` | Optional | Short, human-readable error message. |
| `Detail` | `string` | Optional | Detailed explanation of the error and/or suggested correction. |
| `AdditionalProperties` | `object this[string key]` | Optional | - |

## Example (as JSON)

```json
{
  "error": "INVALID_PARAM_PASSWORD",
  "message": "Invalid supportData.password parameter",
  "detail": "The password must be alphanumeric and no longer than 8 characters",
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

