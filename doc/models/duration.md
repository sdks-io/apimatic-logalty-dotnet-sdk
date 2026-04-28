
# Duration

*This model accepts additional fields of type object.*

## Structure

`Duration`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `CsrDuration` | `string` | Optional | Validity time of the certificate. Accepts a numeric value followed by a unit suffix:<br>`h` (hours), `d` (days), `y` (years). If no unit is specified, `y` is assumed.<br>Default is `3y` (3 years). |
| `AdditionalProperties` | `object this[string key]` | Optional | - |

## Example (as JSON)

```json
{
  "csrDuration": "3y",
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

