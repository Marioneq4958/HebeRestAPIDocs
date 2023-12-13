# Pobieranie uczniów

Po zarejestrowaniu certyfikatu można pobrać listę uczniów przypisanych do certyfikatu.

```http
GET /api/mobile/register/hebe
```

## Potrzebne dane
- Zarejestrowany ceryfikat ([Jak zarejestrować certyfikat?](./rejestrowanie_certyfikatu.md))
- Adres Rest API (tan sam, który był używany podczas rejestracji certyfikatu)


## Przykładowe żądanie

```http
GET http://api.fakelog.cf/powiatwulkanowy/api/mobile/register/hebe

vOS: Android
vDeviceModel: WulkanowyPhone
vAPI: 1
VDate: Tue, 1 Jan 1970 00:00:00 GMT
vCanonicalUrl: api%2fmobile%2fregister%2fnew
Signature: keyId="XYZ",headers="vCanonicalUrl Digest vDate" algorithm="sha256withrsa",signature=Base64(SHA256withRSA(XYZ==))
```

## Parametry

### [Nagłówki](./wysylanie_zadania.md#nagłówki)

### Query

- `mode` _domyślnie `1`, zalecane `2`_

- `lastSyncDate` _opcjonaly_\
  Ostatnia data synchronizacji w formacie `yyyy-MM-dd  HH:mm:ss`

#### Porównanie `mode` _1_ i _2_

| Pole w odpowiedzi | Mode 1                                            | Mode 2                                                                  |
| ----------------- | ------------------------------------------------- | ----------------------------------------------------------------------- |
| `EducatorList`    | Zwraca `null`                                     | Zwraca listę skrzynek wychowawców oddziału dla nowego modułu wiadomości |
| `SenderEntry`     | Zwraca dane nadawcy dla starego modułu wiadomości | Zwraca `null`                                                           |

## Przykładowa odpowiedź

```http
{
  "Envelope": [
    {
      "TopLevelPartition": "powiatwulkanowy",
      "Partition": "powiatwulkanowy-005454",
      "Links": {
        "Group": "powiatwulkanowy",
        "Symbol": "005454",
        "Alias": null,
        "QuestionnaireRoot": "http://uonetplus-ankietyplus.fakelog.cf"
      },
      "ClassDisplay": "1A",
      "InfoDisplay": "PS1 - A1",
      "FullSync": false,
      "SenderEntry": {
        "Address": "Jan Kowalski - uczeń 1A (PS1)",
        "AddressHash": "<hash>",
        "Initials": "JK",
        "LoginId": 1
      },
      "Login": {
        "Id": 1,
        "Value": "jan@fakelog.cf",
        "FirstName": "Jan",
        "SecondName": "Marek",
        "Surname": "Kowalski",
        "DisplayName": "Jan Marek Kowalski",
        "LoginRole": "Uczen"
      },
      "Unit": {
        "Id": 1,
        "Symbol": "005454",
        "Short": "PS1",
        "RestURL": "http://api.fakelog.cf/powiatwulkanowy/005454/api",
        "Name": "Publiczna Szkoła nr 1",
        "Address": "ul. Wulkanowa 1, 00-000 Powiat wulkanowy",
        "Patron": "Wulkan",
        "DisplayName": "Publiczna Szkoła nr 1 im. Wulkana",
        "SchoolTopic": "00000000-0000-0000-0000-000000000000"
      },
      "ConstituentUnit": {
        "Id": 1,
        "Short": "PS1",
        "Name": "Publiczna Szkoła nr 1",
        "Address": "ul. Wulkanowa 1, 00-000 Powiat wulkanowy",
        "Patron": "Wulkan",
        "SchoolTopic": "00000000-0000-0000-0000-000000000000"
      },
      "Capabilities": ["REGULAR", "AVG_ENABLED", "LESSONS_VISIBLE", "PLANNED_VISIBLE"],
      "Educators": [
        {
          "Id": "e-1",
          "LoginId": 1,
          "Name": "Joanna",
          "Surname": "Kowalewska",
          "Initials": "JK",
          "Roles": [
            {
              "RoleName": "Wychowawca",
              "RoleOrder": 0,
              "Address": "Kowalewska Joanna [JK] - wychowawca 1A (PS1)",
              "AddressHash": "<hash>",
              "UnitSymbol": null,
              "ConstituentUnitSymbol": "PS1",
              "ClassSymbol": "1A (PS1)",
              "Name": "Joanna",
              "Surname": "Kowalewska",
              "Initials": "JK"
            }
          ]
        }
      ],
      "EducatorList": [
        {
          "GlobalKey": "00000000-0000-0000-0000-000000000000",
          "Name": "Joanna Kowalewska",
          "Group": null
        }
      ],
      "Pupil": {
        "Id": 1,
        "LoginId": 1,
        "LoginValue": "jan@fakelog.cf",
        "FirstName": "Jan",
        "SecondName": "Marek",
        "Surname": "Kowalski",
        "Sex": true
      },
      "CaretakerId": null,
      "Periods": [
        {
          "Capabilities": [],
          "Id": 1,
          "Level": 1,
          "Number": 1,
          "Start": {
            "Timestamp": 0,
            "Date": "1970-01-01",
            "DateDisplay": "01.01.1970",
            "Time": "00:00:00"
          },
          "End": {
            "Timestamp": 0,
            "Date": "1970-01-01",
            "DateDisplay": "01.01.1970",
            "Time": "00:00:00"
          },
          "Current": true,
          "Last": true
        }
      ],
      "Journal": {
        "Id": 1,
        "YearStart": {
          "Timestamp": 0,
          "Date": "1970-01-01",
          "DateDisplay": "01.01.1970",
          "Time": "00:00:00"
        },
        "YearEnd": {
          "Timestamp": 0,
          "Date": "1970-01-01",
          "DateDisplay": "01.01.1970",
          "Time": "00:00:00"
        }
      },
      "Constraints": {
        "AbsenceDaysBefore": null,
        "AbsenceHoursBefore": null
      },
      "State": 0,
      "Policies": {
        "Privacy": null,
        "Cookie": null,
        "InfoEnclosure": null,
        "AccessDeclaration": null
      },
      "Context": "<context>",
      "MessageBox": {
        "Id": 1,
        "GlobalKey": "00000000-0000-0000-0000-000000000000",
        "Name": "Jan Kowalski - U - (PS1)"
      }
    }
  ],
  "EnvelopeType": "IEnumerable`1",
  "InResponseTo": null,
  "RequestId": "00000000-0000-0000-0000-000000000000",
  "Timestamp": "0",
  "TimestampFormatted": "1970-01-01 00:00:00"
}
```

## Schemat odpowiedzi
[ResponseEnvelope](./modele.md#ResponseEnvelope)<array<[HebePayload](./modele.md#HebePayload)>>
