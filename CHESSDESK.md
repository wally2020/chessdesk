# Chessdesk

Chessdesk ist eine auf [Superdesk](https://www.superdesk.org/) basierende Schachredaktions- und Publikationsplattform. Das Projekt verbindet die Arbeitsweise eines professionellen Redaktionssystems mit den besonderen Anforderungen der Schachberichterstattung: Turniere planen, Meldungen und Analysen redaktionell bearbeiten, Medien verwalten und fertige Inhalte über mehrere Kanäle veröffentlichen.

> **Projektstand:** Der aktuelle `develop`-Branch bildet eine lauffähige Superdesk-Basis ab. Die allgemeine Redaktions-, Planungs- und Publikationsinfrastruktur ist vorhanden. Eigene Schachmodule – etwa PGN-Verarbeitung, Brettdarstellung oder Engine-Analyse – sind im derzeitigen Codebestand noch nicht implementiert und werden als nächste Ausbaustufe beschrieben.

## Zielbild

Chessdesk soll eine gemeinsame Arbeitsumgebung für Schachredaktionen, Turnierveranstalter, Vereine und freie Autor:innen bieten. Statt Texte, Partien, Bilder, Termine und Veröffentlichungen in getrennten Werkzeugen zu verwalten, führt die Plattform diese Bestandteile in einem nachvollziehbaren redaktionellen Ablauf zusammen.

Typische Einsatzbereiche sind:

- aktuelle Turnier- und Mannschaftsberichterstattung;
- Vor- und Nachberichte zu Runden, Wettkämpfen und Veranstaltungen;
- redaktionell kommentierte Partien und Stellungsausschnitte;
- Spieler:innen-, Vereins- und Turnierdossiers;
- Terminplanung, Aufgabenverteilung und Freigaben;
- Bild-, Video- und Dokumentenverwaltung;
- zeitgesteuerte und mehrkanalige Veröffentlichung;
- Aufbau eines durchsuchbaren Schach- und Redaktionsarchivs.

## Redaktioneller Arbeitsablauf

Der von Superdesk übernommene Workflow lässt sich für eine Schachredaktion folgendermaßen verwenden:

1. **Planen:** Turniere, Runden, Paarungen, Pressekonferenzen und Abgabetermine werden in der Planung erfasst.
2. **Zuweisen:** Beiträge, Fotos, Interviews oder Analysen werden Autor:innen und Redaktionsdesks zugeteilt.
3. **Erstellen:** Meldungen, Berichte und Analysen entstehen im Redaktionseditor; zugehörige Medien und künftig auch Partiedaten werden mitgeführt.
4. **Bearbeiten:** Inhalte durchlaufen definierte Arbeitsstufen, etwa Eingang, Bearbeitung, Schachprüfung, Schlussredaktion und Freigabe.
5. **Publizieren:** Freigegebene Beiträge werden sofort oder terminiert an konfigurierte Ausgabekanäle übergeben.
6. **Archivieren:** Versionen, Metadaten, Veröffentlichungsstatus und redaktionelle Änderungen bleiben nachvollziehbar und durchsuchbar.

Superdesk stellt dafür unter anderem Desks, Stages, Rollen und Rechte, Aufgaben, Monitoring, Versionierung, Planung, Suche, Medienverwaltung und Publishing-Schnittstellen bereit.

## Vorgesehene Schachfunktionen

Die schachspezifische Erweiterung soll modular erfolgen, damit der Superdesk-Kern wartbar und mit Upstream-Entwicklungen abgleichbar bleibt.

### Partie- und Stellungsdaten

- Import, Validierung und Export von PGN;
- Erfassung von FEN-Stellungen;
- Verknüpfung von Partien mit Turnieren, Runden, Spieler:innen und Artikeln;
- Varianten, Kommentare, Zeitangaben und Ergebnisdaten;
- interaktive Brettdarstellung im Editor und in veröffentlichten Beiträgen.

### Analyse

- optionale Anbindung einer UCI-Schachengine, beispielsweise Stockfish;
- Speicherung redaktionell ausgewählter Varianten statt unkontrollierter Engine-Ausgaben;
- Kennzeichnung von menschlichen Kommentaren und maschineller Analyse;
- konfigurierbare Analysetiefe, Ressourcenbegrenzung und Warteschlangenverarbeitung.

### Schachmetadaten

- Spieler:innen mit FIDE-ID, Wertungszahl, Titel und Föderation;
- Turniere mit Austragungsort, Zeitraum, Modus und Bedenkzeit;
- Runden, Paarungen, Ergebnisse und Tabellen;
- Eröffnungen über ECO-Codes;
- Vereine, Mannschaften und Serien.

### Publikation

- Einbettung nachspielbarer Partien in Webbeiträge;
- Ergebnisdienste, Rundenzusammenfassungen und Live-Ticker;
- Ausgabe strukturierter Daten über API und Feeds;
- kanalabhängige Darstellung für Website, Newsletter, soziale Medien und Druckvorstufen.

## Architektur

Chessdesk übernimmt die getrennte Client-/Server-Architektur von Superdesk.

| Komponente | Aufgabe | Technische Basis im aktuellen Branch |
|---|---|---|
| `client/` | Browseroberfläche, Editor und Erweiterungen | Superdesk Client Core, TypeScript/JavaScript, AngularJS/React-Komponenten, Grunt |
| `server/` | REST-API, Geschäftslogik, Authentifizierung und Hintergrundaufgaben | Python 3.12, Superdesk Core, Quart/Eve, Celery |
| MongoDB | operative Inhalte und Metadaten | MongoDB 6 |
| Elasticsearch | Volltextsuche und Indizierung | Elasticsearch 7.17 |
| Redis | Queue-, Cache- und Worker-Infrastruktur | Redis 8 |
| Planning | Ereignisse, Aufgaben und redaktionelle Planung | `superdesk-planning` |
| Analytics | redaktionelle Auswertungen | `superdesk-analytics` |
| Publisher | Übergabe an Publikationskanäle | `superdesk-publisher` |

Der Client lädt im aktuellen Stand die Planning- und Broadcasting-Erweiterungen sowie mehrere Superdesk-Core-Erweiterungen. Die Serverabhängigkeiten binden Superdesk Core, Planning und Analytics aus deren `develop`-Branches ein.

## Repository-Struktur

```text
chessdesk/
├── client/                  # Webclient, Konfiguration und Erweiterungsregistrierung
├── server/                  # Python-Server, Daten und Serverkonfiguration
├── scripts/dev/             # Einrichtung, Start, Stopp und Extension-Verwaltung
├── docker-compose.yml       # vollständig containerisierte lokale Umgebung
├── docker-compose.dev.yml   # Backend in Docker, Client nativ mit Watch-Modus
├── DEVSETUP.md              # ausführliche Entwicklungsanleitung
└── CHESSDESK.md             # Projektdokumentation und fachliches Zielbild
```

## Lokaler Schnellstart

Voraussetzung ist eine laufende Docker-Installation.

```sh
docker compose up -d
docker compose exec superdesk-server python manage.py app:initialize_data
docker compose exec superdesk-server python manage.py users:create \
  -u admin -p admin -e admin@localhost --admin
```

Danach ist die Anwendung unter [http://localhost:8080](http://localhost:8080) erreichbar. Die im Beispiel angelegten Zugangsdaten lauten `admin` / `admin` und dürfen nur lokal verwendet werden.

## Entwicklung

Für regelmäßige Arbeiten am Client ist der gemischte Entwicklungsmodus vorgesehen: Server, MongoDB, Redis und Elasticsearch laufen in Docker; der Client läuft nativ mit Dateibeobachtung.

Voraussetzungen:

- Docker Desktop;
- [Volta](https://volta.sh/) für die im Projekt festgelegte Node-Version;
- die Schwester-Repositories `superdesk-client-core` und `superdesk-planning` im selben übergeordneten Verzeichnis;
- optional `superdesk-analytics` und `superdesk-publisher`.

Ersteinrichtung und täglicher Betrieb:

```sh
./scripts/dev/setup.sh
./scripts/dev/up.sh
./scripts/dev/down.sh
```

Der Client ist in diesem Modus unter [http://localhost:9000](http://localhost:9000) erreichbar. Die API verwendet unter Linux standardmäßig Port `5000`, unter macOS wegen möglicher Konflikte mit AirPlay automatisch Port `5001`. Weitere Details, Optionen und Fehlerbehebung stehen in [DEVSETUP.md](./DEVSETUP.md).

## Konfiguration und Sicherheit

Die Docker-Compose-Dateien sind für lokale Entwicklung und Demonstration ausgelegt. Vor einem produktiven Einsatz sind insbesondere folgende Punkte erforderlich:

- sämtliche Beispielzugänge und `SECRET_KEY`-Werte ersetzen;
- TLS, öffentliche URLs und Reverse Proxy korrekt konfigurieren;
- Datenbanken und Redis nicht ungeschützt veröffentlichen;
- Rollen, Rechte, Desks und Freigabestufen für die jeweilige Redaktion definieren;
- Backups, Monitoring, Protokollierung und Wiederherstellung einrichten;
- Publisher-Ziele und externe Dienste mit getrennten Zugangsdaten konfigurieren;
- Datenschutz, Bildrechte und Aufbewahrungsfristen redaktionell festlegen.

Die Standardkonfiguration verwendet derzeit `Europe/Prague` als Zeitzone. Für einen österreichischen Einsatz sollte sie konsistent auf `Europe/Vienna` umgestellt werden.

## Aktueller Stand und Abgrenzung

Der Branch `develop` enthält derzeit vor allem den Superdesk-Anwendungsrahmen und die lokale Entwicklungsinfrastruktur. Bereits nutzbar beziehungsweise konfigurierbar sind die allgemeinen Superdesk-Funktionen für Redaktion, Planung, Aufgaben, Medien, Suche, Monitoring und Publikationsabläufe.

Noch nicht als Chessdesk-spezifischer Code vorhanden sind insbesondere:

- PGN- und FEN-Datenmodelle;
- Schachbrett- und Partiedarstellung;
- Spieler:innen-, Turnier- und Paarungsverwaltung;
- Engine-Anbindung;
- Ergebnisimport und Live-Partie-Schnittstellen;
- eigens benannte Chessdesk-Oberfläche und Beispieldaten.

Diese klare Trennung ist wichtig: Chessdesk ist technisch bereits eine belastbare Redaktionsbasis, befindet sich fachlich aber noch am Beginn der Schachspezialisierung.

## Empfohlene Ausbaureihenfolge

1. **Produktidentität und Grundkonfiguration:** Name, Logo, Sprache, Zeitzone, Rollen, Desks und redaktionelle Stages.
2. **Schachdatenmodell:** PGN, FEN, Spieler:innen, Turniere, Runden und Paarungen.
3. **Editor-Erweiterung:** Partieimport, Brettvorschau und Einbettung in Artikel.
4. **Publikationsformat:** standardisierte Ausgabe von Partien und Metadaten über API und Webkomponente.
5. **Datenquellen:** kontrollierter Import von Turnier- und Ergebnisdaten.
6. **Analyse:** asynchrone Engine-Verarbeitung mit transparenten Grenzen und redaktioneller Freigabe.
7. **Betrieb:** Tests, Migrationen, Sicherheitskonzept, Backups und produktionsfähiges Deployment.

## Upstream und Lizenz

Chessdesk basiert auf dem Open-Source-Projekt [Superdesk](https://github.com/superdesk/superdesk), das von [Sourcefabric](https://www.sourcefabric.org/) und der Community entwickelt wird. Änderungen sollten möglichst als klar abgegrenzte Erweiterungen umgesetzt und regelmäßig mit dem Superdesk-Upstream abgeglichen werden.

Der aktuelle Repository-Code steht unter der [GNU Affero General Public License, Version 3](./LICENSE) (AGPL-3.0). Bei Bereitstellung der Plattform über ein Netzwerk sind die Bedingungen der AGPL zu beachten; insbesondere müssen Nutzer:innen des Dienstes Zugang zum korrespondierenden Quellcode der eingesetzten Version erhalten.
