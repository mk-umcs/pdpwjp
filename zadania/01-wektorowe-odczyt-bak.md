# Zadania z odczytu danych wektorowych

(layers)=
## Zadanie 1 &mdash; nazwy warstw
Napisz program, który dla pobranej od użytkownika nazwy pliku (lub innego źródła danych, np. katalogu z plikami Shapefile) wyświetli nazwy wszystkich warstw. Wypróbuj program z pojedynczym plikiem Shapefile, katalogiem z plikami Shapefile, plikiem GeoJSON, plikem `.gpx`, plikiem `.osm` i plikiem `.pbf` (przykłady plików `.osm` i `.pbf` są w katalogu `osm`).

(layers-geoms)=
## Zadanie 2 &mdash; nazwy warstw i typ geometrii
Zmodyfikuj program z poprzedniego zadania tak, żeby wyświetlał też nazwę typu geometrii związanej z warstwą (np. `Point`, `Multi Polygon`, `Unknown`).

3. Napisz program, który na podstawie danych z pliku `adm/wojewodztwa.shp` wyświetli nazwy wszystkich województw (pole `jpt_nazwa_`).

4. Napisz program, który na podstawie danych z pliku `adm/powiaty.shp` wyświetli nazwy wszystkich powiatów (pole `jpt_nazwa_`) z województwa lubelskiego (województwo wyznaczone jest przez pierwsze dwie cyfry pola `jpt_kod_je`, dla województwa lubelskiego jest to `06`).

5. Napisz program, który na podstawie danych z plików `adm/wojewodztwa.shp` i `adm/powiaty.shp` umożliwi użytkownikowi wyświetlenie nazw wszystkich powiatów z wybranego województwa.

    Program najpierw wyświetla nazwy wszystkich województw wraz z kodem z pola `jpt_kod_je` (`wojewodztwa.shp`). Użytkownik proszony jest o podanie wybranego województwa (kodu). Następnie program wyświetla nazwy wszystkich powiatów z wybranego województwa (pierwsze dwie cyfry pola `jpt_kod_je` z pliku `powiaty.shp` są równe wartości pola `jpt_kod_je` z pliku `wojewodztwa.shp`).

6. Napisz program, który wyświetli informację o tym ile obiektów z pliku `buildings/buildings.shp` nie ma podanej ani nazwy (pole `name`) ani typu (pole `type`).

