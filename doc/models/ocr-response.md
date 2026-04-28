
# Ocr Response

*This model accepts additional fields of type object.*

## Structure

`OcrResponse`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `Result` | [`List<OcrResultItem>`](../../doc/models/ocr-result-item.md) | Optional | Structured data extracted from the identity document. |
| `Validation` | [`List<OcrValidationItem>`](../../doc/models/ocr-validation-item.md) | Optional | Validation tests applied to the extracted data. |
| `AdditionalProperties` | `object this[string key]` | Optional | - |

## Example (as JSON)

```json
{
  "result": [
    {
      "code": "code4",
      "type": "type4",
      "value": "value8",
      "exampleAdditionalProperty": {
        "key1": "val1",
        "key2": "val2"
      }
    },
    {
      "code": "code4",
      "type": "type4",
      "value": "value8",
      "exampleAdditionalProperty": {
        "key1": "val1",
        "key2": "val2"
      }
    },
    {
      "code": "code4",
      "type": "type4",
      "value": "value8",
      "exampleAdditionalProperty": {
        "key1": "val1",
        "key2": "val2"
      }
    }
  ],
  "validation": [
    {
      "code": "code6",
      "blocker": false,
      "condition": "condition8",
      "result": "result8",
      "value": 116.6,
      "exampleAdditionalProperty": {
        "key1": "val1",
        "key2": "val2"
      }
    }
  ],
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

