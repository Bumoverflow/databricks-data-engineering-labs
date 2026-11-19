# Databricks Free Edition i specyfikacje projektów

*Databricks Data Engineering · Dokument 02 · 18 listopada 2026*

[Sylabus i Progress Tracker](01-Sylabus.md) · [Macierz certyfikacyjna](03-Macierz-certyfikacyjna.md)

Trzy projekty współdzielą dane fikcyjnego sklepu. Całą ścieżkę obowiązkową zaplanowano dla jednego workspace Free Edition, z plikami w managed Unity Catalog volumes i compute uruchamianym na czas ćwiczenia. Ustalenia wynikają z bieżącej dokumentacji. Widoczność funkcji warunkowych sprawdzimy na Twoim koncie po akceptacji sylabusa.

## Limity wspólne dla wszystkich projektów

| **Obszar** | **Limit lub warunek** | **Decyzja w kursie** |
| --- | --- | --- |
| Compute | Serverless. Ograniczona moc i użycie w notebookach. Brak custom compute, classic, R/Scala i API Spark RDD. | Python, PySpark DataFrames i SQL. Classic compute w scenariuszach egzaminacyjnych. |
| SQL | Jeden SQL warehouse, maksymalnie 2X-Small. | Wspólny warehouse dla zapytań i dashboardów. Krótkie uruchomienia. |
| Lakeflow | Do 5 jednoczesnych tasków Jobs na konto. Po jednym aktywnym pipeline na typ. | Maksymalnie jeden run danego joba w tym samym czasie. DAG sekwencyjny z małymi kontrolowanymi porcjami. Pipeline triggered. |
| Fair usage | Po wyczerpaniu quota compute może być niedostępny do końca dnia, a wyjątkowo do końca miesiąca. Dane i konfiguracja są zachowywane. | W razie limitu wznów od ostatniego zapisanego batch_id i checkpointu po resecie. Harmonogramy pauzuj po laboratorium. |
| Unity Catalog | Jeden workspace i metastore. Bez account console, account APIs, SSO/SCIM i private networking. Brak custom workspace storage. | Managed storage workspace, osobne schemas dla ćwiczeń i rolloutów. Administracja kontem i zewnętrzny storage jako scenariusze. |
| Sieć i koszty | Ograniczony outbound internet. Edycja do zastosowań niekomercyjnych, bez SLA i wsparcia. | Upload przez UI lub generator z materiałów. Bez płatnej chmury, usług SaaS i LinkedIn verification jako kroku obowiązkowego. |

Wielkości zestawów są budżetem kursu. Dokumentacja limitów, zaktualizowana 16 listopada 2026, opisuje fair usage bez publicznego wymiaru czasu compute do planowania nauki.