7. Pliki `.gpx` są zwykle odczytywane przez oprogramowanie (np. QGIS bądź biblioteki OGR czy Fiona) jako ustalony zestaw warstw o nazwach `waypoints`, `routes`, `tracks`, `route_points` i `track_points`.

    Napisz program, który z zadanego pliu GPX wyświetli nazwy i współrzędne wszystkich &bdquo;[waypointów](https://pl.wikipedia.org/wiki/Waypoint)&rdquo; &mdash; tzn. elementów `wpt`. Elementy `wpt` są wtedy widoczne jako obiekty w warstwie `waypoints`. Nazwa znajduje się w polu `name`.

    Możesz przetestować program na pliku `gpx/St_Louis_Zoo_sample.gpx`.

8. W pliku `gpx/szlak-green-velo.gpx` znajduje się ślad GPS szlaku rowerowego [Green Velo](https://greenvelo.pl/). Punkty trasy znajdują się w warstwie `track_points` (każdy punkt jako osobny obiekt), a wysokości tych punktów można odczytać z pola `ele` (ang. *elevation*). Napisz program znajdujący wysokość najwyższego i najniższego punktu na trasie.

    Weź pod uwagę to, że nie wszystkie punkty mają podaną wysokość &mdash; zignoruj te, które nie mają.

9. Zmodyfikuj program z zadania poprzedniego tak, żeby wyświetlał również współrzędne (długość i szerokość geograficzną) znalezionych punktów. Jeżeli wiele punktów ma najniższą bądź najwyższą wysokość, to program ma wyświetlać współrzędne wszystkich tych punktów.

10. Napisz program, który znajdzie w pliku `50m_cultural/ne_50m_populated_places.shp` miasto, którego populacja zwiększyła się najbardziej w latach 1980-2015 (na podstawie pól `POP1980` i `POP2015` &mdash; populacja w tysiącach). Dla znalezionego miasta program ma wyświetlić wzrost populacji, nazwę (pole `NAME`) i nazwę po polsku (pole `name_pl`). Program ma też wyświetlić nazwy i liczbę miast, których populacja nie zwiększyła się w tym czasie (ale bez brania pod uwagę miast, dla których nie ma danych &mdash; wartości równe 0 w polach dotyczących populacji).

11. W pliku `rzeki_bieszczady/rzeki.shp` każda rzeka reprezentowana jest jako łamana (`Line String`). Nazwa rzeki znajduje się w polu `nazwa`. Napisz program wyświetlający nazwy wszystkich rzek, których nazwa zaczyna się na zadaną przez użytkownika literę.

12. Napisz program wyświetlający powierzchnię, nazwę (pole `name`) i typ (pole `type`) budynku o największej powierzchni z pliku `buildings/buildings.shp`. Program ma brać pod uwagę tylko budynki mające nazwę. Jeżeli budynek nie ma podanego typu, to program ma wyświetlić informację o tym.

13. Program z zadania nr 2 rozwiń tak, żeby w przypadku gdy typ geometrii jest nieznany (np. stała `ogr.wkbUnknown` zwracana jako typ geometrii w warstwie w przypadku użycia OGR lub napis `'Unknown'` w przypadku użycia Fiony) wyświetlane były nazwy typów geometrii wszystkich obiektów z tej warstwy. Wypróbuj program na pliku `geojson/geometries.json`.

14. Napisz program, który na podstawie danych z pliku `rzeki_bieszczady/rzeki.shp` oraz dla podanej przez użytkownika nazwy rzeki wyświetli nazwę jej recypienta (rzeki, do której uchodzi dana rzeka) lub informację o jego braku w pliku. W pliku zachowana jest topologia &mdash; wśród punktów łamanej reprezentującej rzekę są punkty będące ostatnimi punktami wszystkich jej dopływów.

15. Napisz program, który na podstawie danych z pliku `rzeki_bieszczady/rzeki.shp` oraz dla podanej przez użytkownika nazwy rzeki wyświetli listę jej dopływów.

16. W pliku Shapefile ze strefami czasowymi (`tz/tz.shp`) atrybut `time_zone` oznacza strefę czasową. Napisz program, który pobierze od użytkownika współrzędne geograficzne punktu, a następnie wyświetli strefę czasową, w której punkt leży.

17. Na podstawie danych w pliku `adm/wojewodztwa.shp` wyświetl nazwy (pole `jpt_nazwa_`) wszystkich województw sąsiadujących z województwem lubelskim.

    Możesz zmodyfikować program tak, żeby działał dla dowolnego innego wybranego województwa.

18. Na podstawie danych w plikach `rzeki/rzeki.shp` i `adm/wojewodztwa.shp` wyświetl nazwy wszystkich województw przez które przepływa Wisła. Nazwy rzek są w polu `NAZ_RZEKI`.

19. Na podstawie danych w plikach `rzeki/rzeki.shp` i `vector/adm/wojewodztwa.shp` znajdź wszystkie rzeki o nazwie `Czarna` i dla każdej z nich wyświetl nazwy województw przez które przepływa.

20. W pliku `adm/miasta.shp` są informacje o miastach w Polsce na prawach powiatu. Napisz program, który na podstawie tego pliku oraz pliku `vector/adm/wojewodztwa.shp` wyświetli nazwy oraz odległość od województwa lubelskiego wszystkich takich miast (pole `nazwa`), które są odległe od województwa lubelskiego o nie więcej niż 100 kilometrów, ale w nim nie leżą.

    Obiekt reprezentujący województwo lubelskie można np. znaleźć jako obiekt z wartością `lubelskie` w polu `jpt_nazwa_` w pliku `adm/wojewodztwa.shp`.

    Oba pliki używają układu PUWG 1992 (współrzędne są w metrach).
