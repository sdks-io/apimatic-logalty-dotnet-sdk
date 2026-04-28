
# Transaction Response

*This model accepts additional fields of type object.*

## Structure

`TransactionResponse`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `Code` | `Guid?` | Optional | Unique identifier of the transaction in Logalty (UUIDv4 format). |
| `AccessUrl` | `string` | Optional | Synchronous URL to redirect the end-user to the issuing process. |
| `CertId` | `string` | Optional | Unique identifier of the certificate in Logalty. |
| `AdditionalProperties` | `object this[string key]` | Optional | - |

## Example (as JSON)

```json
{
  "code": "00002470-0000-0000-0000-000000000000",
  "accessUrl": "accessUrl0",
  "certId": "certId2",
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

