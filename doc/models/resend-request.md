
# Resend Request

*This model accepts additional fields of type object.*

## Structure

`ResendRequest`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `Operation` | `string` | Required, Constant | Fixed value `resend`.<br><br>**Value**: `"resend"` |
| `NoticeMethod` | [`NoticeMethod?`](../../doc/models/notice-method.md) | Optional | Notification channel used to give the end-user access to the system:<br><br>- `NONE`: No notification is sent; only a synchronous access URL is returned.<br>- `EMAIL`: An asynchronous access link is sent by e-mail.<br>- `SMS`: An asynchronous access link is sent by SMS. |
| `Contact` | `string` | Optional | Alternative contact information to use instead of the one on the original request.<br><br>- For `EMAIL`: must be a valid e-mail address.<br>- For `SMS`: must be a valid phone number.<br>  If the process has not yet been accessed by the user, the contact on the request is updated. |
| `AdditionalProperties` | `object this[string key]` | Optional | - |

## Example (as JSON)

```json
{
  "operation": "resend",
  "noticeMethod": "NONE",
  "contact": "contact6",
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

