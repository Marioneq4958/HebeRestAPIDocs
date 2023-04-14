# Rejestracja certyfikatu

## Porzebne dane

- Token np. `FK1000` i symbol grupujący np. `powiatwulkanowy` lub kod QR
- Adres Rest API _opcjonalny_
- PIN np. `999999`
- Nazwa np. `Wulkanowy` i system urządzenia `Android` lub `iOS`
- Certyfikat np. `X509`
- Token firebase _opcjonalny_

## Uzyskiwanie tokenu, symbolu grupującego i adresu Rest API z użyciem kodu QR

Zawartość kodu QR jest zaszyfrowana z użyciem algorytmu `aes-128-ecb` hasłem `tDVS4ykCBBAeN33h`, do odszyfrowania zawartości można użyć [wulkanowy/qr](https://github.com/wulkanowy/qr).

Po odszyfrowaniu zawartość powinna wyglądać tak:

```txt
CERT#{adresRestAPI}/{symbolGrupujący}/mobile-api#{token}#ENDCERT
```

## Uzyskiwanie adresu Rest API z użyciem tokenu

Na początku należy pobrać listę adresów Rest API:

### Żądanie

```http
GET https://komponenty.vulcan.net.pl/UonetPlusMobile/RoutingRules.txt
```

### Przykładowa odpowiedź

```txt
3S1,https://lekcjaplus.vulcan.net.pl
TA1,https://uonetplus-komunikacja.umt.tarnow.pl
OP1,https://uonetplus-komunikacja.eszkola.opolskie.pl
GD1,https://uonetplus-komunikacja.edu.gdansk.pl
P03,https://efeb-komunikacja-pro-efebmobile.pro.vulcan.pl
P01,http://efeb-komunikacja.pro-hudson.win.vulcan.pl
P02,http://efeb-komunikacja.pro-hudsonrc.win.vulcan.pl
P90,http://efeb-komunikacja-pro-mwujakowska.neo.win.vulcan.pl
```

Lista zawiera 3 pierwsze znaki tokenu i odpowiednie dla nich adresy Rest API, przykładowo adres dla tokenu **`GD1`** `2A6G00` to `https://uonetplus-komunikacja.edu.gdansk.pl`.

## Rejestracja

### Żądanie

```http
POST /api/mobile/register/new
```

#### Przykładowe żądanie

```http
POST http://api.fakelog.cf/powiatwulkanowy/api/mobile/register/new

vOS: Android
vDeviceModel: WulkanowyPhone
vAPI: 1
VDate: Tue, 1 Jan 1970 00:00:00 GMT
vCanonicalUrl: api%2fmobile%2fregister%2fnew
Digest: SHA-256=XYZ=
Signature: keyId="XYZ",headers="vCanonicalUrl Digest vDate" algorithm="sha256withrsa",signature=Base64(SHA256withRSA(XYZ==))
Content-Type: application/json

{
  "AppName": "DzienniczekPlus 2.0",
  "AppVersion": "1.0",
  "Envelope": {
    "OS": "Android",
    "DeviceModel": "WulkanowyPhone",
    "Certificate": "XYZ",
    "CertificateType": "X509",
    "CertificateThumbprint": "XYZ",
    "PIN": "999999",
    "SecurityToken": "FK10000",
    "SelfIdentifier": "00000000-0000-0000-0000-000000000000"
  },
  "API": 1,
  "RequestId": "00000000-0000-0000-0000-000000000000",
  "Timestamp": "0",
  "TimestampFormatted": "1970-01-01 00:00:00"
}
```

#### Parametry

##### Nagłówki

- `vOS`\
  System operacyjny urządzenia

- `vDeviceModel`\
  Nazwa certyfikatu lub urządzenia

- `vAPI` _1_\
  Wersja Rest API

- `vDate`\
  Aktualny czas w formacie `E, d MMM yyyy HH:mm:ss zzz`

- `vCannonicalUrl`\
  Zakodowany endpoint

- `Digest`

- `Signature`\
  Podpis żądania

- `Content_Type` _appliaction/json_

Parametry `vCannonicalUrl`, `Digest` i `Signature` można uzyskać używając [https://github.com/wulkanowy/uonet-request-signer](wulkanowy/uonet-request-signer)

##### Żądanie

- `AppName` _string_ _DzienniczekPlus2.0_\
  Nazwa apilkacji

- `AppVersion` _string_ _1.0_\
  Wersja aplikacji

- `Envelope` _dictionary_

  - `OS` _string_\
    System operacyjny urządzenia

  - `DeviceModel` _string_\
    Nazwa certyfikatu lub urządzenia

  - `Certificate` _string_\
    Certyfikat

  - `CertificateType` _string_\
    Typ certyfikatu

  - `CertificateThumbprint` _string_\
    Odcisk palca certyfikatu

  - `PIN` _string_

  - `SecurityToken` _string_\
    Token

  - `FirebaseToken` _string_ _opcjonalny_\
    Token firebase

  - `SelfIdentifier` _string_\
    Losowe UUID v4

- `API` _number_\
  Wersja Rest API

- `RequestId` _string_\
  Losowe UUID v4

- `Timestamp` _string_\
  Aktualny czas w strefie czasowej UTC+2 w timestamp'ie

- `TimestampFormatted` _string_\
  Aktualny czas w strefie czasowej UTC+2 w formacie `yyyy-MM-dd  HH:mm:ss`

### Odpowiedź

#### Przykładowa odpowiedź

```http
{
  "Envelope": {
    "OS": "Android",
    "DeviceModel": "WulkanowyPhone",
    "Certificate": "XYZ=",
    "CertificateType": "X509",
    "CertificateThumbprint": "XYZ",
    "PIN": "999999",
    "SecurityToken": "FK10000",
    "SelfIdentifier": "00000000-0000-0000-0000-000000000000"
  },
  "EnvelopeType": "AccountPayload",
  "InResponseTo": null,
  "RequestId": "00000000-0000-0000-0000-000000000000",
  "Timestamp": 0,
  "TimestampFormatted": "1970-01-01 00:00:00"
}
```

#### Schemat

- `Envelope` _dictionary_

  - `LoginId` _number_\
    Id użytkownika w grupie klientów

  - `RestURL` _string_\
    Adres Rest API z symbolem grupującym

  - `UserLogin` _string_\
    Nazwa użytkownika

  - `UserName` _string_\
    Identyczna wartość jak w `UserLogin`

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

- `Timestamp` _number_\
  Data odpowiedzi w strefie czasowej UTC+2 w timestamp'ie

- `TimestampFormatted` _string_\
  Data odpowiedzi w strefie czasowej UTC+2 w formacie `yyyy-MM-dd  HH:mm:ss`

