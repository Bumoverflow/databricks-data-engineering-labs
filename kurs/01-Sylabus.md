# Sylabus kursu Databricks Data Engineering

*Master Syllabus · Dokument 01 · 18 listopada 2026*

[Projekty i Free Edition](02-Projekty-i-Free-Edition.md) · [Macierz certyfikacyjna](03-Macierz-certyfikacyjna.md)

Zbudujesz trzy projekty dla jednego fikcyjnego sklepu. Najpierw uruchomisz wsadowy ETL i raport. Następnie obsłużysz przyrosty i historię zmian. W ostatnim projekcie dodasz streaming, odbudowę stanu i powtarzalne wdrożenia. Każdy moduł ma zadanie, dowód wykonania i pytanie do omówienia.

## Ścieżka nauki

| **Etap** | **Moduły** | **Czas** | **Rezultat końcowy** |
| --- | --- | --- | --- |
| [1 · Beginner](#projekt-1--e-commerce-data-warehouse) | P1.1–P1.6 | 14 h | Działający batch ETL Bronze → Silver → Gold i dashboard sprzedaży. |
| [2 · Intermediate](#projekt-2--incremental-data-platform) | P2.1–P2.7 | 21 h | Przyrostowy load, CDC, SCD Type 1/2 i job odporny na ponowienia. |
| [3 · Advanced](#projekt-3--real-time-data-engineering-platform) | P3.1–P3.7 | 24 h | Przyrostowy streaming, replika CDC, monitoring, testy i ścieżka wdrożenia. |
| [Powtórka](#powtórka-i-próbny-egzamin) | R.1–R.2 | 6 h | Próbny egzamin i diagnoza luk na podstawie siedmiu domen. |
| Łącznie | 22 moduły | 65 h | 20 modułów projektowych oraz 2 moduły powtórkowe. |

Szacunek obejmuje krótkie wprowadzenie, samodzielną pracę i pierwszą rundę poprawek. Przy 5–7 godzinach tygodniowo zaplanuj około 10–13 tygodni. Czas oczekiwania na code review lub reset quota jest dodatkowy.

[Przejdź do Progress Tracker](#progress-tracker)

## Jak pracujemy w każdym module

- Wprowadzenie. Poznasz zastosowanie biznesowe i warunek odbioru. Otrzymasz zadanie, pliki wejściowe, ich kontrakt i spodziewany wynik.
- Samodzielna implementacja. Własnoręcznie napiszesz kod lub wykonasz konfigurację. W razie potrzeby dostaniesz wskazówkę krok po kroku, a kompletne rozwiązanie dostaniesz na wyraźną prośbę.
- Code review. Prześlesz notebook lub diff, identyfikator porcji lub runu i wyniki kontroli. Ocenimy poprawność, jakość, wydajność, zachowanie po ponowieniu i zgodność z dokumentacją.
- Podsumowanie. Odpowiesz na krótkie pytania i zapiszesz wynik w trackerze. Po zaliczeniu kryteriów projektu przejdziesz do następnego poziomu.

Pakiet do akceptacji opisuje zadania na poziomie sylabusa. Pełne instrukcje, pliki i generatory będą dostarczane w kolejności modułów po akceptacji.

**Źródła** [Databricks Free Edition limitations](https://docs.databricks.com/aws/en/getting-started/free-edition-limitations)  ·  [Oficjalna strona certyfikacji Associate](https://www.databricks.com/learn/certification/data-engineer-associate)  ·  [Oficjalny Exam Guide z aktualizacją 6 sierpnia 2026](https://www.databricks.com/sites/default/files/2026-10/Databricks-Certified-Data-Engineer-Associate-Exam-Guide-August-2026.pdf)

## Projekt 1 — E-commerce Data Warehouse

### P1.1 Workspace i pierwszy notebook

*1,5 h   ·   Praktyka + porównanie classic na papierze*

**Technologie** Workspace, Catalog Explorer, Notebook, Python, SQL, serverless compute, Unity Catalog

**Cel** Uruchom pojedynczy notebook i odróżnij warstwę compute od storage i governance.

**Lekcje**

1.  Workspace i komórki Python/SQL
2.  Serverless notebook, serverless job, SQL warehouse oraz classic compute
3.  Catalog → schema → volume/table i kwalifikowane nazwy

**Zadanie** Utwórz własny notebook i obejrzyj próbkę danych z zamówieniami. Wybierz compute dla trzech przypadków i uzasadnij wybór przez sposób uruchamiania, współbieżność i model kosztowy. [Brief i dane wejściowe P1.1](../projects/01-ecommerce/p1-01-workspace/README.md)

**Oczekiwany rezultat** Notebook z prostym wynikiem i trzema decyzjami o compute. Możesz wskazać plik, tabelę i schemat w Catalog Explorer.

**Pytanie sprawdzające** Jaki compute wybierzesz dla analityków wykonujących zapytania SQL w ciągu dnia?

### P1.2 Spark i dane wejściowe

*2,5 h   ·   Praktyka*

**Technologie** Apache Spark, PySpark DataFrames, Spark SQL, CSV, JSON, Parquet, managed volume

**Cel** Wczytaj pliki i odróżnij leniwą transformację od akcji oraz typy od reprezentacji tekstowej.

**Lekcje**

1.  Grain, schema i klucze
2.  CSV z ustalonym schematem, zagnieżdżony JSON i Parquet
3.  select, filter, show, count i widok tymczasowy

**Zadanie** Wgraj próbki z paczki kursu do volume. Porównaj typy, schematy i liczności oraz sprawdź dostęp do tych samych danych z SQL.

**Oczekiwany rezultat** Profil trzech formatów oraz odtwarzalny odczyt wszystkich zbiorów. Przykład transformacji i akcji z objaśnieniem.

**Pytanie sprawdzające** Co zmieni się między transformacją filter a akcją count?

### P1.3 Bronze i Delta Lake

*2,5 h   ·   Praktyka*

**Technologie** Delta Lake, managed Delta tables, Unity Catalog, Spark SQL, PySpark

**Cel** Utwórz surową warstwę z metadanymi pochodzenia i rozpoznaj wersje transakcji Delta.

**Lekcje**

1.  Medallion i kontrakt Bronze
2.  Zapis Delta, manifest i tryby zapisu
3.  DESCRIBE HISTORY oraz time travel

**Zadanie** Załaduj bazowy snapshot i manifest. Zachowaj surowe wartości oraz nazwę źródła i batch_id. Porównaj odczyt dwóch kolejnych wersji na tabeli ćwiczeniowej.

**Oczekiwany rezultat** Dane Bronze dają się uzgodnić z manifestem. Porównanie dwóch wersji pokazuje zaplanowaną zmianę.

**Pytanie sprawdzające** Kiedy time travel pozwala sprawdzić efekt wadliwego zapisu?

### P1.4 Silver i jakość danych

*3 h   ·   Praktyka*

**Technologie** PySpark, Spark SQL, Delta, SQL window functions

**Cel** Ustandaryzuj dane i dopilnuj prawidłowej liczności po przekształceniach.

**Lekcje**

1.  NULL, cast, split, rename, explode i filtry
2.  Inner, left, multi-key, cross i broadcast join
3.  UNION i UNION ALL, deduplikacja oraz quarantine

**Zadanie** Oczyść rekordy i rozwiń pozycje JSON. Porównaj joiny na kilku rekordach, usuń duplikaty według deterministycznego porządku i przypisz przyczyny odrzuceń.

**Oczekiwany rezultat** Silver ma unikalne klucze i poprawne typy. Uzgadniasz zaakceptowane, zduplikowane i odrzucone rekordy z wejściem.

**Pytanie sprawdzające** Jak wykryjesz, że left join zwielokrotnił wartości sprzedaży?

### P1.5 Gold i raportowanie

*2 h   ·   Praktyka*

**Technologie** Spark SQL, Databricks SQL, SQL warehouse, AI/BI Dashboards, dimensions i facts

**Cel** Zdefiniuj grain faktów i dostarcz uzgodnione KPI.

**Lekcje**

1.  Fakt pozycji zamówienia i wymiary
2.  COUNT, AVG, approx_count_distinct i summary i porównanie z dokładną liczbą
3.  Gold table, view i ekran raportu

**Zadanie** Zbuduj model i raport dziennej sprzedaży. Porównaj wyniki SQL z ręcznie policzoną próbką po zwrotach i anulowaniach.

**Oczekiwany rezultat** Tabela faktów, widok KPI i dashboard na jednym SQL warehouse. KPI mają opis grain i definicje biznesowe.

**Pytanie sprawdzające** Kiedy warto użyć approx_count_distinct oraz kiedy koszt przybliżenia jest zbyt wysoki?

### P1.6 Wsadowy job i odbiór

*2,5 h   ·   Praktyka*

**Technologie** Lakeflow Jobs, Notebook task, DAG, run history, parametry

**Cel** Uruchom odtwarzalny pipeline ETL i udokumentuj działanie.

**Lekcje**

1.  Parametry batch_id i snapshot
2.  Zależności Bronze → Silver → Gold
3.  Run now, podgląd statusów i odbiór

**Zadanie** Uruchom trzy zależne taski, po czym ponów ten sam snapshot. Zbierz wyniki kontroli i identyfikatory uruchomień.

**Oczekiwany rezultat** Pipeline end-to-end i raport z dwóch uruchomień. Wynik biznesowy po powtórce pozostaje identyczny.

**Pytanie sprawdzające** W którym miejscu DAG powinna się zatrzymać publikacja przy niespójnym Silver?

## Projekt 2 — Incremental Data Platform

### P2.1 Incremental load i upsert

*2,5 h   ·   Praktyka na volume + opis storage chmurowego*

**Technologie** COPY INTO, SQL warehouse, Unity Catalog volume, Delta MERGE

**Cel** Oddziel wykrywanie nowych plików od rozwiązywania zmian rekordów.

**Lekcje**

1.  Niezmienne pliki i idempotencja COPY INTO
2.  Staging, uporządkowanie zmian i Delta MERGE
3.  Porównanie ADLS, S3, GCS i volume

**Zadanie** Załaduj A i B do staging, ponów B i zastosuj insert/update do tabeli docelowej. Spróbuj dostarczyć ten sam rekord pod inną nazwą pliku.

**Oczekiwany rezultat** Masz dowód, że ponowienie pliku i biznesowy duplikat wymagają osobnych kontroli. Aktualizacja nie przebudowuje historii.

**Pytanie sprawdzające** Co chroni przed ponownym załadowaniem tego samego pliku, a co przed powtórką tego samego event_id?

### P2.2 Auto Loader i zmiana schematu

*3 h   ·   Praktyka dla directory listing + symulacja file events*

**Technologie** Auto Loader, cloudFiles, AvailableNow, checkpoint, schema location, rescued data

**Cel** Przyjmij przyrosty plikowe, obsłuż nowe pole i ujawnij niezgodny typ.

**Lekcje**

1.  Directory listing i rozpoznawanie plików
2.  Schema enforcement, evolution, addNewColumns i rescue
3.  Osobny checkpoint, ponowienie i porównanie file events

**Zadanie** Dostarcz B, C i D kolejno. Przećwicz dodanie opcjonalnej kolumny z kontrolowanym restartem, a w osobnym torze zachowanie niezgodności w rescued data.

**Oczekiwany rezultat** Wynik rozróżnia przyjęte pliki, ewolucję i odrzucone wartości. Ponowne uruchomienie z tym samym checkpointem nie przetwarza starych plików.

**Pytanie sprawdzające** Dlaczego dodanie kolumny w addNewColumns może wymagać ponowienia query?

### P2.3 Wybór i konfiguracja ingestii

*3 h   ·   Praktyka na plikach + symulacja konektorów i sieci*

**Technologie** Lakeflow Connect, REST, JDBC/ODBC, JSON, Parquet, Notebook task, Unity Catalog

**Cel** Dobierz metodę ingestii do źródła i sprawdź kontrakt bez połączenia z cudzą usługą.

**Lekcje**

1.  Standard, managed i partner connectors, gateway i staging
2.  REST pagination, cursor, 429 i ponowienie
3.  Dostęp JDBC/ODBC, nested JSON i dokumenty niestrukturalne
4.  Scenariusz audit log delivery

**Zadanie** Odtwórz lokalne odpowiedzi API z zapisanych stron. Zaprojektuj konfigurację i uprawnienia dla SaaS, bazy SQL i plików. Wczytaj payload JSON i przykładowy plik tekstowy z volume.

**Oczekiwany rezultat** Raport doboru narzędzia, tabela Delta po replay, kursor bez utraty strony, projekt konfiguracji CDC i przykładowy kontrakt dla JDBC/ODBC.

**Pytanie sprawdzające** Które źródło uzasadnia managed connector, a kiedy wystarczy Auto Loader?

### P2.4 Deklaratywny pipeline i expectations

*3 h   ·   Praktyka*

**Technologie** Lakeflow Spark Declarative Pipelines, SQL lub pyspark.pipelines, streaming table, materialized view, expectations

**Cel** Zdefiniuj zależności deklaratywnie i publikuj stan jakości danych.

**Lekcje**

1.  Triggered serverless pipeline
2.  Streaming table, materialized view, zwykły view i tabela
3.  Expectations warn/drop/fail, quarantine i event log

**Zadanie** Zbuduj pipeline Bronze → Silver → Gold. Podaj wadliwą partię i porównaj trzy reakcje na złamaną regułę. Umieść gałąź quarantine tam, gdzie nadal są dostępne odrzucane rekordy.

**Oczekiwany rezultat** Masz działające streaming table i materialized view, zapisane wyniki aktualizacji i wskazaną regułę powodującą błąd.

**Pytanie sprawdzające** Co zobaczy odbiorca, gdy zmienisz regułę jakości z warn na drop albo fail?

### P2.5 CDC i wymiary zmienne w czasie

*4 h   ·   Praktyka AUTO CDC + symulowany feed źródłowy*

**Technologie** Lakeflow AUTO CDC, Delta MERGE, SCD Type 1, SCD Type 2, sekwencja i tombstone

**Cel** Zbuduj stan bieżący i historię klienta na podstawie nieuporządkowanego feedu zmian.

**Lekcje**

1.  CDC z operacją I/U/D i deterministycznym kluczem sekwencji
2.  AUTO CDC i porównanie z ręcznym MERGE Type 1
3.  Przedziały Type 2, delete i point-in-time lookup

**Zadanie** Przetwórz syntetyczne insert/update/delete, duplikat i zmianę poza kolejnością. Porównaj stan bieżący oraz historię w obydwu modelach.

**Oczekiwany rezultat** Wyniki są zgodne z manifestem. Dla klienta istnieje co najwyżej jedna wersja aktywna, a jego przedziały nie nakładają się.

**Pytanie sprawdzające** Jak zmiana, która dotarła po późniejszej aktualizacji, wpływa na Type 1 i Type 2?

### P2.6 Orkiestracja i naprawa błędów

*3 h   ·   Praktyka + wariant harmonogramu, gdy trigger lub task jest niedostępny*

**Technologie** Lakeflow Jobs, notebook, SQL query, dashboard i pipeline tasks, If/else, For each, task values

**Cel** Zautomatyzuj dostarczenie danych i odzyskaj uszkodzony run bez dublowania wyników.

**Lekcje**

1.  DAG i cztery typy tasków
2.  Scheduled, file arrival i table update triggers
3.  Retries, timeout, If/else, For each oraz Repair run

**Zadanie** Ustaw krótki harmonogram treningowy, wypróbuj rozgałęzienie i For each, a po kontrolowanym błędzie napraw run. Porównaj dobór pozostałych triggerów i przetestuj je, jeśli UI pozwoli.

**Oczekiwany rezultat** DAG i raport z naprawy pokazują zależności, próbę ponowienia oraz zachowanie idempotencji. Wybór triggera ma uzasadnienie.

**Pytanie sprawdzające** Czym różni się retry pojedynczego taska od Repair run po usunięciu przyczyny błędu?

### P2.7 Monitoring i lineage

*2,5 h   ·   Praktyka*

**Technologie** Lakeflow Jobs run history, pipeline UI, event log, Catalog Explorer, Query Profile

**Cel** Powiąż problem jakości lub wydajności z krokiem pipeline’u i jego odbiorcami.

**Lekcje**

1.  Trend czasów i odsetek błędów
2.  Rozpoznawanie blokady zależności i przyczyn w logach
3.  Data lineage, baseline i dokumentacja odbioru

**Zadanie** Porównaj udany i celowo nieudany run. Znajdź źródło i odbiorcę jednej kolumny lub tabeli, następnie zanotuj koszt względny full reload i przyrostu.

**Oczekiwany rezultat** Masz tabelę pomiarów, wycinek logu i udokumentowany wpływ awarii na Gold. Tabela odbiorcza nie zawiera duplikatów po naprawie.

**Pytanie sprawdzające** Gdzie sprawdzisz, czy długi czas Gold wynikał z SQL, czy z oczekiwania na upstream?

## Projekt 3 — Real-Time Data Engineering Platform

### P3.1 Streaming i checkpointy

*3 h   ·   Praktyka*

**Technologie** Structured Streaming, Auto Loader lub jawny JSON file source, Delta, AvailableNow

**Cel** Uruchom inkrementalny stream z kontrolowanymi wznowieniami.

**Lekcje**

1.  Record, micro-batch, source i sink
2.  Event time i arrival time
3.  Offset, checkpoint i restart

**Zadanie** Dostarcz porcje zdarzeń do volume, uruchom stream i powtórz go po dostarczeniu następnej porcji. Na osobnym torze pokaż efekt nowego checkpointu.

**Oczekiwany rezultat** Bronze rejestruje nowe porcje bez ponownego odczytu starych przy reużyciu checkpointu. Odrębny run demonstruje ryzyko replay.

**Pytanie sprawdzające** Co grozi po skierowaniu źródła ze starymi plikami do nowego checkpointu i istniejącego sinka?

### P3.2 Watermarki i okna

*4 h   ·   Praktyka*

**Technologie** Structured Streaming, event-time windows, withWatermark, dropDuplicatesWithinWatermark, Delta

**Cel** Ogranicz stan i policz alerty lub KPI mimo opóźnień zdarzeń.

**Lekcje**

1.  Tumbling window i append mode
2.  Dedup po event_id z watermarkiem
3.  Stan, późne rekordy i finalizacja okna

**Zadanie** Użyj oddzielnych zapytań do deduplikacji i agregacji. Dodaj rekordy przed i po progu oraz kolejną porcję przesuwającą maksimum event time.

**Oczekiwany rezultat** Porównanie z manifestem pokazuje, które zdarzenia i okna weszły do wyniku, kiedy okno zostało opublikowane oraz jak zachował się duplikat.

**Pytanie sprawdzające** Dlaczego samo upłynięcie czasu zegarowego nie wystarczy do przesunięcia watermarku?

### P3.3 Streaming CDC i operacje Delta

*3 h   ·   Praktyka*

**Technologie** Delta Change Data Feed, table_changes, readChangeFeed, Delta MERGE, time travel

**Cel** Przenieś zmiany z mutowalnej tabeli do odbiorcy i sprawdź granice replay.

**Lekcje**

1.  CDF, wersje i change types
2.  Wznowienie z checkpointu i jawna wersja startowa w kontrolowanym replay
3.  Idempotentny upsert/delete, retention i restore na kopii

**Zadanie** Przeczytaj zmiany Delta przez stream do staging. Zastosuj przyrost do tabeli odbiorczej, sprawdź update preimage/postimage i delete. Przetestuj replay tego samego zakresu.

**Oczekiwany rezultat** Stan odbiorcy zgadza się ze źródłem dla wybranej wersji. Zapisany zakres wersji pozwala zweryfikować efekt ponowienia.

**Pytanie sprawdzające** Dlaczego zwykły odczyt streamingowy tabeli z update/delete może wymagać CDF?

### P3.4 Testy i odzyskiwanie po awarii

*3,5 h   ·   Praktyka*

**Technologie** Python unittest, Spark/SQL integration tests, Delta audit table, Lakeflow Jobs

**Cel** Zweryfikuj kontrakty danych i zachowanie przy awarii między zapisami.

**Lekcje**

1.  Test jednostkowy i mały test integracyjny
2.  Kontrola DQ, metryki i wskaźnik świeżości
3.  Awaria po zapisie, retry i backfill

**Zadanie** Dodaj testy nulli, kluczy, CDC, duplikatów i late data. Wstrzymaj job po zapisie i przed oznaczeniem sukcesu, następnie ponów go i przeprowadź backfill na osobnym torze.

**Oczekiwany rezultat** Testy i audit table rozliczają wejścia i wyjścia. Odzyskanie daje ten sam stan końcowy. Runbook wskazuje źródło i ograniczenia replay.

**Pytanie sprawdzające** Co uchroni drugi sink przed podwójnym zapisem po częściowym sukcesie?

### P3.5 Optymalizacja i diagnoza

*3 h   ·   Praktyka z Query Profile + materiał Spark UI i classic*

**Technologie** EXPLAIN, Query Profile, Spark conf, Liquid Clustering, OPTIMIZE, Delta history

**Cel** Zmierz efekt optymalizacji i rozpoznaj ograniczenia serverless.

**Lekcje**

1.  Shuffle, skew oraz spill w planie, profilu i przykładzie Spark UI
2.  Broadcast i dozwolone Spark configs
3.  Liquid Clustering, predictive optimization i małe pliki

**Zadanie** Porównaj dwa warianty zapytania i zmierz skan lub czas kilku prób. Na małej tabeli przećwicz Liquid Clustering/OPTIMIZE. Przypisz przykładowe logi do błędu rozruchu, bibliotek lub pamięci.

**Oczekiwany rezultat** Zapis pomiarów z tym samym wynikiem danych i uzasadnieniem, kiedy optymalizacja pomaga. Poprawnie opisujesz parametry oraz metryki niedostępne w serverless.

**Pytanie sprawdzające** Która metryka odróżni skew pojedynczego taska od równomiernego, powolnego shuffle?

### P3.6 Unity Catalog i ochrona danych

*3 h   ·   Praktyka + symulacja tożsamości, external i polityk*

**Technologie** Catalog Explorer, GRANT, REVOKE, SHOW GRANTS, managed/external, row filters, column masks, ABAC

**Cel** Zaprojektuj dostęp do surowych i publikowanych danych przy minimalnych uprawnieniach.

**Lekcje**

1.  Własność, dziedziczenie i principals
2.  Cykl życia tabel oraz konwersja i rollback
3.  Row filters, column masks, governed tags i ABAC DENY (Beta)

**Zadanie** Dodaj i usuń własne bezpośrednie uprawnienie na obiekcie testowym, sprawdź wpisy w SQL i UI. W laboratorium z jednym użytkownikiem porównaj widok maskowany z testami predykatu, a w symulacji rozpisz dostęp dla grup i service principal.

**Oczekiwany rezultat** Zapis przed/po zmianie uprawnień, widok z zamaskowanym polem oraz macierz dostępu, cykl managed/external i decyzje ABAC.

**Pytanie sprawdzające** Kiedy cofnięcie bezpośredniego GRANT nadal pozostawi użytkownikowi dostęp do tabeli?

### P3.7 Git, Bundles i CI/CD

*4,5 h   ·   Praktyka warunkowa dla Git folders i deploy + lokalne CI, symulacja prod*

**Technologie** Git folders, Git, pull request, Databricks CLI, Declarative Automation Bundles, Lakeflow Jobs

**Cel** Zaprojektuj powtarzalne dostarczenie przetestowanego pipeline’u oraz rollback.

**Lekcje**

1.  Branch, commit, push i pull request
2.  databricks.yml, resources, variables, overrides i targets
3.  validate, deploy, run, test gates, promocja i rollback

**Zadanie** Zrób zmianę na branchu i przeprowadź testy. Zweryfikuj konfiguracje dev/test/prod, a jeśli dostęp pozwala, wdróż i uruchom mały job w dev. Zasymuluj gate i rollback do poprzedniej rewizji.

**Oczekiwany rezultat** Masz historię Git, dowód walidacji lub symulacji oraz dowód wdrożenia dev lub testowego uruchomienia joba przez UI. Schematy i checkpointy środowisk są rozdzielone.

**Pytanie sprawdzające** Jak zapobiegniesz wskazywaniu na checkpoint z dev po promocji tej samej wersji kodu?

## Powtórka i próbny egzamin

### R.1 Powtórka według luk

*3 h   ·   Powtórka*

**Technologie** Macierz certyfikacyjna, SQL, Python, karty przypadków

**Cel** Uzupełnij cele, dla których zabrakło dowodu opanowania.

**Lekcje**

1.  Siedem domen i przegląd dowodów
2.  Szybkie powtórki SQL/PySpark
3.  Scenariusze symulowane i korekta błędów

**Zadanie** Wybierz zadanie z dwóch najsłabszych domen. Odtwórz wybrany incydent z course fixtures i wyjaśnij dwa warianty rozwiązania.

**Oczekiwany rezultat** Każda domena ma dowód praktyczny lub kartę symulacji. Zapisujesz trzy błędy i poprawioną zasadę dla każdego.

**Pytanie sprawdzające** Jakie zagadnienie potrafisz wyjaśnić, lecz wymaga jeszcze demonstracji?

### R.2 Próbny egzamin i omówienie

*3 h   ·   Próbny egzamin*

**Technologie** Autorskie pytania multiple choice, arkusz wyników, dokumentacja Databricks

**Cel** Zmierz gotowość na pytania scenariuszowe i zaplanuj powtórkę.

**Lekcje**

1.  90 minut bez pomocy
2.  Punktacja według domen
3.  Korekta odpowiedzi i plan doszkolenia

**Zadanie** Rozwiąż 45 pytań po angielsku. Potem sprawdź klucz po polsku, przypisz błędy do domen i uzasadnij poprawione odpowiedzi.

**Oczekiwany rezultat** Wynik ogólny i per domena oraz lista celów do powtórzenia. Próg szkoleniowy wynosi 36/45 i co najmniej 2/3 poprawnych odpowiedzi w każdej domenie.

**Pytanie sprawdzające** W których pytaniach zadecydował błąd w rozumieniu ograniczeń compute lub uprawnień?

## Progress Tracker

Wpisz datę, dowód i status. Możliwe statusy to do zrobienia, w trakcie, do review, poprawki i zaliczone. Zaliczenie wymaga wyniku spełniającego kryterium modułu oraz zapisanej odpowiedzi na pytanie sprawdzające.

| **Moduł** | **Nazwa** | **Czas** | **Status** | **Data i dowód** |
| --- | --- | --- | --- | --- |
| [P1.1](#p11-workspace-i-pierwszy-notebook) | Workspace i pierwszy notebook | 1,5 h | W trakcie |  |
| [P1.2](#p12-spark-i-dane-wejściowe) | Spark i dane wejściowe | 2,5 h | Do zrobienia |  |
| [P1.3](#p13-bronze-i-delta-lake) | Bronze i Delta Lake | 2,5 h | Do zrobienia |  |
| [P1.4](#p14-silver-i-jakość-danych) | Silver i jakość danych | 3 h | Do zrobienia |  |
| [P1.5](#p15-gold-i-raportowanie) | Gold i raportowanie | 2 h | Do zrobienia |  |
| [P1.6](#p16-wsadowy-job-i-odbiór) | Wsadowy job i odbiór | 2,5 h | Do zrobienia |  |
| [P2.1](#p21-incremental-load-i-upsert) | Incremental load i upsert | 2,5 h | Do zrobienia |  |
| [P2.2](#p22-auto-loader-i-zmiana-schematu) | Auto Loader i zmiana schematu | 3 h | Do zrobienia |  |
| [P2.3](#p23-wybór-i-konfiguracja-ingestii) | Wybór i konfiguracja ingestii | 3 h | Do zrobienia |  |
| [P2.4](#p24-deklaratywny-pipeline-i-expectations) | Deklaratywny pipeline i expectations | 3 h | Do zrobienia |  |
| [P2.5](#p25-cdc-i-wymiary-zmienne-w-czasie) | CDC i wymiary zmienne w czasie | 4 h | Do zrobienia |  |
| [P2.6](#p26-orkiestracja-i-naprawa-błędów) | Orkiestracja i naprawa błędów | 3 h | Do zrobienia |  |
| [P2.7](#p27-monitoring-i-lineage) | Monitoring i lineage | 2,5 h | Do zrobienia |  |
| [P3.1](#p31-streaming-i-checkpointy) | Streaming i checkpointy | 3 h | Do zrobienia |  |
| [P3.2](#p32-watermarki-i-okna) | Watermarki i okna | 4 h | Do zrobienia |  |
| [P3.3](#p33-streaming-cdc-i-operacje-delta) | Streaming CDC i operacje Delta | 3 h | Do zrobienia |  |
| [P3.4](#p34-testy-i-odzyskiwanie-po-awarii) | Testy i odzyskiwanie po awarii | 3,5 h | Do zrobienia |  |
| [P3.5](#p35-optymalizacja-i-diagnoza) | Optymalizacja i diagnoza | 3 h | Do zrobienia |  |
| [P3.6](#p36-unity-catalog-i-ochrona-danych) | Unity Catalog i ochrona danych | 3 h | Do zrobienia |  |
| [P3.7](#p37-git-bundles-i-cicd) | Git, Bundles i CI/CD | 4,5 h | Do zrobienia |  |
| [R.1](#r1-powtórka-według-luk) | Powtórka według luk | 3 h | Do zrobienia |  |
| [R.2](#r2-próbny-egzamin-i-omówienie) | Próbny egzamin i omówienie | 3 h | Do zrobienia |  |

Dowód może mieć formę linku do notebooka, identyfikatora runu, wyniku testu, krótkiej karty symulacji lub wyniku próbnego egzaminu.
