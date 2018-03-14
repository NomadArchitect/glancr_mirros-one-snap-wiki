# Dokumentation mirrOS 1.0.0

Im Folgenden werden die Architektur und technische Umsetzung von mirr.OS one dokumentiert.

## Inhaltsverzeichnis

1. [Begriffe](#begriffe)
1. [Technologien und Frameworks](#technologien-und-frameworks)
2. [mirrOS](#mirros)
3. [Scripts](#scripts)
4. [Module](#module)
5. [Datenquellen](#datenquellen)
6. [Datenbankanbindung](#datenbankanbindung)
7. [Lokalisierung](#lokalisierung)
8. [API](api)

## Begriffe
* *Anzeige*: Grafische Darstellung auf dem Spiegel-Display als Webanwendung.
* *Konfiguration*: Grafische Konfigurationsoberfläche, die als Webanwendung vom Mobilgerät/Desktop aufgerufen wird.
* *Frontend*: Beide grafischen Benutzeroberflächen.
* *Backend*: Modul-Logik und API.

## Technologien und Frameworks

Die verwendten Technologien und Frameworks sind unten pro Anwendungsbereich aufgelistet.

### Anzeige
Single Page Application, die auf dem Spiegel über `localhost` im Midori-Browser läuft und die von der API gelieferten Daten anzeigt. Die Logik in den einzelnen Komponenten sollte sich dabei auf die Darstellung beschränken, d. h. keine externen Requests u. Ä. absetzen.

Verwendete Bibliotheken:

* [Vue.js](https://vuejs.org)
* [jQuery](https://jquery.com)

### Konfiguration

Single Page Application zur Konfiguration von mirr.OS und Modulinstanzen. Wird auf dem jeweiligen Endgerät ausgeführt, von dem der Nutzer im lokalen Netzwerk auf den glancr zugreift. Sie muss daher responsiv sein und sowohl Touch als auch Maus-Bedienung ermöglichen.

Verwendete Bibliotheken:

* [Vue.js](https://vuejs.org): App-Framework
* [Gridstack.js](http://troolee.github.io/gridstack.js/): Anordnen der Modulinstanzen, inkl. Abhängigkeiten
	* [jQuery](https://jquery.com)
	* [jQuery UI](https://jqueryui.com)
* [Horizon Swiper](http://horizon-swiper.sebsauer.de): Swipe-Gesten für Modulauswahl usw.
* [Drop](http://github.hubspot.com/drop/): Schönere Dropdown-Menüs
* [Tether](http://tether.io): Absolute Positionierung für responsive Apps
* [Vex](http://github.hubspot.com/vex/): Dialoge

### API

* Definition als OpenAPI mit [Swagger](https://swagger.io)
* Umsetzung als Rails-App mit:
	* Rails 5
	* Rails Background Jobs
	* Rails Websocket Server
	
* Nützliche Gems
	
	* Forms:
		* [simple_form](https://github.com/plataformatec/simple_form)
		* [reform](https://github.com/trailblazer/reform)

	* HTTP/Auth:
		* [activeresource](https://github.com/rails/activeresource)
		* [httparty](https://github.com/jnunemaker/httparty)
		* [webmock](https://github.com/bblimke/webmock)
		* [addressable](https://github.com/sporkmonger/addressable)
		* [oauth2](https://github.com/oauth-xx/oauth2)
		* [oauth-ruby](https://github.com/oauth-xx/oauth-ruby)
		* [fakeweb](https://github.com/chrisk/fakeweb)
	
	* Parsing JSON/XML:
		* [fast_jsonapi](https://github.com/Netflix/fast_jsonapi)
		* [feedparser](https://github.com/feedparser/feedparser)
		* [happymapper](https://github.com/jnunemaker/happymapper)
		* [feedjira](https://github.com/feedjira/feedjira)
		* [crack](https://github.com/jnunemaker/crack)
		* [json]()
		* [json-schema](https://github.com/ruby-json-schema/json-schema)
		* [nokogiri](https://github.com/sparklemotion/nokogiri)
		* [oj](https://github.com/ohler55/oj)
		* [multi_json](https://github.com/intridea/multi_json)
	
	* File-Upload
		* [paperclip](https://github.com/thoughtbot/paperclip)
		* [carrierwave](https://github.com/carrierwaveuploader/carrierwave)
		
	* Settings-Store
		* [settingslogic](https://github.com/binarylogic/settingslogic)
		* [behavior](https://github.com/paulca/behavior)
		* [ledermann-rails-settings]()
		
	* Background processing:
		* [sidekiq](https://github.com/mperham/sidekiq)
		* [whenever](https://github.com/javan/whenever)
		
	* API
	  * [(grape)](https://github.com/ruby-grape/grape)
          * [(json-resource](http://jsonapi-resources.com)      

	* CLI
		* [thor](https://github.com/erikhuda/thor)
		* [highline](https://github.com/JEG2/highline)
		
	* Debugging:
		* [byebug](https://github.com/deivid-rodriguez/byebug)
		* [better_errors](https://github.com/charliesome/better_errors)
	* Misc:
		* [friendly_id](https://github.com/norman/friendly_id)
		* [seed_dump](https://github.com/rroblak/seed_dump)
		* [seed-fu](https://github.com/mbleigh/seed-fu)
		* [mjml](https://github.com/MQuy/mjml)
		* [(dynamicattributes)](https://github.com/moiristo/dynamic_attributes)
		* [devise](https://github.com/plataformatec/devise)
		* [unread](https://github.com/ledermann/unread)
		* [gon](https://github.com/gazay/gon)
		* [listen](https://github.com/guard/listen)
		* [bootsnap](https://github.com/Shopify/bootsnap)
		* [rails-observers](https://github.com/rails/rails-observers)
		* [state_machines](https://github.com/state-machines/state_machines)
                * [rubyzip](https://github.com/rubyzip/rubyzip)
                * [ruby-git](https://github.com/ruby-git/ruby-git)

		
Alternativen:

* [Laravel Lumen](https://lumen.laravel.com): Sprache: PHP. Symfony-Scheduler für Refresh-Jobs, Model-

### Datenbank

* MySQL

### Layout

* Komponenten: [Bootstrap 4](https://getbootstrap.com) oder [Foundation](https://foundation.zurb.com)
* [Fontawesome](https://fontawesome.io) für Icons

### Lokalisierung

* Crowdsourcing [Glotpress](https://github.com/GlotPress/GlotPress-WP)

## mirrOS

### Modulanordnung (Grid-Layout)
Text kommt.

#### Grössen der Module
Text kommt.

#### Resizing der Module
Text kommt.

### Layouteinstellungen
Text kommt.

### Moduleinstellungen (Instanzeinstellungen)
Text kommt.

### Navigationbar
Text kommt.

### mirrOS Einstellungen
Text kommt.

### Zentrales Notification System

Ein zentrales und einheitliches Notification System soll bestimmte Meldungen an den Benutzer über den Spiegel ausgeben. Ein praktischer Anwendungsfall dafür wäre ein Output aus einem Script (siehe nächste Kapitel).

* `Lampen eingeschaltet`
* `Sprachbefehl XY erkannt`
* usw.


## Services

mirr.OS und Widgets können Services bereitstellen, die per API gesteuert werden. Die Scripts können idealerweise Shell, Python, Ruby oder andere ausführbare Scripts sein.

Beispiele:
* Die aktuell angezeigten Schlagzeilen des News-Moduls inkl. Link auf die Quelle an die hinterlegte Mailadresse schicken. So kann man weiterlesen, ohne die Quelle manuell rauszusuchen.
* Einen Steuerbefehl an eine verbundene SmartHome-API schicken
* Display manuell an/aus schalten

### Aktionen über Hardware-Buttons oder Touch

Externe Hardware-Buttons oder Touch-Kapazitive Sensoren sollen ermöglichen, bestimmte Aktionen direkt über den glancr auszuführen. Die verfügbaren Bedienelemente (Taster oder Touch-Sensor) lassen sich über die Konfigurationsoberfläche mit Aktionen belegen. Als Aktion stehen [Services](#services) zur Verfügung.

## Weitere Feature-Ideen
Hier sind einige grobe Ideen für Hard/Software-Features skizziert, die zukünftig in mirr.OS bzw. glancr wünschenswert wären.

### Background Module

Es soll möglich sein, bestimmte "Modul-Scripts" einzubinden ohne dafür ein Modul-Slot zu belegen. Das Script wird ebenfalls alle XY Minuten aktualisiert hat aber keine Anzeige im Frontend.

### Hotword Detection

Mit [Snowboy](https://snowboy.kitt.ai) soll eine Hotword Detection implementiert werden, mit der bestimmte Aktionen (Scripts) ausgeführt werden können.


## Module

### Aufbau

```
/module
/module/info.json
/module/sizes.json
/module/locales.json
/module/module.json
/module/seeds.json
/module/templates/
/module/templates/default.html
/module/templates/2x1.html
/module/settings/default.html
/module/settings/2x1.html
/module/frontend/default.js
/module/frontend/2x1.js
/module/scripts/lights_off.rb
/module/scripts/lights_blue.sh
/module/scripts/order_taxi.py
```

### Modulgrössen

```javascript
// sizes.json

{
	"sizes": [
		{
			"name": "default",
			"height": 3,
			"width": 6,
			"template": "default.html",
			"settings": "default.html",
			"script": "default.html"
		},
		{
			"name": "2x1",
			"height": 1,
			"width": 2,
			"template": "2x1.html",
			"settings": "2x1.html",
			"script": "2x1.html"
		},
		{
			"name": "1x1",
			"height": 1,
			"width": 1,
			"template": "1x1.html",
			"settings": "default.html",
			"script": "default.html"
		}
	]
}

```


### Initialisierung bzw. Reset eines Moduls

```javascript
// seeds.json

{
	"data": [
		{
			"key": "fuel_sort_by",
			"value": "name"
		},
		{
			"key": "fuel_max_stations",
			"value": 5
		}
	]
}

```

```javascript

```
### Sprachen

```javascript
// locales.json

{
	"locales": {
		"urls": [
			"http://46.101.225.168/glotpress/projects/system/netatmo/",
			"http://46.101.225.168/glotpress/projects/system/"
		]
	}
}

```


### `module.json`

```javascript
// module.json

{
	"module": {
		"depenencies": {
			"sources": [
				{
					"name": "tankerkoenig",
					"version": "1.0.0",
					"required": true
				},
				{
					"name": "spritpreisrechner",
					"version": "1.0.0",
					"required": true
				}
			]
		},
		"assets": [
			{
				"url": "https://code.jquery.com/jquery-3.2.1.min.js",
				"group": "script",
				"required_in": [
					"settings/default.html",
					"template/*"
				]
			},
			{
				"url": "https://opensource.keycdn.com/fontawesome/4.7.0/font-awesome.min.css ",
				"group": "stylesheet",
				"required_in": [
					"settings/1x1.html",
					"template/1x1.html"
				]
			}
		]
	}
}

```

### Modulinstanzen
Text kommt.

#### Modulinstanzen und Speichern der Daten
Text kommt.



## Datenquellen

### Aufbau
Text kommt.

### Datenquellen-Typ
Text kommt.

### Abhängigkeiten
Text kommt.

### Eigenschaften
Text kommt.

### Datenquelleninstanz
Text kommt.


### Namespacing
Text kommt.


## Lokalisierung
gettext-Kompatibilität ist wünschenswert, damit die bisherigen MO/PO-Dateien weiterverwendet werden können. POEdit und die Infrastruktur z. B. von Crowdin wären auch sehr praktisch.

https://www.i18next.com basiert auf gettext und hat Vue-Integrationen.

### Plattformen
Text kommt.

### Update-Prozess
Text kommt.

### Update Interval
Text kommt.