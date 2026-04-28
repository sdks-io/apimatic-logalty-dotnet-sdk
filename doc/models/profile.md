
# Profile

*This model accepts additional fields of type object.*

## Structure

`Profile`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `Idtype` | [`IdType?`](../../doc/models/id-type.md) | Optional | **Default**: `IdType.IDC` |
| `Idcountry` | `string` | Optional | Issuing country of the document, coded according to ISO 3166-1. Default is `EN`.<br><br>**Default**: `"EN"` |
| `Idnumber` | `string` | Optional | Identity document number. |
| `Name` | `string` | Required | End-user's given name. |
| `Surname1` | `string` | Optional | End-user's first family name. |
| `Surname2` | `string` | Optional | End-user's second family name. |
| `Phone` | `string` | Required | End-user's telephone number. Required for SMS notifications. |
| `Email` | `string` | Optional | End-user's e-mail address. Required for e-mail notifications. |
| `Validation` | [`List<ValidationRule>`](../../doc/models/validation-rule.md) | Optional | Additional validations to perform on the user's data. |
| `AdditionalProperties` | `object this[string key]` | Optional | - |

## Example (as JSON)

```json
{
  "idtype": "IDC",
  "idcountry": "ES",
  "name": "name8",
  "phone": "+34666112233",
  "email": "pruebas@logalty.com",
  "idnumber": "idnumber6",
  "surname1": "surname14",
  "surname2": "surname26",
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

