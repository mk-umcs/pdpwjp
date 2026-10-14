# Zadania z odczytu i zapisu danych wektorowych

## Zadanie 1 &mdash; Null Island
Napisz program, który tworzy plik Shapefile `null_island.shp` zawierający jeden obiekt &mdash; punkt o współrzędnych (0, 0) w układzie WGS84 (EPSG:4326). Plik ma mieć dwa pola tekstowe: `name` z wartością `"Null Island"` oraz `wikipedia_url` z wartością `"https://en.wikipedia.org/wiki/Null_Island"`.


## Zadanie 2 &mdash; Siatka stopni geograficznych nad Europą
Napisz program, który tworzy siatkę komórek o rozmiarze 5° × 5° pokrywającą obszar Europy i zapisuje ją do pliku `europe_grid.gpkg` w formacie GeoPackage.

Przyjmij następujący zasięg jako stałe w kodzie: długość geograficzna od -25° do 40°, szerokość geograficzna od 35° do 72°. Użyj układu współrzędnych WGS84 (EPSG:4326).

Każda komórka siatki powinna być poligonem prostokątnym. Nadaj każdej komórce atrybuty: `row` i `col` (indeks wiersza i kolumny, licząc od 0), `lon_min` i `lat_min` (współrzędne lewego dolnego rogu komórki) oraz `cell_id` &mdash; string w formacie `R02_C04`.

Do tworzenia geometrii możesz użyć `shapely.geometry.box`.

Popraw program tak, żeby umożliwiał w jakiś sposób podanie rozmiaru komórek oraz zasięgu siatki.


## Zadanie 3 &mdash; Podział krajów na kontynenty
Napisz program, który wczytuje plik Shapefile `ne_10m_admin_0_countries/ne_10m_admin_0_countries.shp` i zapisuje jego zawartość do osobnych plików Shapefile &mdash; po jednym na każdy kontynent.

Pogrupuj kraje według wartości pola `CONTINENT`. Dla każdej grupy utwórz osobny plik Shapefile o nazwie w stylu `south_america.shp` (małe litery, spacje zamienione na podkreślniki). Każdy plik powinien zawierać te same pola co plik źródłowy i zachować oryginalny układ współrzędnych. Schemat pliku wyjściowego skopiuj ze schematu pliku źródłowego.


## Zadanie 4 &mdash; Kraje w strefie czasowej zadanego punktu
Napisz program, który dla zadanego punktu (lon, lat) wyznacza strefę czasową, a następnie zapisuje do pliku GeoPackage wszystkie kraje, które leżą w tej strefie. Informacja o strefach czasowych znajduje się w plikach w katalogu `tz`.

Strefę czasową wyznacz, wczytując plik Shapefile ze strefami czasowymi i sprawdzając, który wielokąt zawiera zadany punkt &mdash; użyj `shapely.geometry.Point` i metody `contains`. Na podstawie informacji z pliku `ne_10m_admin_0_countries/ne_10m_admin_0_countries.shp` wybierz te kraje, które leżą w wybranej strefie. Wynik zapisz do pliku `countries_in_tz.gpkg`, zachowując oryginalne pola i układ współrzędnych z pliku z krajami.

Plik ze strefami czasowymi nie ma topologii zgodnej z plikiem z państwami. Oznacza to, że państw leżące na brzegu strefy mogą według danych częściowo wychodzić poza strefę. Poza tym państwa graniczące ze strefą mogą według danych częściowo znajdować się wewnątrz strefy. Zastanów się jak można rozwiązać ten problem.

Dodatkowo istnieją państwa leżące w wielu strefach. Napisz program tak, żeby w pliku wynikowym umieścić tylko tę część pańwtwa, która leży wewnątrz zadanej strefy.


## Zadanie 5 &mdash; Miejscowości z wybranego powiatu
Napisz program, który filtruje dane z pliku `ms_M1_UrzedoweNazwyMiejscowosci.gml` i zapisuje wybrane miejscowości do pliku w zadanym formacie. Program przyjmuje trzy argumenty z wiersza poleceń: format pliku wynikowego (`shp`, `gml` lub `json`, bez rozróżniania wielkości liter), nazwę województwa oraz nazwę powiatu (porównanie bez rozróżniania wielkości liter). Z pliku źródłowego wybierz wyłącznie miasta (odpowiednia wartość pola `RODZAJOBIEKTU`) należące do podanego powiatu i województwa. Plik wynikowy powinien zawierać tylko dwa pola: `nazwa` (z wartości pola `NAZWAGLOWNA`) i `gmina` (z wartości pola `GMINA`). Jako nazwę pliku wynikowego oraz nazwę warstwy (w przypadku formatów, które ją obsługują) użyj nazwy podanego powiatu.


## Zadanie 6 &mdash; Shapefile na podstawie danych z Nominatim
Napisz program, który przyjmuje w argumencie wiersza poleceń nazwę obiektu geograficznego, wysyła ją do serwisu Nominatim przy użyciu biblioteki `geopy` i zapisuje wynik do pliku Shapefile.

Wywołaj metodę `geocode`, przekazując parametr `geometry` z wartością `"geojson"`. Typ geometrii pliku wynikowego powinien odpowiadać typowi geometrii zwróconej przez Nominatim. Plik wynikowy ma zawierać pola: `osm_id`, `osm_type`, `category`, `type` oraz `display_name` &mdash; wypełnione wartościami z odpowiedzi serwisu. Jako nazwę pliku wynikowego użyj nazwy zadanego obiektu (ze spacjami zamienionymi na znaki podkreślenia i samymi małymi literami).

- [dokumentacja GeoPy](https://geopy.readthedocs.io/)