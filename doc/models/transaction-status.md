
# Transaction Status

*This model accepts additional fields of type object.*

## Structure

`TransactionStatus`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `Code` | `Guid?` | Optional | Transaction's unique identifier in Logalty (UUIDv4 format). |
| `CertId` | `string` | Optional | Unique certificate identifier in Logalty. |
| `Created` | `long?` | Optional | Transaction creation date in epoch (milliseconds) format. |
| `ProfileData` | [`Profile`](../../doc/models/profile.md) | Optional | - |
| `ExternalId` | `string` | Optional | Unique identifier in the client system external to Logalty. |
| `State` | [`TransactionState?`](../../doc/models/transaction-state.md) | Optional | Transaction state:<br><br>- `0`: CREATED — Transaction created.<br>- `1`: ACCESS_SENT — Access notification sent.<br>- `10`: PENDING_CERTIFICATE_CONTRACT_SIGNATURE — Pending signature of the certificate issuance contract.<br>- `11`: PENDING_CERTIFICATE_VALIDATION — Pending validation by the video operator.<br>- `12`: CLOSED — Transaction closed.<br>- `13`: PENDING_CERTIFICATE_ISSUING — Pending issuance by the RA operator.<br>- `14`: PENDING_CERTIFICATE_ACTIVATION — Pending certificate activation by the end-user.<br>- `15`: PENDING_CERTIFICATE_DOWNLOAD — Pending certificate download by the end-user (software support only). |
| `StateDate` | `long?` | Optional | Date of last status change in epoch format. |
| `Result` | [`TransactionResult?`](../../doc/models/transaction-result.md) | Optional | Transaction result:<br><br>- `7`: COMPLETED — Process completed and certificate generated.<br>- `8`: USER_REJECT — End-user rejected the process.<br>- `9901`: ERROR_SENDING_ACCESS — Error sending the access notification.<br>- `9910`: ERROR_CERTIFICATE_CONTRACT_SIGNATURE — Error in the signature of the issuance contract.<br>- `9911`: ERROR_CERTIFICATE_CONTRACT_IDENTIFICATION — Error identifying the user during contract signing.<br>- `9912`: ERROR_CERTIFICATE_VALIDATION_REJECTED — Validation rejected by the video operator.<br>- `9913`: ERROR_CERTIFICATE_ISSUING_REJECTED — Issuance rejected by the RA operator.<br>- `9914`: ERROR_CERTIFICATE_ACTIVATION — Certificate activation error.<br>- `99906`: TIME_EXPIRED — Transaction closed due to expired time.<br>- `99908`: OCR_FAILED — OCR validation exceeded.<br>- `99909`: OCR_FAILED — Maximum number of validation attempts exceeded (permissive).<br>- `99910`: DNI_WITHOUT_CHIP — DNI does not have chip or is not readable.<br>- `99915`: TIME_AUTH_EXPIRED — Time for authorization exceeded.<br>- `99932`: CLOSED_BY_REMITANCE — Transaction cancelled by the customer.<br>- `99940`: DELETED_BY_SENDER — Reserved status.<br>- `99945`: ERROR_ID_NUMBER — Error in the identification number.<br>- `99990`: CLOSED_BY_MAINTENANCE — Reserved status. |
| `ResultDate` | `long?` | Optional | Result date in epoch format. |
| `CoreCancelCode` | [`CancellationCode?`](../../doc/models/cancellation-code.md) | Optional | Cancellation code provided by the end-user:<br><br>- `OPTION_ZERO`: No reason indicated.<br>- `USER_MOBILE_CHANGED`: User changed their phone number.<br>- `SMS_NOT_RECEIVED`: User did not receive the SMS.<br>- `USER_NO_TOKENS_AVAILABLE`: User does not have a cell phone.<br>- `TECHNICAL_PROBLEMS`: Technical problems reported by the user.<br>- `RCPT_INVALID`: Transaction not directed at the user.<br>- `SENDER_UNKNOWN`: User does not know the sender.<br>- `USER_DATA_INVALID`: User data is incorrect.<br>- `DOCUMENT_DATA_INVALID`: Documentation is incorrect.<br>- `OTHER_REASONS`: Other problems.<br>- `NOT_DOCUMENT_AGREE`: User does not agree with the documentation. |
| `CoreCancelReason` | `string` | Optional | Free-text reason for cancellation. |
| `ActivationUrl` | `string` | Optional | URL to access the certificate activation process. |
| `AdditionalProperties` | `object this[string key]` | Optional | - |

## Example (as JSON)

```json
{
  "code": "00002130-0000-0000-0000-000000000000",
  "certId": "certId6",
  "created": 226,
  "profileData": {
    "idtype": "TIN",
    "idcountry": "idcountry4",
    "idnumber": "idnumber4",
    "name": "name8",
    "surname1": "surname14",
    "surname2": "surname24",
    "phone": "phone2",
    "exampleAdditionalProperty": {
      "key1": "val1",
      "key2": "val2"
    }
  },
  "externalId": "externalId4",
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

