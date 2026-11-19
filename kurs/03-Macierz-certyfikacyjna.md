# Macierz pokrycia certyfikacji Associate

*Databricks Certified Data Engineer Associate · Dokument 03 · 18 listopada 2026*

[Sylabus i Progress Tracker](01-Sylabus.md) · [Projekty i Free Edition](02-Projekty-i-Free-Edition.md)

Macierz przypisuje wszystkie 33 cele z oficjalnego Exam Guide do modułów, sposobu ćwiczenia i dowodu wykonania. Przewodnik jest podlinkowany na oficjalnej stronie. Podaje datę publikacji egzaminu 4 maja 2026 i aktualizację przewodnika 6 sierpnia 2026.

| **Domena** | **Waga** | **Próbny** |
| --- | --- | --- |
| Databricks Intelligence Platform | 6% | 3 |
| Data Ingestion and Loading | 21% | 9 |
| Data Transformation and Modeling | 22% | 10 |
| Working with Lakeflow Jobs | 16% | 7 |
| Implementing CI CD | 10% | 5 |
| Troubleshooting Monitoring and Optimization | 10% | 4 |
| Governance and Security | 15% | 7 |

Egzamin ma 45 punktowanych pytań i 90 minut. Możliwe jest do 10 dodatkowych pytań bez punktów. Opłata za zapis wynosi 200 USD plus należne podatki. Projekty, powtórka i autorski test są samodzielną ścieżką nauki. Sprawdź guide ponownie dwa tygodnie przed egzaminem.

## Domena 1 — Databricks Intelligence Platform

