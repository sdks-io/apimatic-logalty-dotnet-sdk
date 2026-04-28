
# Cancel Request

*This model accepts additional fields of type object.*

## Structure

`CancelRequest`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `Operation` | `string` | Required, Constant | Fixed value `cancel`.<br><br>**Value**: `"cancel"` |
| `AdditionalProperties` | `object this[string key]` | Optional | - |

## Example (as JSON)

```json
{
  "operation": "cancel",
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

