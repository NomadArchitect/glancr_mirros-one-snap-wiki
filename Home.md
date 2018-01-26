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
8. [API](#api-1)

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




## API

### Dokumentation mit Swagger UI

```bash
docker pull swaggerapi/swagger-editor
docker run -p 8080:8080 swaggerapi/swagger-editor
open http://localhost:8080
```

Dann die Datei glancr-openapi.yaml aus dem Repository laden.

### Idee

Jeder Spiegel besitzt eine eigene API. Die GUI der Konfigurationsseite und Anzeige soll unäbhängig von der eigentlichen Logik funktionieren. So ist die API eigentlich das zentrale Herzstück des Spiegels, über welche die ganze Kommunikation läuft.

Das Frontend bezieht von der API die Daten, welche auf dem Frontend angezeigt werden. Der Benutzer konfiguriert also seine Datenquelle und die Daten werden dann über die API zur Verfügung gestellt, damit das Frontend auf diese Daten zugreifen kann.

Im Backend: Die Einstellungen von mirr.OS, die Konfiguration von mirr.OS, die Einstellugen der Modulinstanzen sowie die Anordnung der Module kann alles über die API abgefragt werden und anschliessend wieder gespeichert werden.

Mit diesem Setup ist es auch möglich, die API quasi als zentralen Hub im eigenen Netzwerk zu verwenden. So können z.B. aktuelle Daten von Lampenzuständen oder die Temperatur vom Thermostat von ein und der selben Quelle abgefragt werden und die Daten andersweitig verwenden. Die zur Verfügung stehenden Daten hängt von den konfigurierten Datenquellen ab und wird natürlich auch für die Anzeige im Frontend verwendet.

So wird eine zentrale und einheitliche Abfragemöglichkeit von verschiedenen Datenquellen angeboten, die alle gleich formatiert sind.

Hier gibt es z.B. das Anwendungbeispiel mit dem Tanken Modul. Es gibt verschiedene Datenquellen für ein bestimmtes Modul (Tankerkönig.de / Spritpreisrechner.at). Damit nicht zwei verschiedne Moduel entwickelt werden müssen, werden dann idealerweise die Daten dieser Datenquellen von der API einheitlich formatiert und zur Verfügung gestellt. In den Modul(-instanz)einstellungen gibt es dann die Möglichkeit auszuwählen, von welcher Datenquelle diese Instanz die Daten beziehen soll.

Quasi spielt die interne API hier eine Zwischenstelle. Mit den zur Verfügung stehenden Datenquelle und den vom Benutzer eingegeben Einstellungen (wie. z.B. Keys, Tokens oder Accounts) werden die Daten von der externen API abgefragt (z.B. Tanken), dann einheitlich formatiert und dann über die interne API (z.B. JSON und/oder XML) zur Verfügung gestellt.

Ein weiterer Vorteil dieser Lösung ist, dass so alles von der Darstellung unabhängig ist.
Sei es, wenn jemand sein eigenes Interface für die Steuerung für mirr.OS bauen will, später mal eine mobile native Applikation veröffentlicht werden soll oder es letztendlich nur für die Anzeige im Frontend verwendet wird, die API kann immer als zentraler Kommunkationspunkt genutzt werden.

### ReST vs. (JSON-)RPC
Die mirr.OS API soll sowohl Daten liefern als auch Konfigurationsobjekte speichern und Aktionen im Backend steuern. Die meisten dazu benötigten Datenstrukturen lassen sich sinnvoll als Ressourcen modellieren.
Die gezielte Adressierung z. B. von Systemeinstellungen ist sinnvoll, weil mit Ausnahme der WLAN-Konfiguration jedes Feld ohne gesonderten Klick gespeichert wird.



http://www.ics.uci.edu/~fielding/pubs/dissertation/top.htm
https://www.smashingmagazine.com/2016/09/understanding-rest-and-rpc-for-http-apis/#what-are-they-for

### Benötigte Operationen

Widgets:
* CRUD
* List
* [rel] Alle Instanzen eines Widgets

Widget-Instanzen:
* CRUD
* List
* [rel] Widget-Klasse einer Instanz

Datenquellen:
* Installieren (C)
* Konfiguration lesen (R)
* Konfiguration aktualisieren (U)
* Deinstallieren (D)

### Groups

`Groups` regeln, welche `Modules` und `Sources` miteinander funktionieren.

So haben zum Beispiel das `Module` `calendar_week` und die `Source` `Google Kalender` beide die `Group` `calendar`. Über diese Beziehung wird festgelegt, dass `Modules` und `Sources` der gleichen Gruppe miteinander kompatibel sind.


#### Beziehungen

Feld | Model | Identifier | Beschreibung
---  | ---   | ---        | ---
category | `Category` | `Category.name` | Die Kategoriezugehörigkeit dieser Gruppe
sources | `Source` | - | Alle Datenquellen die dieser Gruppe angehören
modules | `Module` | - | Alle Module die dieser Gruppe angehören


#### Aufbau des Models

```javascript
{
	"name": String,
	"model": Model,
	"category": Category,
	"source_structure": Object,
	"modules": [Module],
	"sources": [Source]
}
```

#### Beispiel

```javascript
{
	"name": "calendar",
	"model": "group",
	"source_structure": {},
	"category": "producivity",
	"modules": [...],
	"sources": [...]
}
```

### Modules

#### Endpunkte

`/api/modules`<br>
`/api/modules/{module_name}`<br>

#### Beziehungen

Feld | Model | Identifier | Beschreibung
---  | ---   | ---        | ---
group | `Group` | `Group.name` | Die Gruppe dieses Modules
category | `Category` | `Category.name` | Die Kategorie dieses Modules
sources | `Source` | - | Die mit diesem Modul kompatiblen Datenquellen
languages | `Language` | - | Die zu verfügbaren stehenden Sprachen dieses Moduls
instances | `ModuleInstance` | - | Instanzen, die es von diesem Modul gibt


#### Aufbau des Models

```javascript
{
	"name": String,
	"group": Group,
	"model": Model,
	"author": String,
	"category": Category,
	"version": String,
	"path": String,
	"website": String,
	"repository": String,
	"sizes": Array,
	"sources": [Source],
	"languages": [Language],
	"instances": [ModuleInstance]
}
```

#### Beispiel

```javascript
{
	"name": "fuel",
	"group": "fuel",
	"model": "module",
	"author": "Marco Roth",
	"category": "productiviy",
	"version": "1.0.0",
	"path": "/api/sources/modules/fuel",
	"website": "https://glancr.de/modules/productivity/fuel/",
	"repository": "https://github.com/marcoroth/mirrOS_fuel",
	"sizes": [sizes.json],
	"sources": [...],
	"languages": [...],
	"instances": [...]
}
```


<br>
___
<br>

### ModuleInstances

#### Endpunkte

`/api/modules/{module_name}/{instance_id}`<br>
`/api/modules/{module_name}/{instance_id}/settings`<br>

#### Beziehungen

Feld | Model | Identifier | Beschreibung
---  | ---   | ---        | ---
module | `Module` | `Module.name` | Das übergeordnete Modul dieser Instanz


#### Aufbau des Models

```javascript
{
	"id": Integer,
	"module": Module,
	"model": Model,
	"path": String,
	"settings": Object,
	"position": {
		"width": Integer,
		"height": Integer,
		"col": Integer,
		"row": Integer
	}
}
```

#### Beispiel

```javascript
{
	"id": 1,
	"module": "fuel",
	"model": "module_instance",
	"path": "/api/modules/fuel/1",
	"settings": {},
	"position": {
		"width": 6,
		"height": 3,
		"col": 1,
		"row": 1
	}
}
```


<br>
___
<br>


### Sources

#### Endpunkte

`/api/sources`<br>
`/api/sources/{source_name}`<br>

#### Beziehungen

Feld | Model | Identifier | Beschreibung
---  | ---   | ---        | ---
group | `Group` | `Group.name` | Die Gruppe dieser Datenquelle
category | `Category` | `Category.name` | Die Kategorie dieser Datenquelle
modules | `Module` | - | Die mit dieser Datenquelle kompatiblen Module
languages | `Language` | - | Die zu verfügbaren stehenden Sprachen dieser Datenquelle
instances | `SourceInstance` | - | Instanzen, die es von diesem Datenquelle gibt

#### Aufbau des Models

```javascript
{
	"name": String,
	"group": Group,
	"model": Model,
	"category": Category,
	"version": String,
	"author": String,
	"path": String,
	"website": String,
	"modules": [Module],
	"languages": [Language],
	"instances": [SourceInstance]
}
```

#### Beispiel

```javascript
{
	"name": "google",
	"group": "calendar",
	"model": "source",
	"category": "productivity",
	"version": "1.0.0",
	"author": "Mattes Angelus",
	"path": "/api/sources/calendar/google/",
	"website": "http://glancr.de/sources/google/",
	"modules": [...],
	"languages": [...],
	"instances": [...]
}
```


<br>
___
<br>


### SourceInstances

#### Endpunkte

`/api/sources/{source_name}/{instance_id}`<br>
`/api/modules/{source_name}/{instance_id}/settings`<br>
`/api/modules/{source_name}/{instance_id}/data`<br>

#### Beziehungen

Feld | Model | Identifier | Beschreibung
---  | ---   | ---        | ---
category | `Category` | `Category.name` | Die Kategoriezugehörigkeit dieses Typs
sources | `Source` | - | Die vom diesem Typ verfügbaren Datequellen
modules | `Module` | - | Die vom diesem Typ verfügbaren Module


#### Aufbau des Models

```javascript
{
	"id": Integer,
	"source": Source,
	"model": Model,
	"path": String,
	"data": Object,
	"settings": Object
}
```

#### Beispiel


```javascript
{
	"id": 1,
	"source": "google",
	"model": "source_instance",
	"path": "/api/sources/google/1",
	"data": {},
	"settings": {}
}
```

<br>
___
<br>


### Categories

#### Endpunkte

`/api/categories`<br>
`/api/categories/{category_name}`

#### Beziehungen

Feld | Model | Identifier | Beschreibung
---  | ---   | ---        | ---
sources | `Source` | - | Datenquellen, die dieser Kategorie angehören
modules | `Module` | - | Module, die dieser Kategorie angehören

#### Aufbau des Models


```javascript
{
	"name": String,
	"model": Model,
	"path": String,
	"website": String,
	"modules": [Module],
	"sources": [Source]
}
```

#### Beispiel

```javascript
{
	"name": "productivity",
	"model": "category",
	"path": "/api/categories/productivity/",
	"website": "http://glancr.de/modules/productivity/",
	"modules": [...],
	"sources": [...]
}
```

<br>
___
<br>


### Languages

#### Endpunkte

`/api/languages`<br>
`/api/languages/{language_name}`

#### Beziehungen

Feld | Model | Identifier | Beschreibung
---  | ---   | ---        | ---
sources | `Source` | - | Datenquellen, die diese Sprache unterstützen
modules | `Module` | - | Module, die diese Sprache unterstützen
translations | `Translation` | - | Übersetzungen, die es in dieser Sprache gibt


#### Aufbau des Models

```javascript
{
	"name": String,
	"code": String,
	"model": Model,
	"path": String,
	"modules": [Module],
	"sources": [Source],
	"translations": [Translation]  
}
```

#### Beispiel

```javascript
{
	"name": "Deutsch",
	"code": "de_DE",
	"model": "language",
	"path": "/api/languages/de_DE",
	"modules": [...],
	"sources": [...],
	"translations": [...]
}
```



<br>
___
<br>

### Translation

#### Endpunkte

`/api/translations`<br>
`/api/translations/system`<br>
`/api/translations/{module_name}`<br>
`/api/translations/{source_name}`<br>
`/api/translations/{language_name}`<br>
`/api/translations/{language_name}/system`<br>
`/api/translations/{language_name}/{module_name}`<br>
`/api/translations/{language_name}/{source_name}`<br>


#### Beziehungen

Feld | Model | Identifier | Beschreibung
---  | ---   | ---        | ---
source | `Source` | `Source.name` | Datenquelle, für welches diese Übersetzung ist
module | `Module` | `Module.name` | Modul, für welches diese Übersetzung ist
language | `Langaue` | `Langaue.code` | Sprache, in welcher diese Übersetzung ist


#### Aufbau des Models

```javascript
{
	"name": String,
	"model": Model,
	"language": Language,
	"module": Module,
	"source": Source,
	"data": Object
}
```

#### Beispiel

```javascript
{
	"name": "fuel-de_DE",
	"model": "translation",
	"langugage": "de_DE"
	"module": "fuel",
	"source": null,
	"data": {
		"fuel_title": "Tanken",
		"fuel_description": "Modul zum Anzeigen der billgsten Tankstelle in deiner Nähe"
	}
}
```

<br>
___
<br>

### Scripts

#### Endpunkte

`/api/scripts`<br>
`/api/scripts/{script_name}`<br>
`/api/scripts/{script_name}/trigger`<br>
`/api/scripts/{script_name}/toggle`<br>
`/api/scripts/{script_name}/on`<br>
`/api/scripts/{script_name}/off`<br>

#### Beziehungen

Feld | Model | Identifier | Beschreibung
---  | ---   | ---        | ---
module | `Module` | `Module.name` | Modul, zu welchem dieses Script gehört

#### Aufbau des Models

```javascript
{
	"name": String,
	"model": Model,
	"module": Module,
	"button_type": ["toggle", "once"],
	"path": String,
	"type": String,
	"exec": String,
	"settings": Object
}
```

#### Beispiel

```javascript
{
	"name": "lamps_on",
	"model": "script",
	"module": Module,
	"button_type": "toggle"
	"path": "/scripts/hue/lamps.sh",
	"type": "Shell",
	"exec": "bash {path}",
	"settings": {
		"color": "blue",
		"brightness": 90,
		"room": "kitchen"
	}
}
```

<br>
___
<br>


### Beispiel-Abfragen (vereinfacht)


### `/api`

```javascript
// Example: /api

{
	"name": "Glancr mirrOS",
	"version": "1.0.0",
	"webserver": "Apache 2",
	"device": "Raspberry 3",
	"os": "Raspian X.Y",
	"endpoints": [
		"/api/info",
		"/api/user",
		...
	],
	"documentation": "https://glancr.de/api-documentation"
}

```


### `/api/user`

```javascript
// Example: /api/user

{
	"name": "Marco Roth",
	"firstname": "Marco",
	"lastname": "Roth",
	"email": "marco.roth@intergga.ch",
	"city": "Basel",
	"country": "CH",
	"language": "de_DE"
}
```


### `/api/groups`

```javascript
// Example: /api/groups

{
	"groups": [
		{
			"name": "calendar",
			"modules": [
				{ "name": "calendar_week", ... },
				{ "name": "calendar_today", ... },
				{ "name": "calendar_next", ... }
			],
			"sources": [
				{ "name": "google", ... },
				{ "name": "icloud", ... },
				{ "name": "ical", ... }
			]
		},
		{
			"name": "fuel",
			"modules": [
				{ "name": "fuel", ... }
			],
			"sources": [
				{ "name": "Tankerkönig", ... },
				{ "name": "Spritpreisrechner", ... }
			]
		}
	]
}

```


### `/api/groups/{group_name}`

```javascript

// Example: /api/groups/calendar

{

}

```

### `/api/sources`

```javascript

// Example: /api/sources

{
	"sources": [
		{
			"name": "google",
			"group": "calendar",
			"version": "1.0.0",
			"author": "Mattes Angelus",
			"path": "/api/sources/calendar/google",
			"website": "https://google.com"  
		},
		{
			"name": "tankerkoenig",
			"group": "fuel",
			"version": "1.0.0",
			"path": "/api/sources/fuel/tankerkoenig",
			"website": "https://google.com"  
		}
	]
}

```

### `/api/sources/{source_name}`

```javascript

// Example: /api/sources/calendar

{
	"group": "calendar",
	"sources": [
		{
			"name": "google",
			"group": "calendar",
			"version": "1.0.0",
			"author": "Marco Roth",
			"path": "/api/sources/calendar/google"  
		},
		{
			"name": "icloud",
			"group": "calendar",
			"version": "1.0.0",
			"author": "Marco Roth",
			"path": "/api/sources/calendar/icloud"  
		},
		{
			"name": "ical",
			"group": "calendar",
			"version": "1.0.0",
			"author": "Marco Roth",
			"path": "/api/sources/calendar/ical"  
		}
	]
}

```


### `/api/sources/{source_name}/{instance_id}`

```javascript

// Example: /api/sources/calendar/1/

{

}

```


### `/api/sources/{source_name}/{instance_id}/settings`

```javascript

// Example: /api/sources/calendar/1/settings

{

}

```


### `/api/sources/{source_name}/{instance_id}/data`

```javascript

// Example: /api/sources/calendar/1/data

{

}

```


### `/api/modules`

```javascript

// Example: /api/modules

{
	"modules": [
		{
			"name": "fuel",
			"group": "fuel",
			"author": "Marco Roth",
			"version": "1.0.0",
			"path": "/api/sources/fuel/fuel"  
		},
		{
			"name": "calendar_week",
			"group": "calendar",
			"author": "Mattes Angelus",
			"version": "1.0.0",
			"path": "/api/sources/calendar/calendar_week"  
		}
	]
}

```


### `/api/modules/{module_name}`

```javascript
// Example: /api/modules/fuel

{

}

```


### `/api/modules/{module_name}/{instance_id}`

```javascript
// Example: /api/modules/fuel/1

{

}

```

### `/api/modules/{module_name}/{instance_id}/settings`

```javascript
// Example: /api/modules/fuel/1/settings

{

}

```


### `/api/categories`

```javascript
// Example: /api/categories

{
	"categories": [
		{

		}
	]
}

```


### `/api/categories/{category_name}`

```javascript
// Example: /api/modules/categories/productivity

{

}

```
