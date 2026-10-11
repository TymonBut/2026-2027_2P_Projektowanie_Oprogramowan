# Struktury danych – ćwiczenia
## Lekcje 1–3 – odpowiedzi

# Lekcja 1. Tablice jednowymiarowe i dwuwymiarowe

## Ćwiczenie 1.1 – Indeksy

a) Indeks pierwszego elementu: `0`

b) Indeks ostatniego elementu: `7`

c) Liczba elementów: `8`

d) Poprawny warunek pętli: `for (i = 0; i < 8; i++)`

e)
- **Java:** `tab[8]` powoduje wyjątek `ArrayIndexOutOfBoundsException`.
- **C:** odwołanie poza tablicę powoduje niezdefiniowane zachowanie.

## Ćwiczenie 1.2 – Adresy w pamięci

| Element | Adres |
|---|---:|
| `tab[0]` | 2000 |
| `tab[1]` | 2004 |
| `tab[3]` | 2012 |
| `tab[5]` | 2020 |

Wzór: `adres(tab[i]) = 2000 + i * 4`

Rozmiar tablicy: `6 * 4 = 24 bajty`.

## Ćwiczenie 1.3 – Schematy przetwarzania

### a) Funkcja licząca średnią

```python
def srednia(tab):
    return sum(tab) / len(tab)
```

### b) Funkcja zwracająca indeks najmniejszej wartości

```python
def indeks_min(tab):
    indeks = 0
    for i in range(1, len(tab)):
        if tab[i] < tab[indeks]:
            indeks = i
    return indeks
```

### c) Funkcja zliczająca elementy większe od podanej wartości

```python
def policz_wieksze(tab, wartosc):
    licznik = 0
    for x in tab:
        if x > wartosc:
            licznik += 1
    return licznik
```

## Ćwiczenie 1.4 – Znajdź błąd

### a)

**Błąd:** pętla zaczyna od indeksu `1` i używa `i <= n`, przez co pomija pierwszy element i wychodzi poza tablicę.

Poprawnie:

```cpp
for (i = 0; i < n; i++)
    suma += tab[i];
```

### b)

**Błąd:** `maks = 0` jest niepoprawne, gdy wszystkie elementy tablicy są ujemne.

Poprawnie:

```cpp
int maks = tab[0];

for (i = 1; i < n; i++)
    if (tab[i] > maks)
        maks = tab[i];
```

### c)

**Błąd:** ostatnia iteracja odczytuje `tab[n]`, czyli element poza tablicą.

Poprawnie:

```cpp
for (i = 0; i < n - 1; i++)
    tab[i] = tab[i + 1];
```

## Ćwiczenie 1.5 – Tablica dwuwymiarowa

Macierz:

```text
1   2   3   4
5   6   7   8
9  10  11  12
```

a) `m[0][0] = 1`

b) `m[1][2] = 7`

c) `m[2][3] = 12`

d) `m[2][0] = 9`

### e) Suma każdego wiersza

```cpp
for (int i = 0; i < 3; i++) {
    int suma = 0;

    for (int j = 0; j < 4; j++) {
        suma += m[i][j];
    }

    cout << suma << endl;
}
```

Wyniki: `10`, `26`, `42`.

### f) Suma przekątnej macierzy kwadratowej

```cpp
int suma = 0;

for (int i = 0; i < n; i++) {
    suma += m[i][i];
}

cout << suma;
```

## Ćwiczenie 1.6 – Układ w pamięci

Macierz:

```text
7  8  9
1  2  3
```

a) **Układ wierszami:** `7, 8, 9, 1, 2, 3`

b) **Układ kolumnami:** `7, 1, 8, 2, 9, 3`

c)
- C – układ wierszami.
- Fortran – układ kolumnami.

## Ćwiczenie 1.7 – Szachownica

```python
tab = []

for i in range(8):
    wiersz = []
    for j in range(8):
        if (i + j) % 2 == 0:
            wiersz.append("#")
        else:
            wiersz.append(".")
    tab.append(wiersz)

for wiersz in tab:
    print("".join(wiersz))
```

# Lekcja 2. Tablice dynamiczne i asocjacyjne

## Ćwiczenie 2.1 – Rozmiar a pojemność

Zakładamy początkową pojemność `2` i podwajanie po zapełnieniu.

