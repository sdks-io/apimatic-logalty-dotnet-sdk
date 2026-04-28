
# Ocr Validation Item

*This model accepts additional fields of type object.*

## Structure

`OcrValidationItem`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `Code` | `string` | Optional | Validation test identifier (e.g. `TEST_FACE_RECOGNITION_RATIO`). |
| `Blocker` | `bool?` | Optional | Whether a failing result for this test blocks the issuance process. |
| `Condition` | `string` | Optional | Threshold condition applied. |
| `Result` | `string` | Optional | Validation outcome (e.g. `OK`). |
| `MValue` | `double?` | Optional | Threshold value used for the validation. |
| `AdditionalProperties` | `object this[string key]` | Optional | - |

## Example (as JSON)

```json
{
  "code": "code4",
  "blocker": false,
  "condition": "condition0",
  "result": "result0",
  "value": 203.18,
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

