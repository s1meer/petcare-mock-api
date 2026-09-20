# petcare-mock-api

Static JSON standing in for a vet clinic's appointments API, used by the
[PetCare](https://github.com/s1meer) Android app's clinic-integration feature.

## Endpoints

Two feeds, identical contract, picked by the source toggle on the app's
Integration screen. Both import into the same HEALTHCARE / IMPORTED care tasks.

```
GET https://raw.githubusercontent.com/s1meer/petcare-mock-api/main/vet_appointments.json     # Global
GET https://raw.githubusercontent.com/s1meer/petcare-mock-api/main/vet_appointments_np.json  # Nepal
```

## Response shape

```json
[
  {
    "clinicName": "Baneshwor Pet Care Centre",
    "appointmentType": "Rabies vaccination",
    "dateTimeIso": "2026-10-09T04:15:00Z",
    "notes": "Bring the vaccination card.",
    "clinicAddress": "142 Baneshwor Height Road, New Baneshwor, Kathmandu 44600",
    "latitude": 27.6893,
    "longitude": 85.3436
  }
]
```

| Field | Type | Notes |
|---|---|---|
| `clinicName` | string | Clinic the appointment is with |
| `appointmentType` | string | e.g. Annual vaccination, Dental check |
| `dateTimeIso` | string | ISO-8601, UTC, `yyyy-MM-dd'T'HH:mm:ss'Z'` |
| `notes` | string | Free text, may be absent |
| `clinicAddress` | string | Optional. Postal address of the clinic |
| `latitude` | number | Optional. WGS-84 decimal degrees |
| `longitude` | number | Optional. WGS-84 decimal degrees |

The three location fields are absent from the Global feed and present on the
Nepal one, which is what exercises the app's "no coordinates, no map" path.
`0, 0` is treated by the app as "no location", not as Null Island.

## The Nepal feed

Five entries in real Kathmandu Valley and Pokhara neighbourhoods - Baneshwor,
Lazimpat, Thamel, Lakeside and Jhamsikhel. The clinic names and street numbers
are invented; the coordinates are approximate real positions for those
neighbourhoods, so the app's static map preview lands in the right place.

A real clinic would serve this from an authenticated REST endpoint. These files
serve the identical contract over HTTPS so the app's integration feature can be
demonstrated end to end without a partner API.