| Po dodaniu elementu nr | Rozmiar | Pojemność | Czy nastąpiło przepisanie? |
|---:|---:|---:|---|
| 1 | 1 | 2 | Nie |
| 2 | 2 | 2 | Nie |
| 3 | 3 | 4 | Tak |
| 5 | 5 | 8 | Tak |
| 9 | 9 | 16 | Tak |

Przepisanie następuje wtedy, gdy tablica jest pełna i trzeba zwiększyć jej pojemność.

## Ćwiczenie 2.2 – Nazwy w językach

| Język | Typ tablicy dynamicznej | Dodanie na koniec | Odczyt rozmiaru |
|---|---|---|---|
| Python | `list` | `lista.append(x)` | `len(lista)` |
| Java | `ArrayList` | `lista.add(x)` | `lista.size()` |
| C++ | `vector` | `v.push_back(x)` | `v.size()` |
| C# | `List<T>` | `lista.Add(x)` | `lista.Count` |

## Ćwiczenie 2.3 – Tablica czy słownik

| Dane | Struktura | Uzasadnienie |
|---|---|---|
| Oceny ucznia w kolejności wystawiania | Lista | Zachowuje kolejność ocen i pozwala dodawać kolejne. |
| Liczba mieszkańców według nazwy miasta | Słownik | Nazwa miasta może być kluczem, a liczba mieszkańców wartością. |
| Kolejka zgłoszeń do rozpatrzenia | Kolejka | Zgłoszenia można obsługiwać w kolejności przyjęcia. |
| Ustawienia programu (nazwa opcji i wartość) | Słownik | Każda nazwa opcji wskazuje jej wartość. |
| Lista zakupów do odhaczania | Lista | Przechowuje produkty w kolejności i umożliwia ich oznaczanie. |
| Liczba wystąpień każdego słowa w tekście | Słownik | Słowo jest kluczem, a liczba wystąpień wartością. |

## Ćwiczenie 2.4 – Operacje na słowniku

Dany słownik:

```python
magazyn = {
    "srubki": 120,
    "nakretki": 80,
    "podkladki": 45
}
```

### a) Dodanie gwoździ

```python
magazyn["gwozdzie"] = 200
```

### b) Zwiększenie liczby śrubek o 30

```python
magazyn["srubki"] += 30
```

### c) Sprawdzenie, czy są wkręty

```python
print("wkret y".replace(" ", "") in magazyn)
```

### d) Usunięcie podkładek

```python
del magazyn["podkladki"]
```

### e) Wypisanie pozycji z wartością mniejszą niż 100

```python
for nazwa, liczba in magazyn.items():
    if liczba < 100:
        print(nazwa, liczba)
```

### f) Policzenie łącznej liczby elementów

```python
print(sum(magazyn.values()))
```

## Ćwiczenie 2.5 – Klucz czy nie klucz

a) **Numer PESEL – tak**, jeśli jest przechowywany jako niezmienny tekst lub liczba.

b) **Imię ucznia – tak**, ponieważ tekst może być kluczem słownika; trzeba jednak pamiętać, że imiona mogą się powtarzać.

c) **Lista ocen – nie**, ponieważ lista w Pythonie jest mutowalna i nie może być kluczem słownika.

d) **Adres e-mail – tak**, jeśli jest przechowywany jako tekst.

e) **Data i godzina pomiaru – tak**, jeśli użyty obiekt jest hashowalny i niezmienny, np. `datetime` w Pythonie.

f) **Obiekt, którego pola zmieniają się w trakcie – zazwyczaj nie**, jeśli zmienność wpływa na jego haszowanie lub porównywanie. W Pythonie zwykłe obiekty mutowalne, np. słowniki, nie mogą być kluczami.

## Ćwiczenie 2.6 – Licznik słów

```python
zdanie = input("Podaj zdanie: ").lower()
slowa = zdanie.split()

licznik = {}

for slowo in slowa:
    licznik[slowo] = licznik.get(slowo, 0) + 1

for slowo, ile in licznik.items():
    print(slowo, ile)
```

**Dlaczego słownik jest lepszy od listy?**

Słownik przechowuje słowo jako klucz i szybko pozwala znaleźć lub zwiększyć jego licznik. Lista wymagałaby dodatkowego wyszukiwania słów i zarządzania ich liczbą wystąpień.

