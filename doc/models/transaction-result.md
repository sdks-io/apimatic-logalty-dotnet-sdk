
# Transaction Result

Transaction result:

- `7`: COMPLETED — Process completed and certificate generated.
- `8`: USER_REJECT — End-user rejected the process.
- `9901`: ERROR_SENDING_ACCESS — Error sending the access notification.
- `9910`: ERROR_CERTIFICATE_CONTRACT_SIGNATURE — Error in the signature of the issuance contract.
- `9911`: ERROR_CERTIFICATE_CONTRACT_IDENTIFICATION — Error identifying the user during contract signing.
- `9912`: ERROR_CERTIFICATE_VALIDATION_REJECTED — Validation rejected by the video operator.
- `9913`: ERROR_CERTIFICATE_ISSUING_REJECTED — Issuance rejected by the RA operator.
- `9914`: ERROR_CERTIFICATE_ACTIVATION — Certificate activation error.
- `99906`: TIME_EXPIRED — Transaction closed due to expired time.
- `99908`: OCR_FAILED — OCR validation exceeded.
- `99909`: OCR_FAILED — Maximum number of validation attempts exceeded (permissive).
- `99910`: DNI_WITHOUT_CHIP — DNI does not have chip or is not readable.
- `99915`: TIME_AUTH_EXPIRED — Time for authorization exceeded.
- `99932`: CLOSED_BY_REMITANCE — Transaction cancelled by the customer.
- `99940`: DELETED_BY_SENDER — Reserved status.
- `99945`: ERROR_ID_NUMBER — Error in the identification number.
- `99990`: CLOSED_BY_MAINTENANCE — Reserved status.

## Enumeration

`TransactionResult`

## Fields

| Name |
|  --- |
| `Enum7` |
| `Enum8` |
| `Enum9901` |
| `Enum9910` |
| `Enum9911` |
| `Enum9912` |
| `Enum9913` |
| `Enum9914` |
| `Enum99906` |
| `Enum99908` |
| `Enum99909` |
| `Enum99910` |
| `Enum99915` |
| `Enum99932` |
| `Enum99940` |
| `Enum99945` |
| `Enum99990` |

