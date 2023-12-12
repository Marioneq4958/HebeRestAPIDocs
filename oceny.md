# Oceny
## Pobieranie listy ocen ucznia z danego okresu

```http
GET /api/mobile/grade/byPupil
```

### Potrzebne dane
- Zarejestrowany ceryfikat ([Jak zarejestrować certyfikat?](./rejestrowanie_certyfikatu.md))
- Rest URL dla jednostki sprawozdawczej (`Unit.RestURL` z odpowiedzi [`/register/hebe`](./pobieranie_uczniow.md))
- ID ucznia (`Pupil.Id` z odpowiedzi [`/register/hebe`](./pobieranie_uczniow.md))
- ID okresu (`Pupil.Periods.Id` z odpowiedzi [`/register/hebe`](./pobieranie_uczniow.md))
### Przykład żądania
TODO
### Parametry żądania
TODO
### Przykład odpowiedzi
TODO
### Schemat odpowiedzi
TODO
## Pobieranie oceny o danym id
```http
GET /api/mobile/grade/byId
```
### Potrzebne dane
- Zarejestrowany ceryfikat ([Jak zarejestrować certyfikat?](./rejestrowanie_certyfikatu.md))
- Rest URL dla jednostki sprawozdawczej (`Unit.RestURL` z odpowiedzi [`/register/hebe`](./pobieranie_uczniow.md))
- ID oceny
- ID ucznia (`Pupil.Id` z odpowiedzi [`/register/hebe`](./pobieranie_uczniow.md))
- ID okresu (`Pupil.Periods.Id` z odpowiedzi [`/register/hebe`](./pobieranie_uczniow.md))
### Przykład żądania
TODO
### Parametry żądania
TODO
### Przykład odpowiedzi
TODO
### Schemat odpowiedzi
TODO
## Pobieranie listy usuniętych ocen ucznia z danego okresu
```http
GET /api/mobile/grade/deleted/byPupil
```
### Potrzebne dane
- Zarejestrowany ceryfikat ([Jak zarejestrować certyfikat?](./rejestrowanie_certyfikatu.md))
- Rest URL dla jednostki sprawozdawczej (`Unit.RestURL` z odpowiedzi [`/register/hebe`](./pobieranie_uczniow.md))
- ID ucznia (`Pupil.Id` z odpowiedzi [`/register/hebe`](./pobieranie_uczniow.md))
- ID okresu (`Pupil.Periods.Id` z odpowiedzi [`/register/hebe`](./pobieranie_uczniow.md))
### Przykład żądania
TODO
### Parametry żądania
TODO
### Przykład odpowiedzi
TODO
### Schemat odpowiedzi
TODO
## Pobieranie listy usuniętych ocen
```http
GET /api/mobile/grade/deleted
```
### Potrzebne dane
- Zarejestrowany ceryfikat ([Jak zarejestrować certyfikat?](./rejestrowanie_certyfikatu.md))
- Rest URL dla jednostki sprawozdawczej (`Unit.RestURL` z odpowiedzi [`/register/hebe`](./pobieranie_uczniow.md))
### Przykład żądania
TODO
### Parametry żądania
TODO
### Przykład odpowiedzi
TODO
### Schemat odpowiedzi
TODO
