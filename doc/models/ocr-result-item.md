
# Ocr Result Item

*This model accepts additional fields of type object.*

## Structure

`OcrResultItem`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `Code` | `string` | Optional | OCR field identifier (e.g. `NAME`, `ID_NUMBER`, `EXPIRY`). |
| `Type` | `string` | Optional | Field category (e.g. `Normal`, `Validation`). |
| `MValue` | `string` | Optional | Extracted field value. |
| `AdditionalProperties` | `object this[string key]` | Optional | - |

## Example (as JSON)

```json
{
  "code": "code2",
  "type": "type4",
  "value": "value6",
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

