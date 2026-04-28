
# Support

*This model accepts additional fields of type object.*

## Structure

`Support`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `Password` | `string` | Optional | Password for certificate download. Must be alphanumeric and at most 8 characters.<br>Mandatory only for certificates with software support.<br><br>**Constraints**: *Maximum Length*: `8` |
| `AdditionalProperties` | `object this[string key]` | Optional | - |

## Example (as JSON)

```json
{
  "password": "12345678",
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

