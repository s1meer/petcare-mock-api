# petcare-mock-api

Static JSON standing in for a vet clinic's appointments API, used by the
[PetCare](https://github.com/s1meer) Android app's clinic-integration feature.

## Endpoint

```
GET https://raw.githubusercontent.com/s1meer/petcare-mock-api/main/vet_appointments.json
```

## Response shape

```json
[
  {
    "clinicName": "Riverside Veterinary Clinic",
    "appointmentType": "Annual vaccination",
    "dateTimeIso": "2026-10-14T09:30:00Z",
    "notes": "Bring the vaccination card. Fast for 2 hours beforehand."
  }
]
```

| Field | Type | Notes |
|---|---|---|
| `clinicName` | string | Clinic the appointment is with |
| `appointmentType` | string | e.g. Annual vaccination, Dental check |
| `dateTimeIso` | string | ISO-8601, UTC, `yyyy-MM-dd'T'HH:mm:ss'Z'` |
| `notes` | string | Free text, may be absent |

A real clinic would serve this from an authenticated REST endpoint. This file
serves the identical contract over HTTPS so the app's integration feature can be
demonstrated end to end without a partner API.
