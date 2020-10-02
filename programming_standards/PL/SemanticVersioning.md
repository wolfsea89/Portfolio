Wersjonowanie Semantyczne
=========

Wersjonowanie Semantyczne - numerowanie kodu źródłowego, aplikacji. Wersjonowanie semantyczne składa się z 3-4 liczb, oddzielonych kropkami X.Y.Z.B.

`X` – gdy dokonujemy zmian niekompatybilnych z API np. takim momentem może być aktualizacja framework-a w naszym projekcie,

`Y` – gdy dodajemy nową funkcjonalność zachowując kompatybilność z poprzednimi wersjami, w ramach zmiany tego numeru możliwe jest wprowadzanie także poprawek nie łamiących kompatybilności,

`Z` – gdy dokonujemy naprawy błędu i nie łamie to kompatybilności z poprzednimi wersjami, upraszczając zmieniamy wartość gdy wydanie jest jedynie poprawkowe i nie dodaje żadnych nowych funkcjonalności,

`B` - build number, numer joba wykonanego podczas kompilacji paczki, np z Jenkinsa, TFSa

Extra
=========

regexp na walidacje numeru wersji `X.Y.Z`
```
/^\d+.\d+.\d+/
```

regexp na walidacje numeru wersji `X.Y.Z.B`
```
/^\d+.\d+.\d+.\d+/
```
regexp na walidacje numer wersji `X.Y.Z` i `X.Y.Z.B`
```
^\d+.\d+.\d+.?(\d+)
```

[Powrót](../../README.md)