
# Validation Rule

*This model accepts additional fields of type object.*

## Structure

`ValidationRule`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `Condition` | [`ValidationCondition`](../../doc/models/validation-condition.md) | Required | Condition to apply when validating an OCR attribute. |
| `FieldName` | [`ValidatableAttribute`](../../doc/models/validatable-attribute.md) | Required | OCR attribute name that can be used as a validation target. |
| `MValue` | `string` | Required | Expected value. For lists, separate values with a comma (e.g. `BRA,PTR`). |
| `AdditionalProperties` | `object this[string key]` | Optional | - |

## Example (as JSON)

```json
{
  "condition": "NOT_IN",
  "fieldName": "BIRTHPLACE",
  "value": "value0",
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

