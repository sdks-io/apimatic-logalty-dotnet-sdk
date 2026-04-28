
# Transaction State

Transaction state:

- `0`: CREATED — Transaction created.
- `1`: ACCESS_SENT — Access notification sent.
- `10`: PENDING_CERTIFICATE_CONTRACT_SIGNATURE — Pending signature of the certificate issuance contract.
- `11`: PENDING_CERTIFICATE_VALIDATION — Pending validation by the video operator.
- `12`: CLOSED — Transaction closed.
- `13`: PENDING_CERTIFICATE_ISSUING — Pending issuance by the RA operator.
- `14`: PENDING_CERTIFICATE_ACTIVATION — Pending certificate activation by the end-user.
- `15`: PENDING_CERTIFICATE_DOWNLOAD — Pending certificate download by the end-user (software support only).

## Enumeration

`TransactionState`

## Fields

| Name |
|  --- |
| `Enum0` |
| `Enum1` |
| `Enum10` |
| `Enum11` |
| `Enum12` |
| `Enum13` |
| `Enum14` |
| `Enum15` |

