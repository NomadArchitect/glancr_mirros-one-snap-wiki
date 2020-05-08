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


## Smart Home

### Schema
* `String` Device name
* `String` Current status / last value (on/off, xx,x W consumption, …)

**How should we handle devices that offer > 1 value, but don't fit other schemas like `current_weather`?** 

### Widget
* Display smart home device status / value from connected sources
  * Tabular layout
  * Choose from a set of generic icons

### Sources
Requested by: [(1)](https://gitlab.com/glancr/mirros-one-snap/-/issues/423#note_338445177)
* SMA (photovoltaic manufacturer): [iOS app](https://www.heiko-pruessing.de/projects/energymeterapp/#links) by an SMA employee seems to use “energy meter” APIs via UDP Multicast to get basic information. No authentication necessary.
