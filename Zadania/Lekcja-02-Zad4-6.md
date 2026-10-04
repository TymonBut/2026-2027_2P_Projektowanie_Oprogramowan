# Lekcja 4. Typ logiczny i znakowy. Kodowanie znaków



## Ćwiczenie 4.1 – Tablica prawdy



| a | b | a AND b | a OR b | NOT a | a XOR b | NOT (a AND b) |

| - | - | ------- | ------ | ----- | ------- | ------------- |

| F | F | F       | F      | T     | F       | T             |

| F | T | F       | T      | T     | T       | T             |

| T | F | F       | T      | F     | T       | T             |

| T | T | T       | T      | F     | F       | F             |



## Ćwiczenie 4.2 – Skrócone obliczanie


### a)


Gdy lista == null, pierwszy warunek jest fałszywy. Dzięki && drugi warunek nie jest sprawdzany. Całość daje false.


### b)


Po zamianie warunków program spróbuje wykonać lista.size() dla null, więc wystąpi NullPointerException.


### c)

```java

if (lista == null || lista.size() == 0) {  ... }

```

## Ćwiczenie 4.3 – Kody znaków

a) 68

b) 122

c) J

d) 7

e) A



## Ćwiczenie 4.4 – Zamiana wielkości liter



```text

funkcja naMalaLitera(znak):

jeżeli kod(znak) >= kod('A') i kod(znak) <= kod('Z'):

zwróć znak o kodzie kod(znak) + 32

w przeciwnym razie:

zwróć znak

```



## Ćwiczenie 4.5 – ASCII a Unicode



a) **F** – ASCII jest 7-bitowe i definiuje 128 znaków.

b) **F** – Unicode definiuje punkty kodowe znaków, a UTF-8 jest sposobem ich kodowania.

c) **P**

d) **F** – znak w UTF-8 zajmuje od 1 do 4 bajtów.

e) **P**

f) **F** – emoji można zapisywać w UTF-8.



## Ćwiczenie 4.6 – Mojibake



### a)



Błędną interpretacją kodowania znaków (problem z kodowaniem znaków).



### b)



Nie. Dane zwykle nie zostały uszkodzone, tylko odczytano je przy użyciu niewłaściwego kodowania.



### c)


w pliku HTML: `<meta charset="UTF-8">`,

W nagłówkach HTTP serwera:`Content-Type`,

używanie właściwego kodowania przy odczycie i zapisie plików.



## Ćwiczenie 4.7 – Bajty w praktyce



| Tekst      | Liczba znaków | Liczba bajtów |

| ---------- | ------------: | ------------: |

| `Ala`      |             3 |             3 |

| `Zażółć`   |             6 |             9 |

| `cześć :)` |             7 |            10 |



`len()` liczy znaki, natomiast `len(tekst.encode("utf-8"))` liczy bajty.

W UTF-8:

zwykłe znaki ASCII zajmują 1 bajt,

polskie znaki diakrytyczne zajmują 2 bajty,

emoji zajmuje 4 bajty.


# Lekcja 5. Typ łańcuchowy



## Ćwiczenie 5.1 – Indeksowanie



Dla `s = "Programista"`:



a) `11`

b) `P`

c) `g`

d) `a`

e) `"Progra"`

f) `6`



## Ćwiczenie 5.2 – Niemutowalność



### a)


Wystąpi `TypeError`, ponieważ `str` w Pythonie jest niemutowalny.


### b)



```python

tekst = "kot"

tekst = "bot"

```

### c)


Powstają dwa obiekty `str`: `"kot"` i `"bot"`.



## Ćwiczenie 5.3 – Reprezentacja w pamięci



### a)

```text

[A][l][a][\0]

```

### b)

```text

[3][A][l][a]

```

Szybciej długość odczytuje wersja z zapisaną długością, ponieważ długość znajduje się bezpośrednio w pamięci.


## Ćwiczenie 5.4 – Wydajność



### a)



`str` jest niemutowalny, więc przy każdym `+=` powstaje nowy napis i dane są kopiowane.



\### b)



```python

wynik = "".join(str(i) for i in range(100000))

```



### c)



W Javie do wydajnego tworzenia zmiennych napisów można użyć `StringBuilder`.



## Ćwiczenie 5.5 – Parsowanie danych



```python

wiersz = "  Kowalski;Jan;2008-05-14;klasa 2p  "

pola = wiersz.strip().split(";")



print(pola\[0])

print(pola\[2]\[:4])

```



Wynik:



```text

Kowalski

2008

```



## Ćwiczenie 5.6 – Porównywanie



Rosnąco według kodów znaków:



```text

"Ananas"

"Banan"

"ananas"

"banan"

"zebra"

"Żaba"

```



Nie jest to polski porządek alfabetyczny. Należy zastosować porównywanie zgodne z regułami języka polskiego, czyli odpowiednią lokalizację/collation.



\---



# Lekcja 6. Dobór typu prostego do problemu programistycznego



## Ćwiczenie 6.1 – Formularz rejestracyjny



