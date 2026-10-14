# Zadania z odczytu danych wektorowych

(layers)=
## Zadanie 1 &mdash; nazwy warstw
Napisz program, który dla pobranej od użytkownika nazwy pliku (lub innego źródła danych, np. katalogu z plikami Shapefile) wyświetli nazwy wszystkich warstw. Wypróbuj program z pojedynczym plikiem Shapefile, katalogiem z plikami Shapefile, plikiem GeoJSON, plikem `.gpx`, plikiem `.osm` i plikiem `.pbf` (przykłady plików `.osm` i `.pbf` są w katalogu `osm`).

(layers-geoms)=
## Zadanie 2 &mdash; nazwy warstw i typ geometrii
Zmodyfikuj program z [poprzedniego zadania](#layers) tak, żeby wyświetlał też nazwę typu geometrii związanej z warstwą (np. `point`, `polygon`).

(wojewodztwa-names)=
## Zadanie 3 &mdash; nazwy województw
Napisz program, który na podstawie danych z pliku `adm/wojewodztwa.shp` wyświetli nazwy wszystkich województw (pole `jpt_nazwa_`).

(powiaty-lubelskie)=
## Zadanie 4 &mdash; powiaty z województwa lubelskiego
Napisz program, który na podstawie danych z pliku `adm/powiaty.shp` wyświetli nazwy wszystkich powiatów (pole `jpt_nazwa_`) z województwa lubelskiego (województwo wyznaczone jest przez pierwsze dwie cyfry pola `jpt_kod_je`, dla województwa lubelskiego jest to `06`).

(powiaty-wybrane)=
## Zadanie 5 &mdash; powiaty z wybranego województwa
Napisz program, który na podstawie danych z plików `adm/wojewodztwa.shp` i `adm/powiaty.shp` umożliwi użytkownikowi wyświetlenie nazw wszystkich powiatów z wybranego województwa.

Program najpierw wyświetla nazwy wszystkich województw wraz z kodem z pola `jpt_kod_je` (`wojewodztwa.shp`). Użytkownik proszony jest o podanie wybranego województwa (kodu). Następnie program wyświetla nazwy wszystkich powiatów z wybranego województwa (pierwsze dwie cyfry pola `jpt_kod_je` z pliku `powiaty.shp` są równe wartości pola `jpt_kod_je` z pliku `wojewodztwa.shp`).

(buildings-missing-attrs)=
## Zadanie 6 &mdash; brakujące atrybuty budynków
Napisz program, który wyświetli informację o tym ile obiektów z pliku `buildings/buildings.shp` nie ma podanej ani nazwy (pole `name`) ani typu (pole `type`).

(gpx-waypoints)=
## Zadanie 7 &mdash; odczyt waypointów GPX
Pliki `.gpx` są zwykle odczytywane przez oprogramowanie (np. QGIS bądź biblioteki OGR czy Fiona) jako ustalony zestaw warstw o nazwach `waypoints`, `routes`, `tracks`, `route_points` i `track_points`.

Napisz program, który z zadanego pliu GPX wyświetli nazwy i współrzędne wszystkich &bdquo;[waypointów](https://pl.wikipedia.org/wiki/Waypoint)&rdquo; &mdash; tzn. elementów `wpt`. Elementy `wpt` są wtedy widoczne jako obiekty w warstwie `waypoints`. Nazwa znajduje się w polu `name`.

Możesz przetestować program na pliku `gpx/St_Louis_Zoo_sample.gpx`.

(gpx-elevation-extremes)=
## Zadanie 8 &mdash; ekstremalne wysokości na trasie
W pliku `gpx/szlak-green-velo.gpx` znajduje się ślad GPS szlaku rowerowego [Green Velo](https://greenvelo.pl/). Punkty trasy znajdują się w warstwie `track_points` (każdy punkt jako osobny obiekt), a wysokości tych punktów można odczytać z pola `ele` (ang. *elevation*). Napisz program znajdujący wysokość najwyższego i najniższego punktu na trasie.

Weź pod uwagę to, że nie wszystkie punkty mają podaną wysokość &mdash; zignoruj te, które nie mają.

(gpx-elevation-coords)=
## Zadanie 9 &mdash; współrzędne punktów ekstremalnych
Zmodyfikuj program z [zadania wyświetlającego nazwy warstw](#gpx-elevation-extremes) tak, żeby wyświetlał również współrzędne (długość i szerokość geograficzną) znalezionych punktów. Jeżeli wiele punktów ma najniższą bądź najwyższą wysokość, to program ma wyświetlać współrzędne wszystkich tych punktów.

(population-growth)=
## Zadanie 10 &mdash; największy wzrost populacji
Napisz program, który znajdzie w pliku `50m_cultural/ne_50m_populated_places.shp` miasto, którego populacja zwiększyła się najbardziej w latach 1980-2015 (na podstawie pól `POP1980` i `POP2015` &mdash; populacja w tysiącach). Dla znalezionego miasta program ma wyświetlić wzrost populacji, nazwę (pole `NAME`) i nazwę po polsku (pole `name_pl`). Program ma też wyświetlić nazwy i liczbę miast, których populacja nie zwiększyła się w tym czasie (ale bez brania pod uwagę miast, dla których nie ma danych &mdash; wartości równe 0 w polach dotyczących populacji).

(rivers-by-letter)=
## Zadanie 11 &mdash; wyszukiwanie rzek po literze
W pliku `rzeki_bieszczady/rzeki.shp` każda rzeka reprezentowana jest jako łamana (`LineString`). Nazwa rzeki znajduje się w polu `nazwa`. Napisz program wyświetlający nazwy wszystkich rzek, których nazwa zaczyna się na zadaną przez użytkownika literę.

(largest-building)=
## Zadanie 12 &mdash; budynek o największej powierzchni
Napisz program wyświetlający powierzchnię, nazwę (pole `name`) i typ (pole `type`) budynku o największej powierzchni z pliku `buildings/buildings.shp`. Program ma brać pod uwagę tylko budynki mające nazwę. Jeżeli budynek nie ma podanego typu, to program ma wyświetlić informację o tym.

(unknown-geometries)=
## Zadanie 13 &mdash; rozpoznawanie nieznanej geometrii
Program z [zadania dotyczącego nazw warstw i typów geometrii](#layers-geoms) rozwiń tak, żeby w przypadku gdy typ geometrii jest nieznany (np. stała `ogr.wkbUnknown` zwracana jako typ geometrii w warstwie w przypadku użycia OGR lub napis `'Unknown'` w przypadku użycia Fiony) wyświetlane były nazwy typów geometrii wszystkich obiektów z tej warstwy. Wypróbuj program na pliku `geojson/geometries.json`.

(river-recipient)=
## Zadanie 14 &mdash; recypient rzeki
Napisz program, który na podstawie danych z pliku `rzeki_bieszczady/rzeki.shp` oraz dla podanej przez użytkownika nazwy rzeki wyświetli nazwę jej recypienta (rzeki, do której uchodzi dana rzeka) lub informację o jego braku w pliku. W pliku zachowana jest topologia &mdash; wśród punktów łamanej reprezentującej rzekę są punkty będące ostatnimi punktami wszystkich jej dopływów.

(river-tributaries)=
## Zadanie 15 &mdash; dopływy rzeki
Napisz program, który na podstawie danych z pliku `rzeki_bieszczady/rzeki.shp` oraz dla podanej przez użytkownika nazwy rzeki wyświetli listę jej dopływów.

(time-zone)=
## Zadanie 16 &mdash; strefa czasowa punktu
W pliku Shapefile ze strefami czasowymi (`tz/tz.shp`) atrybut `time_zone` oznacza strefę czasową. Napisz program, który pobierze od użytkownika współrzędne geograficzne punktu, a następnie wyświetli strefę czasową, w której punkt leży.

(neighboring-voivodeships)=
## Zadanie 17 &mdash; sąsiednie województwa
Na podstawie danych w pliku `adm/wojewodztwa.shp` wyświetl nazwy (pole `jpt_nazwa_`) wszystkich województw sąsiadujących z województwem lubelskim.

Możesz zmodyfikować program tak, żeby działał dla dowolnego innego wybranego województwa.

(river-voivodeships)=
## Zadanie 18 &mdash; województwa na trasie rzeki
Na podstawie danych w plikach `rzeki/rzeki.shp` i `adm/wojewodztwa.shp` wyświetl nazwy wszystkich województw przez które przepływa Wisła. Nazwy rzek są w polu `NAZ_RZEKI`.

(rivers-same-name)=
## Zadanie 19 &mdash; rzeki o tej samej nazwie
Na podstawie danych w plikach `rzeki/rzeki.shp` i `vector/adm/wojewodztwa.shp` znajdź wszystkie rzeki o nazwie `Czarna` i dla każdej z nich wyświetl nazwy województw przez które przepływa.

(cities-near-voivodeship)=
## Zadanie 20 &mdash; miasta w pobliżu województwa
W pliku `adm/miasta.shp` są informacje o miastach w Polsce na prawach powiatu. Napisz program, który na podstawie tego pliku oraz pliku `vector/adm/wojewodztwa.shp` wyświetli nazwy oraz odległość od województwa lubelskiego wszystkich takich miast (pole `nazwa`), które są odległe od województwa lubelskiego o nie więcej niż 100 kilometrów, ale w nim nie leżą.

Obiekt reprezentujący województwo lubelskie można np. znaleźć jako obiekt z wartością `lubelskie` w polu `jpt_nazwa_` w pliku `adm/wojewodztwa.shp`.

Oba pliki używają układu PUWG 1992 (współrzędne są w metrach).