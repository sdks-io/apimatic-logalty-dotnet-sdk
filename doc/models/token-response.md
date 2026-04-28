
# Token Response

*This model accepts additional fields of type object.*

## Structure

`TokenResponse`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `AccessToken` | `string` | Optional | Access token in JWT format. |
| `ExpiresIn` | `int?` | Optional | Token expiry time in seconds. Default is 3600 (1 hour). |
| `TokenType` | [`TokenType?`](../../doc/models/token-type.md) | Optional | Fixed value `Bearer`. |
| `AdditionalProperties` | `object this[string key]` | Optional | - |

## Example (as JSON)

```json
{
  "expires_in": 3600,
  "access_token": "access_token4",
  "token_type": "Bearer",
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

