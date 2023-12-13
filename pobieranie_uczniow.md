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

## Schemat `Envelope` _array_

Schemat odpowiedzi znajdziesz w [Wysyłanie żądań](./wysylanie_zadan.md).

  - `TopLevelPartition` _string_\
    Symbol grupujący

  - `Partition` _string_\
    Symbol grupujący i symbol jednostki sprawozdawczej

  - `Links` _dictionary_

    - `Group` _string_\
      Symbol grupujący

    - `Symbol` _string_\
      Symbol jednostki sprawozdawczej

    - `Alias` _null_

    - `QuestionnaireRoot` _string_\
      Adres bazowy modułu `uonetplus-ankietyplus`

  - `ClassDisplay` _string_\
    Aktualny poziom i symbol oddziału

  - `InfoDisplay` _string_\
    Symbol jednostki sprawozdawczej oraz symbol i aktualny poziom oddziału

  - `FullSync` _boolean_

  - `SenderEntry` _dictionary_ _opcjonalny_\
    Dane nadawcy wiadomości, pozostałość po starym module wiadomości, nie jest to już używane. Pole zwracane tylko w mode 1, w mode 2 zawsze ma wartość `null`.

    - `Address` _string_\
      Adres

    - `AddressHash` _string_\
      Zhashowany adres

    - `Initials` _string_\
      Inicjały

    - `LoginId` _number_\
      Id użytkownika w grupie klientów

  - `Login` _dictionary_\
    Dane użytkownika w grupie klientów

    - `Id` _number_

    - `Value` _string_\
      Nazwa użytkownika

    - `FirstName` _string_\
      Imię

    - `SecondName` _string_\
      Drugie imię

    - `Surname` _string_\
      Nazwisko

    - `DisplayName` _string_\
      Imię, drugie imię i nazwisko

    - `LoginRole` _string_\
      Rola `Uczen` lub `Opiekun`

  - `Unit` _dictionary_\
    Dane jednostki sprawozdawczej

    - `Id` _number_

    - `Symbol` _string_

    - `Short` _string_\
      Skrót

    - `RestURL` _string_\
      Adres bazowy Rest API dla jednostki sprawozdawczej, potrzebny do wysyłania zapytań o np. oceny

    - `Name` _string_\
      Nazwa

    - `Address` _string_\
      Adres

    - `Patron` _string_

    - `DisplayName` _string_\
      Pełna nazwa

    - `SchoolTopic` _string_

  - `ConstituentUnit` _dictionary_\
    Dane jednostki składowej

    - `Id` _number_

    - `Short` _string_\
      Skrót

    - `Name` _string_\
      Nazwa

    - `Address` _string_\
      Adres

    - `Patron` _string_

    - `SchoolTopic` _string_

  - `Capabilities` _array_

  - `Educators` _array_\
    Lista wychowawców oddziału, pozostałość po starym module wiadomości

    - `Id` _number_

    - `LoginId` _number_\
      Id w grupie klienów

    - `Name` _string_\
      Imię

    - `Surname` _string_\
      Nazwisko

    - `Initials` _string_\
      Inicjały

    - `Roles` _array_\
      Role

      - `RoleName` _string_\
        Nazwa roli

      - `RoleOrder` _string_\
        Id roli

      - `Address` _string_\
        Adres

      - `AddressHash` _string_\
        Zhashowany adres

      - `UnitSymbol` _null_

      - `ConstituentUnitSymbol` _string_\
        Symbol jednostki składowej

      - `ClassSymbol` _string_\
        Aktualny poziom i symbol oddziału oraz skrót jednostki składowej

      - `Name` _string_\
        Imię

      - `Surname` _string_\
        Naziwsko

      - `Initials` _string_\
        Inicjały

    - `EducatorList` _array_\
      Lista skrzynek wychowawców oddziału, używane w nowym module wiadomości. Pole zwracane w mode 2, w mode 1 zawsze ma wartość null.

      - `GlobalKey` _string_

      - `Name` _string_\
        Nazwa skrzynki

      - `Group` _null_

    - `Pupil` _dictionary_\
      Dane ucznia

      - `Id` _number_

      - `LoginId` _number_\
        Id użytkownika

      - `LoginValue` _string_\
        Nazwa użytkownika

      - `FirstName` _string_\
        Imię

      - `SecondName` _string_\
        Drugie imię

      - `Surname` _string_\
        Nazwisko

      - `Sex` _boolean_\
        Płec `true` - mężczyzna, `false` - kobieta

    - `CaretakerId` _null_

    - `Periods` _array_\
      Lista okresów klasyfikacyjnych

      - `Capabitilies` _array_

      - `Id` _number_

      - `Level` _number_\
        Poziom oddziału

      - `Number` _number_\
        Numer okresu klasyfikacyjnego w roku szkolnym

      - `Start` _dictionary_\
        Data rozpoczęcia

        - `Timestamp` _number_

        - `Date` _string_\
          Data w formacie `yyyyy-MM-dd`

        - `DateDisplay` _string_\
          Data w formacie `dd.MM.yyyyy`

        - `Time` _string_\
          Data w formacie `HH:mm:ss`

      - `End` _dictionary_\
        Data zakończenia

        - `Timestamp` _number_

        - `Date` _string_\
          Data w formacie `yyyyy-MM-dd`

        - `DateDisplay` _string_\
          Data w formacie `dd.MM.yyyyy`

        - `Time` _string_\
          Data w formacie `HH:mm:ss`

    - `Current` _boolean_\
      Czy okres klasyfikacyjny jest aktualny

    - `Last` _boolean_\
      Czy okres klasyfikacyjny jest ostatnim w roku szkolnym

  - `Journal` _dictionary_\
    Dane aktualnego dziennika

    - `Id` _number_

    - `YearStart` _dictionary_\
      Data rozpoczęcia aktualnego roku szkolnego

      - `Timestamp` _number_

      - `Date` _string_\
         Data w formacie `yyyyy-MM-dd`

      - `DateDisplay` _string_\
         Data w formacie `dd.MM.yyyyy`

      - `Time` _string_\
         Data w formacie `HH:mm:ss`

    - `YearEnd` _dictionary_\
      Data zakończenia aktualnego roku szkolnego

      - `Timestamp` _number_

      - `Date` _string_\
         Data w formacie `yyyyy-MM-dd`

      - `DateDisplay` _string_\
         Data w formacie `dd.MM.yyyyy`

      - `Time` _string_\
         Data w formacie `HH:mm:ss`

  - `Constrains` _dictionary_

    - `AbsenceDaysBefore` _null_

    - `AbsenceHoursBefore` _null_

  - `State` _number_

  - `Policies` _dictionary_

    - `Privacy` _null_

    - `Cookie` _null_

    - `InfoEnclosure` _null_

    - `AccessDeclaration` _null_

  - `Context` _string_

  - `MessageBox` _dictionary_\
    Dane skrzynki

    - `Id` _number_

    - `GlobalKey` _string_

    - `Name` _string_\
      Nazwa skrzynki
