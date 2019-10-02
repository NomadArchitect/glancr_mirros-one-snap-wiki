Place to sketch out ideas for new mirr.OS extensions.

## Sport results
Create a data source for sports results: Football results and basketball results. Migrate the two "modules" of v0.x.x and build two widgets.

LIGA hat
- Spielklasse
- Altersklasse
- Geschlecht
- Anzahl der Plätze
- Saison

MANNSCHAFT hat
- Logo
- Siege
- Unentschieden
- Niederlagen
- Anzahl d. Spiele
- Tordifferenz
- Punkte
- Platzierung
- Platzierung Änderung zum letzten Messpunkt

SPIELTAG hat
- Nummer (also Zahl des Spieltages)
- Ergebnisse der Begegnungen
- Zeitstempel

Jede LIGA hat n-MANNSCHAFTEN
Jeder SPIELTAG hat n-SPIELE (MANNSCHAFTEN:2)
Zu jedem SPIELTAG spielen MANNSCHAFTEN mit Ergebnissen

Ziele:
Ich will die Liga auswählen und dann entweder die Spielergebnisse der letzten Spiele (neueste zuerst) oder die Tabelle
- Ergebnistabelle (wie im Modul)
- Begegnung + Ergebnisse des aktuellen Spieltag

## Traffic incident / route information
Data sources for Bing Maps + [TomTom Traffic API](https://developer.tomtom.com/traffic-api)
* Parent model: Chosen route (start/end), possibly a title
* Child model: 0-n incidents along this route, cf. old traffic module for fields

Widget to display active incidents along the chosen route