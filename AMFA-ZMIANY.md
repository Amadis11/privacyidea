# Zmiany AMFA w tym forku

Ten plik opisuje, jak oznaczamy i opisujemy nasze zmiany, zeby automat wydan (#199 w repozytorium
amitronic-amfa) mogl je rozpoznac i nalozyc na nowe wydanie privacyIDEA.

## Model galezi

- `master` — **lustro podstawy**. Nigdy nie commitujemy tu naszych zmian; sluzy tylko do pobierania
  nowych wydan i jako baza dla nakladania.
- `amfa` — **nasza linia**. Tu wchodza wszystkie nasze zmiany, kazda przez osobny PR.
- `amfa-<krok>` — galaz jednego kroku; po scaleniu usuwana. Uwaga: nie mozna uzywac nazw z ukosnikiem
  (`amfa/cos`), bo git nie pozwala miec jednoczesnie galezi `amfa` i `amfa/cos`.

## Konwencja commitow

Kazdy commit zaczyna sie od `AMFA: `. Po temacie idzie blok opisowy w stalej kolejnosci:

    AMFA: <co i ktory krok> (krok N z #199)

    CO: <co dokladnie zmienione, plikami>
    DLACZEGO: <powod zmiany>
    JAK: <sposob wykonania, zeby dalo sie odtworzyc>
    RYZYKO: <co moze sie zderzyc z nowa wersja podstawy i gdzie>
    WERYFIKACJA: <czym sprawdzone>
    AUTOMAT: <co ma zrobic automat wydan przy nakladaniu>

Uzasadnienie: przy nakladaniu na nowe wydanie najwazniejsze jest `RYZYKO` (gdzie spodziewac sie
konfliktu) i `AUTOMAT` (co uruchomic, zeby potwierdzic, ze zmiana nadal dziala). Bez tego kazda
aktualizacja bylaby czytaniem calego diffu od nowa.

## Zasady

- Jeden krok = jeden commit. Nasze zmiany nigdy nie sa wymieszane z kodem podstawy.
- Kazda zmiana, ktora da sie sprawdzic statycznie, dostaje straznika w `tests/test_amfa_zmiany.py`.
- Straznicy sa szybcy i nie wymagaja bazy danych — maja dzialac w automacie bez ciezkich zaleznosci.
- Wewnetrznej nazwy pakietu `privacyidea` nie zmieniamy: jest niewidoczna, a jej zmiana zerwalaby
  mozliwosc nakladania naszych zmian na nowe wydania.
