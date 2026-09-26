# Lekcja 1. Rola typów danych
## Ćwiczenie 1.1 – Trzy cechy typu

**bool** – true / false, operacje logiczne, 1 bajt.

**int32** – liczby od -2 147 483 648 do 2 147 483 647, działania matematyczne, 4 bajty.

**char** – pojedynczy znak, np. 'a', '7', porównywanie i odczyt kodu, 1–2 bajty.

## Ćwiczenie 1.2 – Statyczne czy dynamiczne

a) **Statyczne** – typ jest ustalany podczas kompilacji.

b) **Dynamiczne** – typ zmiennej może się zmienić podczas działania programu.

c) **Statyczne** – auto tylko automatycznie wykrywa typ, ale później się on nie zmienia.

d) **Dynamiczne** – w JavaScript zmienna może zmienić typ podczas działania.

## Ćwiczenie 1.3 – Silne czy słabe

"5" + 3 → Python: błąd, JavaScript: "53"

"5" * 2 → Python: "55", JavaScript: 10

"10" - 5 → Python: błąd, JavaScript: 5

True + 1 → Python: 2, JavaScript: 2

## Ćwiczenie 1.4 – Konwersje

a) 7

b) -7

c) 5.0

d) 3 + 3 = 6

e) 3.5 + 3.5 = 7.0 → 7

**W d ułamki obcinamy przed dodawaniem, a w e dopiero po dodawaniu.**

## Ćwiczenie 1.5 – Sprawdź w konsoli

**Ostatnia linia daje ValueError, ponieważ tekst "abc" nie może zostać zamieniony na liczbę całkowitą.**

# Lekcja 2. Typy liczbowe stałoprzecinkowe
## Ćwiczenie 2.1 – Zakresy

4 bity: 16 wartości → bez znaku 0–15, ze znakiem -8–7.

8 bitów: 256 wartości → bez znaku 0–255, ze znakiem -128–127.

16 bitów: 65 536 wartości → bez znaku 0–65 535, ze znakiem -32 768–32 767.

## Ćwiczenie 2.2 – Konwersja dwójkowo-dziesiętna

Bez znaku:
a) 15
b) 128
c) 255

Ze znakiem (U2):
a) 15
b) -128
c) -1

## Ćwiczenie 2.3 – Przepełnienie

120 → 127 → -128 → -121

**Wartość stanie się ujemna po 2 krokach, ponieważ 127 jest maksymalną wartością int8.**

## Ćwiczenie 2.4 – Dzielenie całkowite

a) 3

b) 2 – reszta z dzielenia

c) -3

d) 8 stron

## Ćwiczenie 2.5 – Dobór typu

Wiek: **uint8**, Maks. 255 lat, więc spokojnie wystarczy.

Rok: **uint16**, Maks. 65 535, więc wystarczy na lata.

Mieszkańcy Polski: **uint32**, mieszkańców jest około 38 mln, a typ mieści ponad 4 mld.

Mieszkańcy Ziemi: **uint64**, zakres 0 – 18 446 744 073 709 551 615, ludzi jest około 8 mld, więc wystarczy.

Rozmiar filmu w bajtach: **uint64**, Duże pliki mogą mieć wiele miliardów bajtów, więc uint64 daje odpowiednio duży zakres.

Temperatura: **int8**, Zakres -128 do 127 wystarczy do temperatur.

## Ćwiczenie 2.6 – Przepełnienie

**Wynik: -128.**

int8 kończy się na 127, więc po przekroczeniu zakresu licznik przechodzi na -128.

# Lekcja 3. Typy zmiennoprzecinkowe
## Ćwiczenie 3.1 – Float czy double

GPS: double

Kolor piksela: float

Obliczenia naukowe: double

Saldo bankowe: float

## Ćwiczenie 3.2 – Zapisywalne czy nie

Dokładnie zapiszemy:

0,5, 0,25, 0,75, 0,125, 1,5

**Ułamki z mianownikiem będącym potęgą 2 można dokładnie zapisać binarnie.**

## Ćwiczenie 3.3 – Klasyczny przykład

0.1 + 0.2 → 0.30000000000000004

0.1 + 0.2 == 0.3 → False

f"{0.1:.20f}" → 0.10000000000000000555 

0.1 + 0.7 → 0.7999999999999999

Jeśli 0.1 + 0.2 → 0.30000000000000004, to chyba już nic mnie nie zaskoczy.

## Ćwiczenie 3.4 – Poprawa kodu

Nie powinno się porównywać float przez ==, bo mogą wystąpić małe błędy zaokrągleń.
```python
def czy_zaplacono(kwota_wplacona, kwota_do_zaplaty):
    return abs(kwota_wplacona - kwota_do_zaplaty) < 0.00001
```
## Ćwiczenie 3.5 – Wartości specjalne

a) inf

b) -inf

c) nan

d) błąd – dzielenie przez zero

e) nan

f) False – nan nie jest równe nawet samemu sobie.

## Ćwiczenie 3.6 – Kwoty pieniężne

a) Może pojawić się np. 59.96999999999999.

b) Można przechowywać kwotę w groszach (1999 zamiast 19.99) albo użyć Decimal`.

c) W bazie danych: DECIMAL(10,2).