| **Cel z przewodnika** | **Moduł i tryb** | **Dowód opanowania** |
| --- | --- | --- |
| 1.1  Architektura Lakehouse, Delta Lake i Unity Catalog. | [P1.1](01-Sylabus.md#p11-workspace-i-pierwszy-notebook), [P1.3](01-Sylabus.md#p13-bronze-i-delta-lake) · Praktyka | Wskaż compute, storage i governance na schemacie. Pokaż transakcję Delta, historię i ścieżkę do tabeli. |
| 1.2  Charakterystyka, limity i modele kosztowe compute. Dobór do obciążenia. | [P1.1](01-Sylabus.md#p11-workspace-i-pierwszy-notebook), [P1.6](01-Sylabus.md#p16-wsadowy-job-i-odbiór) · Praktyka + symulacja | Dobierz serverless notebook/job albo SQL warehouse. Na kartach porównaj all-purpose, job i classic compute, rozruch, autoscaling oraz zużycie DBU i koszt infrastruktury. |

**Źródła** [Oficjalna strona certyfikacji Associate](https://www.databricks.com/learn/certification/data-engineer-associate)  ·  [Oficjalny Exam Guide z aktualizacją 6 sierpnia 2026](https://www.databricks.com/sites/default/files/2026-10/Databricks-Certified-Data-Engineer-Associate-Exam-Guide-August-2026.pdf)  ·  [Databricks Free Edition limitations](https://docs.databricks.com/aws/en/getting-started/free-edition-limitations)  ·  [Free Edition oraz Free Trial](https://docs.databricks.com/aws/en/getting-started/free-trial-vs-free-edition)  ·  [Serverless compute limitations](https://docs.databricks.com/aws/en/compute/serverless/limitations)

## Plan weryfikacji wiedzy

Po każdym module sprawdzisz wynik praktyczny i odpowiesz na pytania scenariuszowe. W R.1 przejrzysz luki według domen. R.2 obejmuje autorskie pytania po angielsku, klucz z omówieniem po polsku i powtórkę błędów według celu. Rozkład próbnego egzaminu przybliża oficjalne wagi.

## Domena 2 — Data Ingestion and Loading

*Waga oficjalna 21% · Pytania na próbnym egzaminie 9*

| **Cel z przewodnika** | **Moduł i tryb** | **Dowód opanowania** |
| --- | --- | --- |
| 2.1  Batch, streaming i incremental load. Local files oraz standard/managed connectors. | [P1.2](01-Sylabus.md#p12-spark-i-dane-wejściowe), [P2.1](01-Sylabus.md#p21-incremental-load-i-upsert)–[P2.3](01-Sylabus.md#p23-wybór-i-konfiguracja-ingestii), [P3.1](01-Sylabus.md#p31-streaming-i-checkpointy) · Praktyka + symulacja | Wgraj pliki lokalne i odtwórz trzy wzorce przepływu. Dopasuj typ konektora do źródła i określ uprawnienia. |
| 2.2  COPY INTO z ADLS, S3 lub GCS do tabeli zgodnej z Unity Catalog. | [P2.1](01-Sylabus.md#p21-incremental-load-i-upsert) · Praktyka + symulacja | COPY INTO z /Volumes i powtórka tej samej partii. Rozpisz osobno cloud URI, storage credential, external location i uprawnienia. |
| 2.3  Auto Loader, schema enforcement/evolution i tryby odnajdywania nowych plików. | [P2.2](01-Sylabus.md#p22-auto-loader-i-zmiana-schematu), [P3.1](01-Sylabus.md#p31-streaming-i-checkpointy) · Praktyka + symulacja | Directory listing, AvailableNow, rescued data, restart po zmianie i checkpoint. Na schemacie omów file notification i managed file events. |
| 2.4  Konfiguracja Lakeflow Connect dla źródeł enterprise i Unity Catalog. | [P2.3](01-Sylabus.md#p23-wybór-i-konfiguracja-ingestii), [P2.5](01-Sylabus.md#p25-cdc-i-wymiary-zmienne-w-czasie) · Symulacja + lokalny feed | Zaprojektuj connection, source, gateway, staging, pipeline, sink, uprawnienia, retry i checkpoint. Odtwórz feed I/U/D bez źródłowej bazy. |
| 2.5  JDBC/ODBC lub REST w notebookach, cloud storage lub tabela UC, automatyzacja. | [P2.3](01-Sylabus.md#p23-wybór-i-konfiguracja-ingestii), [P2.6](01-Sylabus.md#p26-orkiestracja-i-naprawa-błędów) · Praktyka + symulacja | Odtwórz zapisane strony REST, błąd 429 i kursor. Zaprojektuj JDBC/ODBC z auth/schemą. Notebook task zapisuje wynik replay do UC. |
| 2.6  Wybór Auto Loader, Lakeflow Connect, partner connectors i innych ścieżek. | [P2.3](01-Sylabus.md#p23-wybór-i-konfiguracja-ingestii) · Symulacja decyzyjna | Uzupełnij kartę dla plików, relacyjnej bazy i SaaS. Uzasadnij wybór przez typ, wolumen, częstotliwość, CDC i governance. |
| 2.7  Dane semi-structured i unstructured, managed connectors, Delta w Unity Catalog. | [P1.2](01-Sylabus.md#p12-spark-i-dane-wejściowe), [P2.3](01-Sylabus.md#p23-wybór-i-konfiguracja-ingestii)–[P2.4](01-Sylabus.md#p24-deklaratywny-pipeline-i-expectations) · Praktyka + symulacja | Wczytaj nested JSON i dokument tekstowy. Ustal kontrakt payload/metadane, obsługę ewolucji i docelowe tabele. Konektor odegraj z fixtures. |

Dodatkowy scenariusz z Exam Guide obejmuje audit log delivery. Karta P2.3 ćwiczy interpretację JSON, typowego opóźnienia i możliwości nadpisania pliku przez dostawcę.

**Źródła** [Oficjalny Exam Guide z aktualizacją 6 sierpnia 2026](https://www.databricks.com/sites/default/files/2026-10/Databricks-Certified-Data-Engineer-Associate-Exam-Guide-August-2026.pdf)  ·  [Volumes i format ścieżki](https://docs.databricks.com/aws/en/files/volumes)  ·  [COPY INTO z Unity Catalog volume](https://docs.databricks.com/aws/en/ingestion/cloud-object-storage/copy-into/tutorial-notebook)  ·  [Auto Loader i discovery plików](https://docs.databricks.com/aws/en/ingestion/cloud-object-storage/auto-loader)  ·  [Auto Loader schema inference i evolution](https://docs.databricks.com/aws/en/ingestion/cloud-object-storage/auto-loader/schema)  ·  [Lakeflow Connect i rodzaje konektorów](https://docs.databricks.com/aws/en/ingestion/overview)  ·  [Databricks audit log delivery](https://docs.databricks.com/aws/en/admin/account-settings/audit-log-delivery)

## Domena 3 — Data Transformation and Modeling

*Waga oficjalna 22% · Pytania na próbnym egzaminie 10*

| **Cel z przewodnika** | **Moduł i tryb** | **Dowód opanowania** |
| --- | --- | --- |
| 3.1  Czyszczenie Bronze w PySpark/SQL, NULL i cast, zapis Silver. | [P1.3](01-Sylabus.md#p13-bronze-i-delta-lake)–[P1.4](01-Sylabus.md#p14-silver-i-jakość-danych) · Praktyka | Uzgodnij liczności Bronze i Silver oraz utrwal standard typów i odrzuty. |
| 3.2  Inner, left, broadcast, multi-key i cross joins, union i union all. | [P1.4](01-Sylabus.md#p14-silver-i-jakość-danych), [P3.5](01-Sylabus.md#p35-optymalizacja-i-diagnoza) · Praktyka | Porównaj cardinality i duplikaty na małym fixture. Uzasadnij broadcast małego wymiaru i obejrzyj plan. |
| 3.3  Dodawanie, usuwanie, dzielenie i zmiana nazw kolumn, filtrowanie i explode. | [P1.4](01-Sylabus.md#p14-silver-i-jakość-danych) · Praktyka | Rozwiń pozycje zamówienia i znormalizuj pola. Wskaż zmianę grain po explode. |
| 3.4  Deduplikacja, count, approx count distinct, mean i summary. | [P1.4](01-Sylabus.md#p14-silver-i-jakość-danych)–[P1.5](01-Sylabus.md#p15-gold-i-raportowanie), [P3.2](01-Sylabus.md#p32-watermarki-i-okna) · Praktyka | Zastosuj deterministyczną deduplikację, policz KPI i porównaj exact z approx. Obejrzyj podsumowanie kolumn. |
| 3.5  Tuning Spark i ponowny pomiar. spark.sql.shuffle.partitions, spark.default.parallelism, spark.executor.memory, spark.driver.memory, spark.sql.autoBroadcastJoinThreshold. | [P3.5](01-Sylabus.md#p35-optymalizacja-i-diagnoza) · Praktyka + symulacja | Zmierz bezpieczny wariant serverless z dostępną konfiguracją i porównaj broadcast. Parametry pamięci, równoległości classic i niedostępne ustawienia oceń na fragmencie konfiguracji. |
| 3.6  Dobór i budowa Gold table, view, materialized view oraz streaming table. | [P1.5](01-Sylabus.md#p15-gold-i-raportowanie), [P2.4](01-Sylabus.md#p24-deklaratywny-pipeline-i-expectations) · Praktyka | Porównaj odświeżanie, trwałość i konsumowanie czterech typów obiektów pod kątem BI i danych przyrostowych. |
| 3.7  Reguły jakości i walidacja Silver oraz Gold. | [P1.4](01-Sylabus.md#p14-silver-i-jakość-danych), [P2.4](01-Sylabus.md#p24-deklaratywny-pipeline-i-expectations), [P3.4](01-Sylabus.md#p34-testy-i-odzyskiwanie-po-awarii) · Praktyka | Sprawdź unikalność i spójność kluczy, porównaj warn/drop/fail oraz weryfikuj Gold względem kontraktu. |

P1.5 obejmuje profil kolumn przez summary i porównanie wyniku COUNT, approx_count_distinct oraz AVG z wynikiem referencyjnym.

**Źródła** [Oficjalny Exam Guide z aktualizacją 6 sierpnia 2026](https://www.databricks.com/sites/default/files/2026-10/Databricks-Certified-Data-Engineer-Associate-Exam-Guide-August-2026.pdf)  ·  [Lakeflow expectations i zasady jakości](https://docs.databricks.com/aws/en/ldp/expectations)  ·  [Diagnostyka obciążeń serverless](https://docs.databricks.com/aws/en/compute/serverless/best-practices)  ·  [Parametry Spark obsługiwane przez Databricks](https://docs.databricks.com/aws/en/spark/conf)

## Domena 4 — Working with Lakeflow Jobs

*Waga oficjalna 16% · Pytania na próbnym egzaminie 7*

| **Cel z przewodnika** | **Moduł i tryb** | **Dowód opanowania** |
| --- | --- | --- |
| 4.1  Sterowanie wykonaniem, retries, gałęzie i pętle. | [P1.6](01-Sylabus.md#p16-wsadowy-job-i-odbiór), [P2.6](01-Sylabus.md#p26-orkiestracja-i-naprawa-błędów), [P3.4](01-Sylabus.md#p34-testy-i-odzyskiwanie-po-awarii) · Praktyka | Użyj If/else, For each i parametrów. Wymuś porażkę taska i pokaż recovery bez podwójnego zapisu. |
| 4.2  Notebook, SQL query, dashboard i pipeline tasks oraz zależności DAG. | [P1.6](01-Sylabus.md#p16-wsadowy-job-i-odbiór), [P2.6](01-Sylabus.md#p26-orkiestracja-i-naprawa-błędów) · Praktyka + warunkowo | Zbuduj DAG i przypisz cztery typy tasków. Jeśli Dashboard task jest niedostępny, rozrysuj konfigurację i odśwież po SQL task w UI. |
| 4.3  Scheduled, file arrival i table update triggers. | [P2.6](01-Sylabus.md#p26-orkiestracja-i-naprawa-błędów) · Praktyka + warunkowo | Uruchom scheduled trigger. Sprawdź możliwość file arrival na volume i table update na Delta. Wariant z Run now odtwarza warunek gotowości. |
| 4.4  Dobór time-based lub data-driven triggers do zależności i dostępności wejścia. | [P2.6](01-Sylabus.md#p26-orkiestracja-i-naprawa-błędów), [P3.1](01-Sylabus.md#p31-streaming-i-checkpointy) · Praktyka + przypadek | Porównaj koszt pustych przebiegów, opóźnienie, arrival pozorowany porcjami i aktualizację tabeli upstream. |

**Źródła** [Oficjalny Exam Guide z aktualizacją 6 sierpnia 2026](https://www.databricks.com/sites/default/files/2026-10/Databricks-Certified-Data-Engineer-Associate-Exam-Guide-August-2026.pdf)  ·  [Lakeflow Jobs schedules i triggers](https://docs.databricks.com/gcp/en/jobs/triggers)  ·  [File arrival i wymagania ścieżki](https://docs.databricks.com/aws/en/jobs/file-arrival-triggers)  ·  [Table update trigger](https://docs.databricks.com/aws/en/jobs/trigger-table-update)

## Domena 5 — Implementing CI/CD

*Waga oficjalna 10% · Pytania na próbnym egzaminie 5*

| **Cel z przewodnika** | **Moduł i tryb** | **Dowód opanowania** |
| --- | --- | --- |
| 5.1  Branch, switch, commit, push i pull request w Databricks Git folders. | [P3.7](01-Sylabus.md#p37-git-bundles-i-cicd) · Warunkowo + praktyka lokalna | Sprawdź operacje na własnym bezpłatnym repo. Gdy Git folders nie jest dostępny, wykonaj Git lokalnie i review w formie PR lub lokalnego diff. |
| 5.2  Bundle variables i overrides, ta sama baza kodu dla dev/test/prod. | [P3.7](01-Sylabus.md#p37-git-bundles-i-cicd) · Praktyka + symulacja | Porównaj trzy targety, rozwiązane wartości zmiennych i rozdział schema/checkpoint. Zaprojektuj przekazanie sekretu w CI bez wpisywania wartości do repo. |
| 5.3  Pakowanie i wdrażanie Jobs, Pipelines i workspace assets z Bundles. | [P3.7](01-Sylabus.md#p37-git-bundles-i-cicd) · Warunkowo + symulacja | Opisz zasoby job i pipeline. Wdróż mały dev job jeśli masz dostęp. Odtwórz promocję i rollback na schemacie. Uruchom job przez UI w wariancie zastępczym. |
| 5.4  Databricks CLI w CI/CD do walidacji, wdrożeń i obsługi zasobów. | [P3.7](01-Sylabus.md#p37-git-bundles-i-cicd) · Warunkowo + praktyka lokalna | Po autoryzacji sprawdź bundle validate, deploy i run. Lokalny gate wykonuje testy. Gdy brakuje dostępu, czytaj przykładowe logi komend i zasymuluj decyzję gate. |

Git host jest opcjonalny dla ukończenia projektu. W dostępnym wariancie można utworzyć PR w interfejsie dostawcy z gałęzi używanej przez Git folders. Zmienne niesekretne i przekazywanie sekretów są omawiane oddzielnie.

**Źródła** [Oficjalny Exam Guide z aktualizacją 6 sierpnia 2026](https://www.databricks.com/sites/default/files/2026-10/Databricks-Certified-Data-Engineer-Associate-Exam-Guide-August-2026.pdf)  ·  [Databricks Git folders i operacje Git](https://docs.databricks.com/aws/en/repos/git-operations-with-repos)  ·  [Databricks CLI i polecenia bundle](https://docs.databricks.com/aws/en/dev-tools/cli/bundle-commands)  ·  [OAuth user-to-machine dla CLI](https://docs.databricks.com/aws/en/dev-tools/auth/oauth-u2m)  ·  [Bundle i pliki konfiguracyjne](https://docs.databricks.com/aws/en/dev-tools/bundles/settings)

## Domena 6 — Troubleshooting, Monitoring, and Optimization

*Waga oficjalna 10% · Pytania na próbnym egzaminie 4*

| **Cel z przewodnika** | **Moduł i tryb** | **Dowód opanowania** |
| --- | --- | --- |
| 6.1  Historia wykonań Jobs i trendy względem wcześniejszych czasów. | [P2.7](01-Sylabus.md#p27-monitoring-i-lineage), [P3.4](01-Sylabus.md#p34-testy-i-odzyskiwanie-po-awarii) · Praktyka | Zapisz czasy kilku runów i porównaj medianę lub zakres w tym samym scenariuszu. |
| 6.2  Statusy, upstream blockers, czasy i failure rates w Lakeflow Jobs UI i DAG. | [P2.6](01-Sylabus.md#p26-orkiestracja-i-naprawa-błędów)–[P2.7](01-Sylabus.md#p27-monitoring-i-lineage) · Praktyka | Od awarii w DAG przejdź do logu i czasu taska. Policz odsetek błędów z prób i sprawdź Repair run. |
| 6.3  Spark UI stage metrics, data skew, shuffle i spill. | [P3.5](01-Sylabus.md#p35-optymalizacja-i-diagnoza) · Praktyka + symulacja | Przeanalizuj Query Profile oraz gotową tabelę metryk Spark UI z medianą i maksimum per task. Wskaż osobno skew, shuffle i disk spill. |
| 6.4  Liquid Clustering i predictive optimization. | [P3.5](01-Sylabus.md#p35-optymalizacja-i-diagnoza) · Praktyka + symulacja | Użyj CLUSTER BY/OPTIMIZE na tabeli próbnej. Wyjaśnij automatyzację maintenance, zakres managed tables oraz gdzie sprawdzić konfigurację. |
| 6.5  Diagnoza rozruchu klastra, konfliktów bibliotek i OOM. | [P3.5](01-Sylabus.md#p35-optymalizacja-i-diagnoza) · Karty incydentów | Na przykładowych komunikatach wybierz etap awarii i kontrolę potwierdzającą hipotezę. Odtwórz bezpieczny błąd walidacji w jobie. |

**Źródła** [Oficjalny Exam Guide z aktualizacją 6 sierpnia 2026](https://www.databricks.com/sites/default/files/2026-10/Databricks-Certified-Data-Engineer-Associate-Exam-Guide-August-2026.pdf)  ·  [Serverless compute limitations](https://docs.databricks.com/aws/en/compute/serverless/limitations)  ·  [Event log pipeline’u](https://docs.databricks.com/aws/en/ldp/monitor-event-logs)  ·  [Diagnostyka obciążeń serverless](https://docs.databricks.com/aws/en/compute/serverless/best-practices)  ·  [Parametry Spark obsługiwane przez Databricks](https://docs.databricks.com/aws/en/spark/conf)  ·  [Liquid Clustering](https://docs.databricks.com/aws/en/tables/clustering)  ·  [Predictive optimization dla tabel managed](https://docs.databricks.com/aws/en/optimizations/predictive-optimization)

## Domena 7 — Governance and Security

*Waga oficjalna 15% · Pytania na próbnym egzaminie 7*

| **Cel z przewodnika** | **Moduł i tryb** | **Dowód opanowania** |
| --- | --- | --- |
| 7.1  Managed i external tables. Create, modify, delete i konwersja. | [P1.3](01-Sylabus.md#p13-bronze-i-delta-lake), [P3.6](01-Sylabus.md#p36-unity-catalog-i-ochrona-danych) · Praktyka + symulacja | Ćwicz podstawowe operacje na tabeli managed. Rozpisz external location i cykl danych. Oceń ALTER TABLE SET MANAGED oraz UNSET MANAGED i warunki rollback. |
| 7.2  Kontrola dostępu w UI i SQL, GRANT, REVOKE i DENY, principals i hierarchia. | [P3.6](01-Sylabus.md#p36-unity-catalog-i-ochrona-danych) · Praktyka + symulacja | Wykonaj GRANT/REVOKE i SHOW GRANTS na obiekcie testowym oraz sprawdź Catalog Explorer. Zasymuluj grupy, service principal, dziedziczenie i jawne odmowy. |
| 7.3  Column-level masking i row-level security według członkostwa w grupie. | [P3.6](01-Sylabus.md#p36-unity-catalog-i-ochrona-danych) · Praktyka + symulacja | Przetestuj logikę filtra i maski na danych fikcyjnych. Rozpisz wyniki dla dwóch ról oraz wybór row filter, column mask lub dynamic view. |
| 7.4  Polityki ABAC scentralizowane przez governed tags, row filtering i masking. | [P3.6](01-Sylabus.md#p36-unity-catalog-i-ochrona-danych) · Symulacja | Rozpisz scope polityki, tag, principal, warunek i oczekiwany wynik dla kilku obiektów. Porównaj z konfiguracją per tabela. |

Guide wymienia DENY. Ćwiczenie rozróżnia historyczne DENY w legacy Hive table ACL, podstawowy zestaw GRANT/REVOKE w Unity Catalog i opisaną obecnie politykę ABAC DENY (Beta). Odmowa w polityce ma pierwszeństwo nad nadaniem. Symulacja obejmuje odrębne tożsamości i polityki, z dowodem SQL/UI tam, gdzie workspace na to pozwala.

**Źródła** [Oficjalny Exam Guide z aktualizacją 6 sierpnia 2026](https://www.databricks.com/sites/default/files/2026-10/Databricks-Certified-Data-Engineer-Associate-Exam-Guide-August-2026.pdf)  ·  [Databricks Free Edition limitations](https://docs.databricks.com/aws/en/getting-started/free-edition-limitations)  ·  [Konwersja tabel do managed i rollback](https://docs.databricks.com/aws/en/tables/convert-to-managed)  ·  [Unity Catalog access control](https://docs.databricks.com/aws/en/data-governance/unity-catalog/access-control)  ·  [Row filters i column masks](https://docs.databricks.com/aws/en/data-governance/unity-catalog/filters-and-masks/manually-apply)  ·  [ABAC i model governed tags](https://docs.databricks.com/aws/en/data-governance/unity-catalog/abac/core-concepts)  ·  [ABAC DENY policies w wersji Beta](https://docs.databricks.com/aws/en/data-governance/unity-catalog/abac/deny-policies)  ·  [Migracja z legacy Hive metastore](https://docs.databricks.com/gcp/en/data-governance/unity-catalog/hive-metastore)
