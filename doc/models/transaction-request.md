
# Transaction Request

*This model accepts additional fields of type object.*

## Structure

`TransactionRequest`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `IdModel` | [`CertificateModel`](../../doc/models/certificate-model.md) | Required | Certificate model:<br><br>- `personal-hsm-fortress-qes`: Qualified personal certificate (QES) hosted in the cloud (FirmaCloud).<br>- `personal-sw`: Qualified personal certificate (AES) in software support.<br>- `personal-sw-identity`: Qualified personal certificate (AES) hosted in the cloud (FirmaCloud).<br>- `personal-sw-identity-sc`: Qualified personal certificate (AES) hosted in Client System (SC) in cloud. Does not require end-user activation. |
| `ProfileData` | [`Profile`](../../doc/models/profile.md) | Required | - |
| `DurationData` | [`Duration`](../../doc/models/duration.md) | Optional | - |
| `SupportData` | [`Support`](../../doc/models/support.md) | Optional | - |
| `ExternalId` | `string` | Optional | Unique identifier in the client system external to Logalty. Can be used to search transactions. |
| `DuplicateKeyOff` | `bool?` | Optional | When combined with `externalId`, allows two transactions with the same external identifier<br>to be registered. By default the external identifier is unique and duplicate use is not allowed.<br><br>**Default**: `false` |
| `UrlBack` | `string` | Optional | Redirect URL where the end-user will be redirected after process completion (GET method).<br>The following query parameters are appended automatically:<br><br>- `code`: Unique transaction identifier in Logalty.<br>- `externalid`: External identifier (URL-encoded), if provided.<br>- `process`: `issuing` (certificate issuance flow) or `activation` (certificate activation flow).<br>- `status`: `ok`, `cancelled`, `error`, or `exit`. |
| `NoticeMethod` | [`NoticeMethod?`](../../doc/models/notice-method.md) | Optional | Notification channel used to give the end-user access to the system:<br><br>- `NONE`: No notification is sent; only a synchronous access URL is returned.<br>- `EMAIL`: An asynchronous access link is sent by e-mail.<br>- `SMS`: An asynchronous access link is sent by SMS. |
| `Time2Close` | `string` | Optional | Validity period of the transaction. Accepts a numeric value followed by a unit:<br>`m` (minutes), `h` (hours), `d` (days). After this period the transaction is<br>automatically closed with result `TIME_EXPIRED`. Default: `30d`.<br><br>**Default**: `"30d"` |
| `Locale` | `string` | Optional | Language of the transaction in IETF format. Default is `es-ES`.<br><br>**Default**: `"es-ES"` |
| `AdditionalProperties` | `object this[string key]` | Optional | - |

## Example (as JSON)

```json
{
  "idModel": "personal-hsm-fortress-qes",
  "profileData": {
    "idtype": "IDC",
    "idcountry": "ES",
    "name": "name8",
    "phone": "+34666112233",
    "email": "pruebas@logalty.com",
    "idnumber": "idnumber4",
    "surname1": "surname14",
    "surname2": "surname24",
    "exampleAdditionalProperty": {
      "key1": "val1",
      "key2": "val2"
    }
  },
  "duplicateKeyOff": false,
  "time2close": "30d",
  "locale": "es-ES",
  "durationData": {
    "csrDuration": "csrDuration8",
    "exampleAdditionalProperty": {
      "key1": "val1",
      "key2": "val2"
    }
  },
  "supportData": {
    "password": "password2",
    "exampleAdditionalProperty": {
      "key1": "val1",
      "key2": "val2"
    }
  },
  "externalId": "externalId2",
  "urlBack": "urlBack4",
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