# Lekcja 3. Typ rekordowy: struktura i unia

## Ćwiczenie 3.1 – Projekt rekordu

| Pole | Typ | Uzasadnienie |
|---|---|---|
| `tytul` | `string` | Przechowuje tytuł książki. |
| `autor` | `string` | Przechowuje autora. |
| `rok_wydania` | `int` | Przechowuje rok wydania. |
| `liczba_stron` | `int` | Przechowuje liczbę stron. |
| `dostepna` | `bool` | Określa, czy książka jest dostępna. |

## Ćwiczenie 3.2 – Tablice równoległe

### a) Dwa problemy

1. Dane jednego pracownika są rozdzielone między trzy tablice.
2. Łatwo pomylić indeksy, przez co można przypisać niewłaściwą pensję do pracownika.

### b) Struktura i tablica rekordów w C++

```cpp
struct Pracownik {
    char nazwisko[40];
    int wiek;
    float pensja;
};

Pracownik pracownicy[100];
```

### c) Wypisanie nazwisk osób zarabiających powyżej 5000

```cpp
for (int i = 0; i < 100; i++) {
    if (pracownicy[i].pensja > 5000) {
        cout << pracownicy[i].nazwisko << endl;
    }
}
```

## Ćwiczenie 3.3 – Rozmiar struktury

Zakładamy podane rozmiary typów i wyrównanie do rozmiaru największego pola.

a) `struct A { int x; int y; };`

**Rozmiar: 8 bajtów** – dwa pola po 4 bajty.

b) `struct B { char c; int x; };`

**Rozmiar: 8 bajtów** – 1 bajt na `char`, 3 bajty dopełnienia i 4 bajty na `int`.

c) `struct C { char c; char d; int x; };`

**Rozmiar: 8 bajtów** – 2 bajty na znaki, 2 bajty dopełnienia i 4 bajty na `int`.

d) `union D { int x; double y; char c[4]; };`

**Rozmiar: 8 bajtów** – unia musi pomieścić największe pole, czyli `double` zajmujący 8 bajtów.

W podpunkcie b wynik nie wynosi 5 bajtów, ponieważ struktura zawiera dopełnienie (padding), które zapewnia odpowiednie wyrównanie pamięci dla pola `int`.

## Ćwiczenie 3.4 – Rekord zagnieżdżony

Przykładowa definicja w C++:

```cpp
struct Adres {
    string ulica;
    string miasto;
    string kodPocztowy;
};

struct Klient {
    string nazwa;
    Adres adres;
};

struct Data {
    int dzien;
    int miesiac;
    int rok;
};

struct Zamowienie {
    int numer;
    Klient klient;
    Data dataZlozenia;
    double wartosc;
};
```

Odwołanie do miasta klienta:

```cpp
zamowienie.klient.adres.miasto
```

## Ćwiczenie 3.5 – Struktura a unia

a) **Struktura** przechowuje osobne miejsce dla każdego pola, a **unia** współdzieli pamięć między polami.

b) W unii sensowną wartość ma zazwyczaj jedno pole naraz.

c) Pole rozpoznawcze informuje, który wariant unii jest aktualnie zapisany.

d) Praktyczne zastosowanie: przechowywanie różnych typów wyniku pomiaru, np. liczby całkowitej albo rzeczywistej.

## Ćwiczenie 3.6 – Unia z polem rozpoznawczym

Przykładowe rozwiązanie w C++:

```cpp
#include <iostream>
using namespace std;

enum TypWyniku {
    CALKOWITY,
    RZECZYWISTY,
    BLAD
};

struct WynikPomiaru {
    TypWyniku typ;

    union {
        int calkowity;
        double rzeczywisty;
        int kodBledu;
    } dane;
};

void wypisz(WynikPomiaru wynik) {
    if (wynik.typ == CALKOWITY) {
        cout << wynik.dane.calkowity;
    } else if (wynik.typ == RZECZYWISTY) {
        cout << wynik.dane.rzeczywisty;
    } else if (wynik.typ == BLAD) {
        cout << "Blad pomiaru, kod: "
             << wynik.dane.kodBledu;
    }
}
```

Pole `typ` określa, którą część unii należy odczytać. Dzięki temu program interpretuje zapisane dane we właściwy sposób.
