# P1.1 Workspace i pierwszy notebook

**Czas orientacyjny** 1,5 h · **Środowisko** Databricks Free Edition

Dołączasz do zespołu danych sklepu internetowego. Przed pierwszym importem trzeba sprawdzić, czy w workspace można przechować plik wejściowy, uruchomić notebook i odnaleźć dane w Unity Catalog.

## Dane wejściowe

[orders-smoke.jsonl](orders-smoke.jsonl) to fikcyjny eksport zamówień. Każdy wiersz reprezentuje jedno zamówienie, a `items` zawiera jego pozycje. Kwoty `unit_price_pln` są cenami jednostkowymi w PLN.

## Zadanie

1. Utwórz własny notebook w workspace Free Edition. Pokaż, że działa w nim co najmniej jedna komórka Python i jedna komórka SQL. Temat prostego sprawdzenia w każdej komórce wybierz samodzielnie.
2. Umieść plik w managed volume w Unity Catalog. Pokaż w notebooku podgląd rekordów z pliku i policz zamówienia. Zapisz pełną ścieżkę pliku i pełną nazwę jednej tabeli widocznej w Catalog Explorer. Może to być tabela przykładowa. Porównaj, co reprezentują oba obiekty.
3. W krótkiej notatce dobierz compute dla trzech sytuacji: inżynier ręcznie bada nowy eksport, proces co noc przetwarza dane automatycznie, a kilku analityków w ciągu dnia zadaje pytania w SQL. Dla każdej sytuacji uzasadnij wybór przez sposób uruchamiania, współbieżność i rozliczanie zasobów. Ustal z dokumentacji, w którym przypadku rozważyłbyś classic compute poza Free Edition.

## Kryteria odbioru

- Po uruchomieniu notebooka widać wynik każdej z dwóch komórek językowych, podgląd zamówień i liczbę rekordów zgodną z plikiem.
- Możesz wskazać, gdzie działa kod, gdzie jest plik i jak `catalog`, `schema`, `volume` oraz `table` odnoszą się do obiektów, które znalazłeś.
- Każda z trzech decyzji o compute ma uzasadnienie i odnośnik do dokumentacji, którą samodzielnie znalazłeś.

Do review prześlij eksport notebooka lub wklej jego komórki i wyniki. Dołącz swoje decyzje o compute oraz, jeśli coś Cię zatrzymało, opis próby i komunikat błędu. [Limity Databricks Free Edition](https://docs.databricks.com/aws/en/getting-started/free-edition-limitations)
