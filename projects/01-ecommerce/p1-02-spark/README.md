# P1.2 Spark i dane wejściowe

**Czas orientacyjny** 2,5 h · **Środowisko** Databricks Free Edition

Zespół sklepu wysyła dane z trzech systemów. Przed budową Bronze masz ustalić, co zawierają pliki i czy można je poprawnie wczytać do Spark.

## Dane wejściowe

| Plik | Zawartość |
| --- | --- |
| [customers.csv](customers.csv) | Eksport z CRM. Zawiera identyfikator klienta, datę rejestracji, kod pocztowy i informację o zgodzie marketingowej. |
| [orders-smoke.jsonl](../p1-01-workspace/orders-smoke.jsonl) | Zamówienia z P1.1. Ponownie wykorzystaj plik, który masz w volume, lub dołącz jego kopię z repozytorium. |
| [refunds.parquet](refunds.parquet) | Eksport z systemu zwrotów. Obejmuje identyfikatory zwrotów i zamówień, numer pozycji, datę, status i kwotę w PLN. |

## Zadanie

1. Udostępnij trzy pliki w managed volume. We własnym notebooku wczytaj każdy do PySpark DataFrame. Dla CSV zadeklaruj schemat i uzasadnij dobór typów na podstawie wartości oraz znaczenia biznesowego pól.
2. Przygotuj krótki profil każdego zbioru. Pokaż próbkę i schemat, policz wiersze, opisz co reprezentuje jeden wiersz oraz sprawdź unikalność zaproponowanego klucza. W JSONL wskaż, gdzie odczyt zachował zagnieżdżoną strukturę. Sprawdź, czy klucz zamówienia nadal jest unikalny w pliku zwrotów.
3. Pokaż na zamówieniach przykład wyboru kolumn, filtrowania i akcji. W swoich słowach wyjaśnij, kiedy Spark wykona obliczenia i co dzieje się z liczbą rekordów po samym wyborze kolumn.
4. Udostępnij zamówienia w tej samej sesji jako widok tymczasowy. W Spark SQL sprawdź liczbę wszystkich zamówień oraz liczbę zamówień ze statusem `fulfilled`. Uzgodnij wyniki z PySpark.

## Kryteria odbioru

- Notebook działa od początku po wskazaniu ścieżek do plików. Widać trzy schematy, liczbę wierszy i sprawdzenie kluczy.
- Kod pocztowy zachowuje zera wiodące, puste pole w CSV ma świadomie przyjętą interpretację, a kwota zwrotu ma dokładność zgodną z typem odczytanym z Parquet.
- Profil uwzględnia fakt, że jedno zamówienie może mieć więcej niż jedną pozycję lub zwrot. Widać, że obie wersje obliczeń dają te same wyniki.

Do review prześlij notebook z wynikami oraz krótką notatkę o typach, kluczach i działaniu Spark. W części o researchu wskaż dokumentację, która pomogła Ci podjąć przynajmniej jedną decyzję.