| Pole               | Typ       | Uzasadnienie                                       |

| ------------------ | --------- | -------------------------------------------------- |

| Imię               | `String`  | Imię jest tekstem.                                 |

| Wiek               | `int`     | Jest liczbą całkowitą.                             |

| PESEL              | `String`  | Jest identyfikatorem, a nie liczbą do obliczeń.    |

| Numer telefonu     | `String`  | Jest identyfikatorem i może zawierać zera wiodące. |

| Adres e-mail       | `String`  | Jest tekstem.                                      |

| Zgoda na regulamin | `boolean` | Ma dwie wartości: tak lub nie.                     |

| Wzrost w cm        | `int`     | Jest liczbą całkowitą.                             |

| Waga w kg          | `double`  | Może zawierać część ułamkową.                      |



## Ćwiczenie 6.2 – Sklep internetowy



| Kolumna          | Typ w aplikacji | Typ w bazie danych | Uzasadnienie                      |

| ---------------- | --------------- | ------------------ | --------------------------------- |

| `id\_zamowienia`  | `long`          | `BIGINT`           | Duży zakres identyfikatorów.      |

| `id\_klienta`     | `long`          | `BIGINT`           | Identyfikator klienta.            |

| `data\_zlozenia`  | `LocalDateTime` | `TIMESTAMP`        | Data i czas złożenia zamówienia.  |

| `wartosc\_brutto` | `BigDecimal`    | `DECIMAL(12,2)`    | Dokładne przechowywanie kwot.     |

| `liczba\_pozycji` | `int`           | `INT`              | Liczba całkowita.                 |

| `czy\_oplacone`   | `boolean`       | `BOOLEAN`          | Dwie możliwe wartości.            |

| `kod\_rabatowy`   | `String`        | `VARCHAR(50)`      | Kod może zawierać litery i cyfry. |



## Ćwiczenie 6.3 – Znajdź błąd



### a)



`float` dla salda może powodować błędy zaokrągleń.



Poprawka:`BigDecimal`.



### b)



Numer telefonu nie powinien być liczbą.



```java

String numer\_telefonu = "501234567";

```



### c)



`byte` ma zbyt mały zakres.



Poprawka: `int`.



### d)



`int` może być poprawny, jeśli liczba identyfikatorów mieści się w jego zakresie. Przy większym zakresie należy użyć `long`.



### e)



`char` jest technicznie poprawny dla `'K'` i `'M'`.



### f)



Kod pocztowy nie powinien być liczbą.



```java

String kod\_pocztowy = "50-137";

```



## Ćwiczenie 6.4 – Sensor temperatury



### a)



Można użyć `float` albo `double`.



`float` wystarczy do dokładności 0,1°C i zajmuje 4 bajty. `double` zajmuje 8 bajtów.



### b)



Liczba odczytów w ciągu roku:



```text

365 × 24 × 60 = 525600 odczytów

```



### c)



`float`:



```text

525600 × 4 B = 2 102 400 B

```



`double`:



```text

525600 × 8 B = 4 204 800 B

```



### d)



Można zapisywać temperaturę w dziesiątych częściach stopnia jako `short`:



```text

−40,0°C → −400

+85,0°C → 850

```



`short` zajmuje 2 bajty, więc:



```text

525600 × 2 B = 1 051 200 B

```


## Ćwiczenie 6.5 – Zadanie zespołowe



**Przykład: system biblioteczny**



| Nazwa danej          | Typ          | Zakres wartości       | Uzasadnienie                             |

| -------------------- | ------------ | --------------------- | ---------------------------------------- |

| `id\_ksiazki`         | `int`        | 1–2 147 483 647       | Identyfikator liczbowy.                  |

| `tytul`              | `String`     | tekst                 | Tytuł jest tekstem.                      |

| `autor`              | `String`     | tekst                 | Autor jest tekstem.                      |

| `rok\_wydania`        | `short`      | −32 768–32 767        | Rok mieści się w zakresie.               |

| `isbn`               | `String`     | tekst                 | ISBN jest identyfikatorem.               |

| `liczba\_egzemplarzy` | `int`        | 0–2 147 483 647       | Liczba całkowita nieujemna.              |

| `id\_czytelnika`      | `int`        | 1–2 147 483 647       | Identyfikator liczbowy.                  |

| `imie\_czytelnika`    | `String`     | tekst                 | Imię jest tekstem.                       |

| `data\_wypozyczenia`  | `LocalDate`  | daty kalendarzowe     | Przechowuje datę wypożyczenia.           |

| `czy\_zwrocona`       | `boolean`    | `true`/`false`        | Dwie możliwe wartości.                   |

| `kara`               | `BigDecimal` | 0 i wartości dodatnie | Dokładne przechowywanie kwot.            |

| `numer\_polki`        | `String`     | tekst                 | Oznaczenie może zawierać litery i cyfry. |

Robiłem razem z [link do repozytorium](https://github.com/1nnonlyy/Websites/tree/main/elektronik-2p)



