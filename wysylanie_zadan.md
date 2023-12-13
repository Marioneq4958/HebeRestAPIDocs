# Wysyłanie żadań

## Żądanie

Do każdego żądania z wyjątkiem rejestrowania certyfikatu i pobierania listy uczniów należy używać Rest URL z danych ucznia np. `http://api.fakelog.cf/powiatwulkanowy/123456/api`.

### Parametry

#### Nagłówki

- `vOS`\
  System operacyjny urządzenia

- `vDeviceModel`\
  Nazwa certyfikatu lub urządzenia

- `vAPI` _1_\
  Wersja API

- `vDate`\
  Aktualny czas w formacie `E, d MMM yyyy HH:mm:ss zzz`

- `vCannonicalUrl`\
  Zakodowany endpoint

- `Signature`\
  Podpis żądania

Parametry `vCannonicalUrl` i `Signature` można uzyskać używając [wulkanowy/uonet-request-signer](https://github.com/wulkanowy/uonet-request-signer)

#### Żądanie (tylko dla POST)

- `AppName` _string_ _DzienniczekPlus2.0_\
  Nazwa apilkacji

- `AppVersion` _string_ _1.0_\
  Wersja aplikacji

- `Envelope`\
  Dane przekazywane w żądaniu


- `FirebaseToken` _string_ _opcjonalny_\
    Token firebase
  
- `API` _number_\
  Wersja Rest API

- `RequestId` _string_\
  Losowe UUID v4

- `Timestamp` _string_\
  Aktualny czas w strefie czasowej UTC+2 w timestamp'ie

- `TimestampFormatted` _string_\
  Aktualny czas w strefie czasowej UTC+2 w formacie `yyyy-MM-dd  HH:mm:ss`

### Przykład

```http
POST http://api.fakelog.cf/powiatwulkanowy/api/mobile/example

vOS: Android
vDeviceModel: WulkanowyPhone
vAPI: 1
VDate: Tue, 1 Jan 1970 00:00:00 GMT
vCanonicalUrl: api%2fmobile%2fexample
Digest: SHA-256=XYZ=
Signature: keyId="XYZ",headers="vCanonicalUrl Digest vDate" algorithm="sha256withrsa",signature=Base64(SHA256withRSA(XYZ==))
Content-Type: application/json

{
  "AppName": "DzienniczekPlus 2.0",
  "AppVersion": "1.0",
  "Envelope": {"hello": "world"},
  "FirebaseToken": "XYZ",
  "API": 1,
  "RequestId": "00000000-0000-0000-0000-000000000000",
  "Timestamp": "0",
  "TimestampFormatted": "1970-01-01 00:00:00"
}
```

## Odpowiedź

### Przykład

```http
{
  "Envelope": "Hello hebe!",
  "EnvelopeType": "String",
  "InResponseTo": null,
  "RequestId": "00000000-0000-0000-0000-000000000000",
  "Status": {
    "Code": 0,
    "Message": "OK"
  },
  "Timestamp": "0",
  "TimestampFormatted": "1970-01-01 00:00:00"
}
```

### Schemat

- `Envelope`\
  Dane zwracane w odpowiedzi np. lista ocen

- `EnvelopeType` _string_\
  Typ `Envelope`

- `InResponseTo` _null_

- `RequestId` _string_\
  Losowe UUID v4

- `Status` _dictionary_

  - `Code` _number_\
    Kod statusu

  - `Message` _string_\
    Opis statusu

- `Timestamp` _string_\
  Data odpowiedzi w strefie czasowej UTC+2 w timestamp'ie

- `TimestampFormatted` _string_\
  Data odpowiedzi w strefie czasowej UTC+2 w formacie `yyyy-MM-dd  HH:mm:ss`