**Źródła** [F01](https://docs.databricks.com/aws/en/getting-started/free-edition-limitations)  ·  [F02](https://docs.databricks.com/aws/en/getting-started/free-trial-vs-free-edition)  ·  [F03](https://docs.databricks.com/aws/en/getting-started/free-edition)  ·  [F04](https://docs.databricks.com/aws/en/compute/serverless/limitations)  ·  [F06](https://docs.databricks.com/aws/en/files/volumes)

## Dostępność funkcji według projektu

Praktyka oznacza ścieżkę przewidzianą w bazowym workspace. Wariant warunkowy zaczyna się od krótkiej próby dostępności i ma przygotowaną ścieżkę zastępczą. Symulacja wykorzystuje pliki, przykładowe logi lub karty przypadków.

| **Projekt** | **Praktyka w Free Edition** | **Wariant warunkowy albo symulacja** |
| --- | --- | --- |
| 1 · Batch | Notebooki serverless, Unity Catalog managed volumes i Delta, PySpark/SQL, Lakeflow Jobs, SQL warehouse, dashboard AI/BI. | Classic, dobór rozmiaru i rozliczanie compute rozpatrujemy na przypadkach. Podstawowy dashboard korzysta z jednego warehouse. |
| 2 · Incremental | COPY INTO z volume, Auto Loader w directory listing, Delta MERGE, triggered Lakeflow Spark Declarative Pipelines, expectations, AUTO CDC, SCD 1/2, Jobs i lineage. | Zarządzane file events i kolejki powiadomień wymagające własnego cloud storage omawiamy na schemacie. Database CDC connectors Lakeflow Connect są wyłączone w Free Edition, więc feed I/U/D tworzy generator. SaaS, JDBC/ODBC i REST ćwiczymy na kontraktach i odpowiedziach zapisanych w plikach. |
| 2 · Jobs | Scheduled trigger, Run now, zależności, statusy, retries i Repair run. | File arrival na UC volume i table update na Delta próbujemy po sprawdzeniu UI i uprawnień. Zastępstwo to harmonogram z pustym przebiegiem lub Run now po dostarczeniu danych. Gdy Dashboard task jest niedostępny, raport odświeżasz ręcznie po SQL task. |
| 3 · Streaming | Structured Streaming z AvailableNow, watermarks, window aggregations, checkpoint, CDF, Delta sink. Porcje danych z volume. | ProcessingTime, Continuous i domyślny trigger nie są obsługiwane w serverless notebooks/jobs. Continuous w Lakeflow pozostaje opcjonalnym omówieniem przy quota. Kafka i działanie 24/7 symulowane. |
| 3 · Utrzymanie | Query Profile, testy, praktyka Liquid Clustering/OPTIMIZE na tabeli próbnej, Catalog Explorer, podstawowe GRANT/REVOKE, lokalny Git i test gates. | Spark UI i classic cluster na przykładowych metrykach. Predictive optimization jako analiza konfiguracji, jeśli brak uprawnień. External tables, ABAC, niezależne principals i account governance w symulacji. |
| 3 · Wdrożenia | Konfiguracja bundle, lokalne testy CI, wzorzec oddzielenia dev/test/prod w schemas. | Git folders i CLI OAuth/deploy sprawdzamy na koncie. Zastępstwo to lokalny Git, analiza konfiguracji i testowy job przez UI. Promocja między odrębnymi workspaces, identyfikacja CI i prod pozostają symulacją. |

**Źródła** [F01](https://docs.databricks.com/aws/en/getting-started/free-edition-limitations)  ·  [F03](https://docs.databricks.com/aws/en/getting-started/free-edition)  ·  [F05](https://docs.databricks.com/aws/en/compute/serverless/streaming)  ·  [F07](https://docs.databricks.com/aws/en/ingestion/cloud-object-storage/copy-into/tutorial-notebook)  ·  [F08](https://docs.databricks.com/aws/en/ingestion/cloud-object-storage/auto-loader)  ·  [F10](https://docs.databricks.com/aws/en/ingestion/overview)  ·  [F11](https://docs.databricks.com/aws/en/ldp/concepts/pipeline-mode)  ·  [F12](https://docs.databricks.com/aws/en/ldp/expectations)  ·  [F13](https://docs.databricks.com/aws/en/ldp/cdc)  ·  [F15](https://docs.databricks.com/gcp/en/jobs/triggers)  ·  [F16](https://docs.databricks.com/aws/en/jobs/file-arrival-triggers)  ·  [F17](https://docs.databricks.com/aws/en/jobs/trigger-table-update)  ·  [F20](https://docs.databricks.com/aws/en/compute/serverless/best-practices)  ·  [F22](https://docs.databricks.com/aws/en/tables/clustering)  ·  [F23](https://docs.databricks.com/aws/en/optimizations/predictive-optimization)  ·  [F25](https://docs.databricks.com/aws/en/data-governance/unity-catalog/access-control)  ·  [F27](https://docs.databricks.com/aws/en/data-governance/unity-catalog/abac/core-concepts)  ·  [F29](https://docs.databricks.com/aws/en/repos/git-operations-with-repos)  ·  [F30](https://docs.databricks.com/aws/en/dev-tools/cli/bundle-commands)  ·  [F31](https://docs.databricks.com/aws/en/dev-tools/auth/oauth-u2m)  ·  [F33](https://docs.databricks.com/aws/en/dashboards/tutorials/)  ·  [F34](https://docs.databricks.com/aws/en/data-governance/unity-catalog/data-lineage)

## Projekt 1 — E-commerce Data Warehouse

Zespół handlowy potrzebuje dziennego raportu sprzedaży, zamówień i zwrotów. Dane przychodzą w różnych formatach, a raport ma zgadzać się z uzgodnioną definicją sprzedaży.

### Architektura i dane

> CSV + JSONL + Parquet → landing volume → Bronze Delta → Silver Delta → Gold → AI/BI

CSV zawiera customers i products. JSONL zawiera orders z tablicą pozycji. Parquet dostarcza refunds. Kurs dostarczy próbkę smoke, bazowy snapshot i drugi snapshot testowy. Budżet startowy to 200 klientów, 60 produktów, około 1 000 zamówień i maksymalnie 10 MB plików wejściowych.

Dane otrzymają kontrolowane braki identyfikatora, niepoprawne typy, osierocone klucze i duplikaty. Manifest wskaże liczności, sumy kontrolne i identyfikatory rekordów istotnych dla odbioru.

### Kontrakty warstw

| **Warstwa** | **Oczekiwany kontrakt** |
| --- | --- |
| Bronze | Zachowuje surowe wartości, źródło, batch_id i czas ingestii. Ładowanie pełnego snapshotu według jawnego trybu zapisu. |
| Silver | Klucz pozycji to order_id i line_id. Typy i waluta są jawne, a odrzuty zawierają reason_code. Zamówienia walidowane przed publikacją. |
| Gold | Fakt pozycji, wymiary klientów i produktów, dzienna agregacja i widok dla BI. Strefa czasu UTC i waluta PLN. Przychód to suma qty × unit_price dla zrealizowanych pozycji pomniejszona o zatwierdzone zwroty. Anulowane pozycje mają zerowy wkład. |
| Job i raport | Sekwencja Bronze → Silver → Gold, kontrola z run history, filtry daty i trzy KPI. Zatwierdzone zwroty są przypisane do dnia zamówienia, zgodnie z kontraktem kursu. |

### Odbiór projektu

- Wynik Gold uzgadnia się z ręcznie policzoną próbką i manifestem. Po ponownym przetworzeniu tego samego snapshotu KPI i klucze pozostają identyczne.
- Dowód obejmuje identyfikatory dwóch runów, liczności i przyczyny odrzutów oraz link lub zrzut raportu. Jeden shared SQL warehouse wystarcza do odbioru.

**Źródła** [F03](https://docs.databricks.com/aws/en/getting-started/free-edition)  ·  [F06](https://docs.databricks.com/aws/en/files/volumes)  ·  [F33](https://docs.databricks.com/aws/en/dashboards/tutorials/)

## Projekt 2 — Incremental Data Platform

Sklep dodaje korekty zamówień i zmienia dane klientów w ciągu dnia. Platforma ma przetworzyć przyrost i zachować historię adresów do analiz wykonywanych według stanu na dany dzień.

### Architektura i dane

> Niezmienne porcje → Auto Loader → Bronze → Silver + quarantine → Gold

Oddzielne ćwiczenie COPY INTO i MERGE ma własny staging. Główny triggered pipeline serverless publikuje streaming tables i materialized view oraz utrzymuje dwie projekcje klientów z feedu CDC. Job steruje aktualizacją, kontrolą jakości i odświeżeniem raportu. Tory demonstracyjne wykorzystują odrębne cele i checkpointy.

Porcja A to seed. B dodaje klientów i aktualizuje zamówienia. C dodaje opcjonalne pole delivery_channel. D ma wadliwy typ, powtórkę, delete i spóźnioną aktualizację. Feed CDC niesie event_id, customer_id, op, source_seq, event_ts i payload. Manifest wskazuje kolejność źródłową, liczbę zmian i oczekiwane wersje. Budżet wynosi do 5 000 rekordów i 20 MB danych wejściowych.

### Kontrakty i odporność

- Auto Loader wykrywa nowe ścieżki. Deduplikacja według event_id obsługuje ten sam rekord w nowym pliku. Testowany jest także brak wejścia po wznowieniu ze starym checkpointem.
- Ewolucja pól i zmiana typu mają osobne scenariusze. Przed Delta MERGE ogranicz zbiór do jednej właściwej zmiany per klucz dla danego upsertu. Dla historii Type 2 przetwarzaj wszystkie wymagane zdarzenia w porządku source_seq.
- Type 1 pokazuje aktualny stan, Type 2 przedziały obowiązywania, a delete zamyka aktywny przedział zgodnie z kontraktem feedu. Raport point-in-time łączy fakt z właściwą wersją wymiaru.

### Odbiór projektu

- Ponowienie B i Repair run po błędzie D dają zgodny wynik. Raport pokazuje, które pliki lub zmiany zostały przyjęte i jak duży przyrost przeszedł przez pipeline.
- Zapisz stan SCD 1/2 przed i po opóźnionej zmianie, dane z lineage oraz status i metryki event log. Jeden aktywny pipeline danego typu wystarcza do całego odbioru.

**Źródła** [F07](https://docs.databricks.com/aws/en/ingestion/cloud-object-storage/copy-into/tutorial-notebook)  ·  [F08](https://docs.databricks.com/aws/en/ingestion/cloud-object-storage/auto-loader)  ·  [F09](https://docs.databricks.com/aws/en/ingestion/cloud-object-storage/auto-loader/schema)  ·  [F11](https://docs.databricks.com/aws/en/ldp/concepts/pipeline-mode)  ·  [F12](https://docs.databricks.com/aws/en/ldp/expectations)  ·  [F13](https://docs.databricks.com/aws/en/ldp/cdc)  ·  [F14](https://docs.databricks.com/aws/en/ldp/monitor-event-logs)  ·  [F15](https://docs.databricks.com/gcp/en/jobs/triggers)  ·  [F34](https://docs.databricks.com/aws/en/data-governance/unity-catalog/data-lineage)

## Projekt 3 — Real-Time Data Engineering Platform

Zespół operacyjny chce śledzić zdarzenia zakupowe, błędy płatności i korekty statusów. Platforma ma regularnie dostarczać przyrostowe wyniki i bezpiecznie wznawiać pracę po awarii.

### Architektura i dane

> Emitter plików → stream Bronze → dedup Silver → okna Gold

> Mutowalna tabela Delta → strumień CDF → staging zmian → MERGE do repliki

Przygotowany emitter wypuści 6–8 małych porcji JSONL. Kontrakt zawiera event_id, event_ts, arrival_batch, order_id, event_type i amount. Scenariusze obejmą duplikat w oknie, zdarzenia opóźnione po obu stronach progu, rekordy odrzucone oraz porcje przesuwające event time. Budżet wynosi do 10 000 zdarzeń i 25 MB danych wejściowych.

### Projektowanie pracy w małej skali

- Każde zapytanie ma stabilny, niezależny checkpoint poza ścieżką wejścia. Tory dedup i window aggregation mają osobne zapytania i trwały sink pośredni. Okna zamykamy według event time, z zadanym progiem 10 minut i osobnymi porcjami, które umożliwiają obserwację progresu watermarku.
- Lakeflow Jobs uruchamia skończone przebiegi AvailableNow. Każda porcja ma identyfikator i oczekiwany wynik. Testy mierzą opóźnienie od dostawy porcji do zapisu, bez SLA. Wzorce always-on omawiamy na podstawie wykonanych przebiegów.
- Włączymy CDF na tabeli testowej przed zmianami. Jeżeli ćwiczenie pomija początkowy snapshot, odczyt wystartuje od jawnie wskazanej wersji. Staging utrwala pozycję. Oddzielny upsert/delete jest idempotentny i zachowuje kolejność wersji. Replay odbywa się do izolowanego celu przed ewentualnym backfill.

### Odbiór projektu

- Okna i replika zgadzają się z manifestem. Z testów można odczytać efekt duplikatu, rekordów poza watermarkiem, restartu i częściowego zapisu. Runbook objaśnia, jak wznowić i zweryfikować stan.
- Do odbioru dołączasz wynik testów, pomiary Query Profile, schemat uprawnień, historię Git i dowód powtarzalnego dostarczenia joba. Wariant UI z lokalnym test gate pozostaje pełną ścieżką przy braku deploy z CLI.

**Źródła** [F04](https://docs.databricks.com/aws/en/compute/serverless/limitations)  ·  [F05](https://docs.databricks.com/aws/en/compute/serverless/streaming)  ·  [F18](https://docs.databricks.com/aws/en/structured-streaming/watermarks)  ·  [F19](https://docs.databricks.com/aws/en/tables/features/change-data-feed)  ·  [F20](https://docs.databricks.com/aws/en/compute/serverless/best-practices)  ·  [F22](https://docs.databricks.com/aws/en/tables/clustering)  ·  [F25](https://docs.databricks.com/aws/en/data-governance/unity-catalog/access-control)  ·  [F29](https://docs.databricks.com/aws/en/repos/git-operations-with-repos)  ·  [F30](https://docs.databricks.com/aws/en/dev-tools/cli/bundle-commands)  ·  [F31](https://docs.databricks.com/aws/en/dev-tools/auth/oauth-u2m)

## Pakiet danych i organizacja plików

Paczki są wspólnym kontraktem dla ćwiczeń i przeglądów kodu. Przyjmuję dane syntetyczne z generatorem deterministycznym. Każda wersja fixture ma seed, wersję schematu, oczekiwane liczności i referencje do konkretnych testów.

| **Ścieżka docelowa** | **Zawartość i moment przygotowania** |
| --- | --- |
| `kurs/` | Trzy dokumenty do akceptacji oraz osadzony Progress Tracker. Po akceptacji aktualizacje zakresu i odnośniki do materiałów. |
| `projects/01-ecommerce/` | Specyfikacja robocza, instrukcje modułów P1.1–P1.6, szablony notebooków, próbka smoke, snapshoty CSV/JSONL/Parquet. |
| `projects/02-incremental/` | Instrukcje P2.1–P2.7, porcje A–D, osobny feed CDC, fixtures REST/JDBC, schematy v1/v2 i rubryki diagnozy. |
| `projects/03-streaming/` | Instrukcje P3.1–P3.7, porcje eventów i generator CDF, starter testów, runbook, ćwiczenie Git, szkic bundle i gates. |
| `shared/generators/` | Generator na projekt z parametrami seed, scale i batch_id. Skrypty przygotowują wyłącznie wejście. Artefakty dostarczane sukcesywnie z modułami. |
| `shared/contracts/` | Wersjonowane schematy i manifesty z kluczami, count, kontrolnymi sumami i oznaczeniami błędów. Oczekiwany stan do odbioru. |
| `certification/` | Pytania modułowe, karty symulacji, próbny egzamin, klucz i arkusz wyników w etapie powtórki. |

### Organizacja w Unity Catalog

Użyj katalogu dostępnego w workspace. Ćwiczenia będą miały własne schemas, np. p1_bronze, p1_silver i p1_gold. Managed volumes landing oraz pipeline_state mają odrębne ścieżki. W P3 także dev i test otrzymają oddzielne schemas, ścieżki stanu i tabele wynikowe.

### Sprawdzenie konta po akceptacji

Na początku wystarczą: notebook serverless, managed volume, managed Delta table i SQL warehouse. Przed P2 sprawdzimy uprawnienia do Lakeflow Jobs i triggered pipeline. Przed P3 sprawdzimy Git folders, OAuth w CLI i możliwość wdrożenia. Próbę wykonamy bez płatnego połączenia i na najmniejszym zbiorze.

**Źródła** [F01](https://docs.databricks.com/aws/en/getting-started/free-edition-limitations)  ·  [F03](https://docs.databricks.com/aws/en/getting-started/free-edition)  ·  [F06](https://docs.databricks.com/aws/en/files/volumes)  ·  [F29](https://docs.databricks.com/aws/en/repos/git-operations-with-repos)  ·  [F31](https://docs.databricks.com/aws/en/dev-tools/auth/oauth-u2m)

## Dokumentacja źródłowa

Identyfikatory źródeł użyte w specyfikacjach prowadzą do dokumentacji Databricks. Stan weryfikacji to 18 listopada 2026. Przed ćwiczeniami warunkowymi sprawdzimy aktualne zachowanie workspace.

### Oficjalne dokumenty techniczne

| **ID** | **Dokument** | **ID** | **Dokument** |
| --- | --- | --- | --- |
| F01 | [Databricks Free Edition limitations](https://docs.databricks.com/aws/en/getting-started/free-edition-limitations) | F19 | [Delta Change Data Feed](https://docs.databricks.com/aws/en/tables/features/change-data-feed) |
| F02 | [Free Edition oraz Free Trial](https://docs.databricks.com/aws/en/getting-started/free-trial-vs-free-edition) | F20 | [Diagnostyka obciążeń serverless](https://docs.databricks.com/aws/en/compute/serverless/best-practices) |
| F03 | [Free Edition i ścieżka startowa](https://docs.databricks.com/aws/en/getting-started/free-edition) | F21 | [Parametry Spark obsługiwane przez Databricks](https://docs.databricks.com/aws/en/spark/conf) |
| F04 | [Serverless compute limitations](https://docs.databricks.com/aws/en/compute/serverless/limitations) | F22 | [Liquid Clustering](https://docs.databricks.com/aws/en/tables/clustering) |
| F05 | [Streaming on serverless compute](https://docs.databricks.com/aws/en/compute/serverless/streaming) | F23 | [Predictive optimization dla tabel managed](https://docs.databricks.com/aws/en/optimizations/predictive-optimization) |
| F06 | [Volumes i format ścieżki](https://docs.databricks.com/aws/en/files/volumes) | F24 | [Konwersja tabel do managed i rollback](https://docs.databricks.com/aws/en/tables/convert-to-managed) |
| F07 | [COPY INTO z Unity Catalog volume](https://docs.databricks.com/aws/en/ingestion/cloud-object-storage/copy-into/tutorial-notebook) | F25 | [Unity Catalog access control](https://docs.databricks.com/aws/en/data-governance/unity-catalog/access-control) |
| F08 | [Auto Loader i discovery plików](https://docs.databricks.com/aws/en/ingestion/cloud-object-storage/auto-loader) | F26 | [Row filters i column masks](https://docs.databricks.com/aws/en/data-governance/unity-catalog/filters-and-masks/manually-apply) |
| F09 | [Auto Loader schema inference i evolution](https://docs.databricks.com/aws/en/ingestion/cloud-object-storage/auto-loader/schema) | F27 | [ABAC i model governed tags](https://docs.databricks.com/aws/en/data-governance/unity-catalog/abac/core-concepts) |
| F10 | [Lakeflow Connect i rodzaje konektorów](https://docs.databricks.com/aws/en/ingestion/overview) | F28 | [ABAC DENY policies w wersji Beta](https://docs.databricks.com/aws/en/data-governance/unity-catalog/abac/deny-policies) |
| F11 | [Obsługa trybu triggered i continuous](https://docs.databricks.com/aws/en/ldp/concepts/pipeline-mode) | F29 | [Databricks Git folders i operacje Git](https://docs.databricks.com/aws/en/repos/git-operations-with-repos) |
| F12 | [Lakeflow expectations i zasady jakości](https://docs.databricks.com/aws/en/ldp/expectations) | F30 | [Databricks CLI i polecenia bundle](https://docs.databricks.com/aws/en/dev-tools/cli/bundle-commands) |
| F13 | [AUTO CDC w Lakeflow pipelines](https://docs.databricks.com/aws/en/ldp/cdc) | F31 | [OAuth user-to-machine dla CLI](https://docs.databricks.com/aws/en/dev-tools/auth/oauth-u2m) |
| F14 | [Event log pipeline’u](https://docs.databricks.com/aws/en/ldp/monitor-event-logs) | F32 | [Databricks audit log delivery](https://docs.databricks.com/aws/en/admin/account-settings/audit-log-delivery) |
| F15 | [Lakeflow Jobs schedules i triggers](https://docs.databricks.com/gcp/en/jobs/triggers) | F33 | [AI/BI Dashboard tutorials](https://docs.databricks.com/aws/en/dashboards/tutorials/) |
| F16 | [File arrival i wymagania ścieżki](https://docs.databricks.com/aws/en/jobs/file-arrival-triggers) | F34 | [Data lineage w Unity Catalog](https://docs.databricks.com/aws/en/data-governance/unity-catalog/data-lineage) |
| F17 | [Table update trigger](https://docs.databricks.com/aws/en/jobs/trigger-table-update) | F35 | [Migracja z legacy Hive metastore](https://docs.databricks.com/gcp/en/data-governance/unity-catalog/hive-metastore) |
| F18 | [Watermark i tryby zapisu](https://docs.databricks.com/aws/en/structured-streaming/watermarks) | F36 | [Bundle i pliki konfiguracyjne](https://docs.databricks.com/aws/en/dev-tools/bundles/settings) |
