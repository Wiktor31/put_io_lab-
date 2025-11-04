# System aukcyjny

## Wprowadzenie

Specyfikacja wymagań funkcjonalnych w ramach informatyzacji procesu sprzedaży produktów w oparciu o mechanizm aukcyjny. 

## Procesy biznesowe

---
<a id="bc1"></a>
### BC1: Sprzedaż aukcyjna 

**Aktorzy:** [Sprzedający](#ac1), [Kupujący](#ac2)

**Opis:** Proces biznesowy opisujący sprzedaż za pomocą mechanizmu aukcyjnego. |

**Scenariusz główny:**
1. [Sprzedający](#ac1) wystawia produkt na aukcję. ([UC1](#uc1))
2. [Kupujący](#ac2) oferuje kwotę za produkt wyższą od aktualnie najwyższej oferty. ([BR1](#br1))
3. [Kupujący](#ac2) wygrywa aukcję ([BR2](#br2))
4. [Kupujący](#ac2) przekazuje należność Sprzedającemu.
5. [Sprzedający](#ac1) przekazuje produkt Kupującemu.

**Scenariusze alternatywne:** 

2.A. Oferta Kupującego została przebita, a [Kupujący](#ac2) pragnie przebić aktualnie najwyższą ofertę.
* 2.A.1. Przejdź do kroku 2.

3.A. Czas aukcji upłynął i [Kupujący](#ac2) przegrał aukcję. ([BR2](#br2))
* 3.A.1. Koniec przypadku użycia.

---

## Aktorzy

<a id="ac1"></a>
### AC1: Sprzedający

Osoba oferująca towar na aukcji.

<a id="ac2"></a>
### AC2: Kupujący

Osoba chcąca zakupić produkt na aukcji.


## Przypadki użycia poziomu użytkownika

### Aktorzy i ich cele

[Sprzedający](#ac1):
* [UC1](#uc1): Wystawienie produktu na aukcję
* [UC2](#uc2): Wysłąnie produktu
* ...

[Kupujący](#ac2)
* [UC3](#UC3): wystawienie oferty
* [UC4](#UC4): dokonanie płątności
* ...

---
<a id="uc1"></a>
### UC1: Wystawienie produktu na aukcję

**Aktorzy:** [Sprzedający](#ac1)

**Scenariusz główny:**
1. [Sprzedający](#ac1) zgłasza do systemu chęć sprzedania produktu na aukcję.
2. System prosi o podanie danych produktu i ceny wywoławczej.
3. [Sprzedający](#ac1) podaje dane produktu oraz cenę wywoławczą.
4. System weryfikuje poprawność danych.
5. System informuje o pomyślnym wystawieniu produktu na aukcję.

**Scenariusze alternatywne:** 

4.A. Podano niepoprawne lub niekompletne dane produktu.
* 4.A.1. System informuje o błędnie podanych danych.
* 4.A.2. Przejdź do kroku 2.

---

<a id="UC2"></a>
### UC2: Wysłąnie produktu

**Aktorzy:** [Sprzedający](#ac1), [Kupujący](#ac2), ...

**Scenariusz główny:**
1. [Sprzedający](#ac1) zgłasza do systemu chęć wysłania produktu.
2. System prosi o podanie danych.
3. [Sprzedający](#ac1) podaje adres kupującego.
4. System wysyła produkt do sprzedawcy.
---

<a id="UC3"></a>
### UC3: wystawienie oferty

**Aktorzy:** [Sprzedający](#ac1), [Kupujący](#ac2), ...

**Scenariusz główny:**
1. [Kupujący](#ac2) zgłasza swoją chęć oferty na zakup produktu w aukcji
2. System prosi o podanie oferty dla produktu.
3. [Kupujący](#ac2) zgłasza swoją oferta na zakup
4. System weryfikuje czy cena jest wyższa od obecnej ceny
5. System informuje o pomyślnym ofercie na produkt i zmiana ceny produktu.

**Scenariusze alternatywne:** 

4.A. Podano za małą oferte.
* 4.A.1. System informuje o za małej ofercie.
* 4.A.2. Przejdź do kroku 2.

---<a id="UC4"></a>
### UC3: dokonanie platności

**Aktorzy:** [Sprzedający](#ac1), [Kupujący](#ac2), ...

**Scenariusz główny:**
1. [Kupujący](#ac2) zgłasza swoją chęć na zapłate produktu w aukcji
2. System podaje konto.
3. [Kupujący](#ac2) płaci na dane konto
4. System weryfikuje czy zapłata się udałą
5. System informuje o pomyślnym przelewie.

**Scenariusze alternatywne:** 

4.A. Podano za małą oferte.
* 4.A.1. System informuje o za małej ofercie.
* 4.A.2. Przejdź do kroku 2.

---

## Obiewkty biznesowe (inaczje obiekty dziedzinowe lub informatycjne)

### BO1: Aukcja

Aukcja jest formą zawierania transakcji kupna-sprzedaży, w której Sprzedający określa cenę wywoławczą produktu, natomiast Kupujący mogą oferować własną ofertę zakupu każdorazowo proponując kwotę wyższą od aktualnie oferowanej kwoty. Aukcja kończy się po upływie określonego czasu. Jeśli złożona została co najmniej jedna oferta zakupy produkt nabywa ten Kupujący, który zaproponował najwyższą kwotę. 

### BO2: Produkt

Fizyczny lub cyfrowy obiekt, który ma zostać sprzedany w ramach aukcji.

## Reguły biznesowe

<a id="br1"></a>
### BR1: Złożenie oferty

Złożenie oferty wymaga zaproponowania kwoty wyższej niż aktualnie oferowana o minimum 1,00 PLN.


<a id="br2"></a>
### BR2: Rozstrzygnięcie aukcji

Aukcję wygrywa ten z [Kupujący](#ac2)ch, który w momencie jej zakończenia (upłynięcia czasu) złożył najwyższą ofertę.

## Macierz CRUDL


| Przypadek użycia                                  | Aukcja | Produkt | adres |  konto | 
| ------------------------------------------------- | ------ | ------- | --- |
| UC1: Wystawienia produktu na aukcję               |    c   |    C    | ... | ...
| UC2: Wysłąnie produktu               |    ...   |    ...    | r | c
| UC3: wystawienie oferty               |    ...   |    ...    | ... | ...|
| UC4: dokonanie płątności               |    ...   |    ...    | ... |
| ???                                               |  ...   |  ...    | ... |
