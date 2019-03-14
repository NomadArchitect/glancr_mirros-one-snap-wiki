# Kurzanleitung zurErstellung eines Widgets

Zur Vorabinfo:
- Datenquellen werden in Ruby geschrieben
- Widgets werden mit vue.js und HTML geschrieben

Wir haben aber einen 'Rails Generator', der dir das Grundgerüst komplett fertig baut. In diesen Widget-Grundgerüst musst Du die speziellen Funktionen integrieren.

## Vorarbeit
- lokal ruby installieren (>=v2.5.1)
- die API klonen: https://gitlab.com/glancr/mirros_api (aktueller Master-Branch)
- die Settings App klonen (https://gitlab.com/glancr/mirros_settings) 
- die Display App klonen (https://gitlab.com/glancr/mirros_display)

Hier in die readme schauen und die Befehle nacheinander abfeuern. Das Ergebnis ist, dass beide Apps unter localhost:8080 und aus localhost:8081 laufen.

## Datenbank zum laufen bekommen
- im API Verzeichnis einmal den Befehl "bin/bundle install" eingeben (falls ein Fehler kommt, musst Du noch das gem "bundler" installieren. ab ruby >=2.6 ist bundler automatisch dabei)
- jetzt den Befehl "bin/rails db:setup"

## Im mirr.OS API-Verzeichnis den Rails Generator starten
- zum Widget erstellen den Befehl "bin/rails generate widget dein_widget_name" eingeben
- auf den Output achten. Da steht, was Du noch machen musst, damit es in die Datenbank kommt.

Im API Verzeichnis den Rails Server starten: "bin/rails s"

Ergebnis:
- rails server läuft auf localhost:3000
- die JS-Apps laufen
- du findest den Code Deines Widgets imAPI-Verzeichnis im Ordner /widgets/dein_widget_name

## Widget bearbeiten
Folgende 3 Dateien müssen mindestens bearbeitet werden:
- app/assets/templates/display.vue: Anzeige-Code
- app/assets/templates/settings.vue: Formular für Einstellungen
- dein_widget_Name.gemspec: Metadaten (ist mit Kommentaren erklärt)

Wenn du in widgets/dein_widget_name den Befehl "bin/rails g controller NowPlaying" ausführst, wird die Datei in app/controllers/now_playing_controller.rb angelegt. Damit kannst du Anfragen aus der Display-App an die Route localhost:3000/dein_widget_name/route bearbeiten, die du in dein_widget_name/config/routes.rb angelegt hast. Ein Beispiel, wie das geht, siehst du in der Datenquelle Openweathermap (Abfrage von Städtenamen): https://gitlab.com/glancr/source--openweathermap/