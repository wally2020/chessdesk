# Chessdesk – README zum Neustart

**Projekt:** Chessdesk  
**Repository:** `wally2020/chessdesk`  
**Basis:** aktueller Superdesk-Fork  
**Arbeitsbranch:** `develop`  
**Projektstart:** 08.09.2026  
**Lizenzbasis:** AGPL-3.0  
**Status:** technische Basis vorhanden, Schachspezialisierung noch am Anfang

---

## 1. Kurzfassung

Chessdesk ist eine auf Superdesk basierende **Schachredaktions- und Publikationsplattform**.

Die Grundidee lautet:

> **Superdesk stellt die Redaktionsmaschine bereit; Chessdesk ergänzt die schachspezifische Fachlogik.**

Chessdesk soll keine bloße Schach-Website werden, sondern eine vollständige Arbeitsumgebung für Redaktionen, Turnierveranstalter, Vereine und freie Autor:innen.

Der vorhandene Superdesk-Kern liefert bereits:

- Benutzer- und Rechteverwaltung;
- redaktionelle Workflows;
- Planung;
- Medienverwaltung;
- Suche;
- Versionierung;
- Monitoring;
- Publishing-Schnittstellen.

Chessdesk ergänzt darauf aufbauend insbesondere:

- PGN;
- FEN;
- interaktive Schachbretter;
- Spieler:innen;
- Turniere;
- Runden;
- Paarungen;
- Ergebnisse;
- ECO-Daten;
- optionale Engine-Analyse;
- ein öffentliches Schachzeitungs-Frontend.

---

## 2. Entstehung und Ausgangslage

Chessdesk entstand im September 2026 aus der Überlegung, für eine geplante
Schachzeitung nicht erneut ein vollständiges Redaktionssystem von Grund auf zu
entwickeln, sondern eine vorhandene professionelle Open-Source-Plattform um
schachspezifische Funktionen zu erweitern.

Als technische Basis wurde Superdesk gewählt. Superdesk bringt bereits jene
Infrastruktur mit, die bei einer eigenständigen Neuentwicklung einen erheblichen
Teil des Aufwandes verursachen würde: Benutzer- und Rechteverwaltung,
redaktionelle Workflows, Planung, Medienverwaltung, Suche, Versionierung,
Monitoring und Publikationsprozesse.

Am 8. September 2026 wurde dafür der aktuelle `develop`-Branch von Superdesk
in das Repository `wally2020/chessdesk` übernommen.

Ein wesentlich älterer Superdesk-Fork im selben GitHub-Account aus dem Jahr
2017 wurde zuvor geprüft, aber bewusst **nicht** als Entwicklungsbasis verwendet.

Der alte Fork bleibt höchstens als historisches Referenzobjekt interessant.

---

## 3. Herkunft des Projekts

| Ebene | Herkunft | Aufgabe |
|---|---|---|
| Superdesk | Sourcefabric / Superdesk Community | allgemeines Redaktionssystem |
| Chessdesk-Basis | Fork des aktuellen Superdesk-`develop` | technische Ausgangsplattform |
| Chessdesk-Erweiterungen | eigenes Projekt | Schachlogik, Datenmodelle, Darstellung und Produktidentität |

Wichtig für die weitere Entwicklung:

> Änderungen am allgemeinen Superdesk-Kern möglichst vermeiden, solange dieselbe Funktion über Konfiguration, Erweiterungen oder klar abgegrenzte Module realisiert werden kann.

Damit bleibt der Fork besser mit dem Upstream synchronisierbar.

---

## 4. Zielbild

Chessdesk soll Texte, Partien, Bilder, Termine, Ergebnisse und Veröffentlichungen in einem gemeinsamen redaktionellen Ablauf zusammenführen.

Typische Einsatzbereiche:

- aktuelle Turnier- und Mannschaftsberichterstattung;
- Vor- und Nachberichte;
- kommentierte Partien;
- Stellungsausschnitte;
- Spieler:innen-Dossiers;
- Vereins- und Turnierdossiers;
- Terminplanung;
- Aufgabenverteilung;
- Bild-, Video- und Dokumentenverwaltung;
- zeitgesteuerte Veröffentlichung;
- mehrkanalige Veröffentlichung;
- Aufbau eines durchsuchbaren Schacharchivs.

---

## 5. Redaktioneller Workflow

Der übernommene Superdesk-Workflow wird für Schach ungefähr so verwendet:

1. **Planen** – Turniere, Runden, Paarungen, Termine und Presseereignisse.
2. **Zuweisen** – Beiträge, Bilder, Interviews und Analysen.
3. **Erstellen** – Meldungen, Berichte und Analysen.
4. **Bearbeiten** – Eingang, Bearbeitung, Schachprüfung, Schlussredaktion, Freigabe.
5. **Publizieren** – sofort oder terminiert.
6. **Archivieren** – Versionen, Metadaten, Publikationsstatus und redaktionelle Änderungen.

---

## 6. Ist-/Soll-Zustand

| Bereich | Ist-Zustand | Ziel |
|---|---|---|
| Redaktion | Superdesk-Funktionen vorhanden | schachspezifischer Workflow |
| Benutzer/Rollen | vorhanden | Rollen für Schachredaktion |
| Planung | vorhanden | Turniere, Runden und Ereignisse |
| Artikel | vorhanden | Artikel mit strukturierten Partiedaten |
| Medien | vorhanden | Bilder, Videos und Schachdokumente |
| Suche/Archiv | vorhanden | Suche nach Spielern, Turnieren, ECO und Partien |
| PGN | noch nicht implementiert | Import, Validierung, Speicherung, Export |
| FEN | noch nicht implementiert | Stellungen speichern und darstellen |
| Schachbrett | noch nicht implementiert | interaktive Partie- und Stellungsanzeige |
| Engine | noch nicht implementiert | optionale asynchrone Analyse |
| Spieler:innen | kein Chessdesk-Modell | strukturierte Spielerprofile |
| Turniere | kein Chessdesk-Modell | Turniere, Runden, Paarungen, Ergebnisse |
| Zeitung/Frontend | noch festzulegen | öffentliches Chessdesk-Angebot |

---

## 7. Eigenanteil von Chessdesk

Der eigentliche Entwicklungsgegenstand beginnt dort, wo die allgemeinen Funktionen von Superdesk enden.

Geplanter Eigenanteil:

- Schachdatenmodelle;
- PGN- und FEN-Verarbeitung;
- Spieler-, Turnier-, Runden- und Paarungsdaten;
- Verknüpfung zwischen Artikeln und Schachdaten;
- interaktive Brettdarstellung;
- schachspezifische Suche;
- Ergebnis- und Turnierimporte;
- optionale Engine-Analyse;
- Chessdesk-Branding;
- öffentliches Schachzeitungs-Frontend.

---

## 8. Systemidee

```text
                         CHESSDESK

        ┌───────────────────────────────────┐
        │           SCHACHREDAKTION          │
        │                                   │
        │ Texte · Bilder · Termine · Partien│
        └─────────────────┬─────────────────┘
                          │
                          ▼
        ┌───────────────────────────────────┐
        │          SUPERDESK-KERN            │
        │                                   │
        │ Workflow · Rechte · Planung       │
        │ Suche · Medien · Publishing       │
        └─────────────────┬─────────────────┘
                          │
             ┌────────────┴────────────┐
             ▼                         ▼
   ┌──────────────────┐      ┌──────────────────┐
   │  SCHACHMODULE    │      │   PUBLIKATION    │
   │                  │      │                  │
   │ PGN / FEN        │      │ Website          │
   │ Spieler:innen    │      │ Newsletter       │
   │ Turniere         │      │ Feeds / API      │
   │ Brett            │      │ weitere Kanäle   │
   │ Engine optional  │      │                  │
   └──────────────────┘      └──────────────────┘
```

Das Zielmodell lautet damit:

> **REDAKTION + SCHACH + PUBLIKATION**

---

## 9. Architektur

Chessdesk übernimmt die getrennte Client-/Server-Architektur von Superdesk.

| Komponente | Aufgabe |
|---|---|
| `client/` | Browseroberfläche, Editor, Erweiterungen |
| `server/` | REST/API, Geschäftslogik, Authentifizierung, Hintergrundaufgaben |
| MongoDB | operative Inhalte und Metadaten |
| Elasticsearch | Volltextsuche und Indizierung |
| Redis | Queue-, Cache- und Worker-Infrastruktur |
| Planning | Ereignisse, Aufgaben und redaktionelle Planung |
| Analytics | redaktionelle Auswertungen |
| Publisher | Übergabe an Publikationskanäle |

Die genauen technischen Versionsstände sollen bei jedem größeren Upstream-Update erneut gegen die tatsächlichen Konfigurationsdateien geprüft werden.

---

## 10. Repository-Struktur

```text
chessdesk/
├── client/
├── server/
├── scripts/dev/
├── docker-compose.yml
├── docker-compose.dev.yml
├── DEVSETUP.md
├── CHESSDESK.md
└── README_NEUSTART.md
```

---

## 11. Lokaler Schnellstart

Voraussetzung ist Docker.

```sh
docker compose up -d
docker compose exec superdesk-server python manage.py app:initialize_data
docker compose exec superdesk-server python manage.py users:create \
  -u admin -p admin -e admin@localhost --admin
```

Danach sollte die Anwendung lokal unter:

```text
http://localhost:8080
```

erreichbar sein.

Die Beispielzugänge `admin/admin` nur lokal verwenden.

---

## 12. Entwicklungsmodus

Für regelmäßige Entwicklung:

```sh
./scripts/dev/setup.sh
./scripts/dev/up.sh
./scripts/dev/down.sh
```

Für Client-Entwicklung wird ein gemischter Modus genutzt: Backend-Dienste in Docker, Client nativ mit Watch-Modus.

---

## 13. Technische Leitentscheidung

Für die erste Entwicklungsphase gilt:

> **Upstream möglichst wenig verändern – Chessdesk möglichst modular ergänzen.**

Schachspezifische Funktionen sollen bevorzugt als Erweiterungen, zusätzliche Datenmodelle, Dienste, Frontend-Komponenten sowie Import-/Exportmodule gebaut werden.

Der Superdesk-Kern selbst soll nur dann verändert werden, wenn es technisch wirklich nötig ist.

---

## 14. Schach-Datenmodell – erste Zielstruktur

Die folgende Struktur ist noch keine endgültige Implementierung, aber ein sinnvoller Zielrahmen.

### Partie

```text
Game
├── id
├── white_player
├── black_player
├── result
├── date
├── tournament
├── round
├── eco
├── pgn
├── initial_fen
└── annotations
```

### Spieler:in

```text
Player
├── id
├── name
├── fide_id
├── title
├── rating
├── federation
└── birth_year
```

### Turnier

```text
Tournament
├── id
├── name
├── location
├── start_date
├── end_date
├── format
├── time_control
├── rounds
└── participants
```

### Stellung

```text
Position
├── id
├── fen
├── source_game
├── move_number
├── side_to_move
└── commentary
```

Diese Modelle sollen nicht vorschnell direkt in den Superdesk-Kern geschrieben werden. Zuerst ist zu prüfen, welche bestehenden Content- und Extension-Mechanismen dafür sinnvoll wiederverwendet werden können.

---

## 15. PGN und FEN – erste Entwicklungsstufe

### FEN

FEN eignet sich als erster Prototyp, weil eine einzelne Stellung einfacher zu behandeln ist als eine vollständige Partie.

Minimalziel:

1. FEN erfassen;
2. Syntax prüfen;
3. FEN speichern;
4. Stellung als Brett darstellen;
5. FEN wieder ausgeben.

### PGN

Danach:

1. PGN importieren;
2. Header lesen;
3. Züge parsen;
4. Ergebnis erkennen;
5. Partie einem Artikel zuordnen;
6. Partie im Editor darstellen;
7. Partie im Publikationsfrontend nachspielbar ausgeben.

---

## 16. Engine-Analyse

Engine-Funktionalität ist ausdrücklich **nicht** Teil der ersten Ausbaustufe.

Später denkbar:

```text
PGN
 │
 ▼
Analyse-Queue
 │
 ▼
Stockfish / UCI
 │
 ▼
Varianten + Bewertungen
 │
 ▼
redaktionelle Auswahl
 │
 ▼
Artikel
```

Grundsatz:

> Engine-Ausgaben sind Rohmaterial und werden nicht ungeprüft als redaktionelle Inhalte veröffentlicht.

---

## 17. Risiken und offene Fragen

Zu prüfen sind insbesondere:

- lässt sich der aktuelle Fork reproduzierbar starten?
- welche Client-Komponenten sind technisch älter?
- wie stabil bleiben eigene Extensions gegenüber Upstream-Änderungen?
- wie sollen PGN/FEN mit bestehenden Content-Modellen verbunden werden?
- gehören Turnier- und Spielerdaten in Superdesk oder in ein eigenes Chessdesk-Modul?
- welches öffentliche Frontend wird eingesetzt?
- welche Datenquellen dürfen rechtlich eingebunden werden?
- wie wird Engine-Rechenlast von der Redaktion getrennt?
- wie werden Tests für Schachlogik und Datenmigration aufgebaut?
- wie wird ein späterer Upstream-Merge organisiert?

---

## 18. Versionen und Chronologie

### Historischer Superdesk-Fork

Im Account `wally2020` existiert ein älterer Superdesk-Fork mit Stand 2017.

Er wurde geprüft und bewusst nicht als Entwicklungsbasis verwendet.

### 08.09.2026 – Projektstart

- aktuelles Superdesk untersucht;
- Architektur bewertet;
- Entscheidung für Superdesk als Basis;
- neuer Fork `wally2020/chessdesk`;
- `develop` als Ausgangsbranch;
- Projektname Chessdesk;
- erste Projektdokumentation;
- noch keine schachspezifischen Eingriffe in den Kern.

---

## 19. Definition Chessdesk v0.1

Version **0.1** soll erstmals einen klar als Chessdesk erkennbaren und reproduzierbar startbaren Entwicklungsstand darstellen.

Ziele:

- [ ] Superdesk-Fork lokal unverändert starten;
- [ ] Grundfunktionen prüfen;
- [ ] Entwicklungsumgebung dokumentieren;
- [ ] Produktname Chessdesk einführen;
- [ ] Zeitzone auf `Europe/Vienna`;
- [ ] Chessdesk-Redaktionsbereiche definieren;
- [ ] Schachdatenmodell festlegen;
- [ ] FEN speichern;
- [ ] FEN als Brett darstellen;
- [ ] PGN importieren;
- [ ] PGN strukturiert speichern;
- [ ] Partie im Redaktionssystem anzeigen;
- [ ] automatisierte Tests für neue Schachlogik;
- [ ] Installations- und Entwicklungsdoku aktualisieren.

Nicht Teil von v0.1:

- vollständige Turnierverwaltung;
- Live-Partien;
- große Engine-Infrastruktur;
- fertige öffentliche Schachzeitung;
- umfassendes Spielerregister.

---

## 20. Erstes Arbeitspaket

```text
Superdesk unverändert starten
          │
          ▼
Entwicklungsumgebung verifizieren
          │
          ▼
Chessdesk-Branding
          │
          ▼
Schachdatenmodell definieren
          │
          ├──── FEN
          │
          └──── PGN
          │
          ▼
Brettdarstellung
          │
          ▼
automatisierte Tests
          │
          ▼
       Chessdesk v0.1
```

Der erste technische Meilenstein lautet:

> **Chessdesk kann innerhalb des Superdesk-Workflows eine Schachstellung und eine Schachpartie als strukturierten redaktionellen Inhalt erfassen, bearbeiten und darstellen.**

---

## 21. Konkreter Neustartpunkt

Wenn die Arbeit an Chessdesk in einem neuen Chat, mit Codex oder auf einem neuen Rechner fortgesetzt wird, zuerst diesen Ablauf verwenden:

1. Repository `wally2020/chessdesk` öffnen.
2. Branch `develop` verwenden.
3. `CHESSDESK.md` und diese Datei lesen.
4. Prüfen, ob der Fork gegenüber Superdesk-Upstream verändert wurde.
5. Lokale Entwicklungsumgebung starten.
6. Nur Fehler beheben, die den unveränderten Start verhindern.
7. Noch keine Engine- oder Live-Daten-Funktionen bauen.
8. Danach mit Branding und FEN-Prototyp beginnen.
9. Jede neue Chessdesk-Funktion mit Tests absichern.
10. Größere Architekturentscheidungen in der Dokumentation festhalten.

---

## 22. Arbeitsprinzipien

Für die weitere Entwicklung gelten folgende Regeln:

- zuerst reproduzierbar, dann komplex;
- zuerst Datenmodell, dann Oberfläche;
- zuerst FEN, dann PGN;
- zuerst PGN, dann Engine;
- Superdesk-Kern möglichst unangetastet lassen;
- eigene Funktionen klar als Chessdesk-Code trennen;
- jede größere Änderung dokumentieren;
- keine Funktion als vorhanden beschreiben, bevor sie tatsächlich implementiert ist;
- Upstream regelmäßig beobachten;
- Schachdaten nicht mit redaktionellen Artikeldaten unnötig vermischen.

---

## 23. GitHub-/Codex-Hinweis

Die bisher verwendete ChatGPT-/GitHub-Integration konnte das Repository lesen, aber Schreibzugriffe auf Repository-Inhalte wurden mit

```text
403 Resource not accessible by integration
```

abgewiesen.

Deshalb wurden Dokumentationsänderungen teilweise lokal vorbereitet und anschließend über das GitHub-Webinterface hochgeladen.

Für zukünftige Arbeiten bedeutet das:

- Repo-Zustand immer auf GitHub kontrollieren;
- lokale Codex-Commits sind erst nach erfolgreichem Push Teil des Repositories;
- bei einem 403 nicht davon ausgehen, dass der Commit bereits online ist.

---

## 24. Aktueller Projektstatus

**Stand: 08.09.2026**

### Vorhanden

- aktueller Superdesk-Fork;
- `develop` als Arbeitsbasis;
- allgemeine Redaktionsinfrastruktur;
- Docker-/Dev-Setup;
- Projektname Chessdesk;
- `CHESSDESK.md`;
- Neustartdokumentation;
- fachliches Zielbild;
- erste Roadmap.

### Offen

- lokaler Funktionstest;
- Branding;
- endgültiges Datenmodell;
- FEN-Prototyp;
- PGN-Prototyp;
- Brettkomponente;
- Tests;
- öffentliches Frontend;
- Upstream-Strategie im laufenden Betrieb.

---

## 25. Nächste konkrete Aufgabe

**Arbeitspaket 0: Ausgangsbasis verifizieren**

Ziel:

> Den aktuellen Fork unverändert lokal starten und dokumentieren, welche Dienste, Ports, Abhängigkeiten und Schritte tatsächlich funktionieren.

Erst wenn dieser Stand reproduzierbar läuft, beginnt die eigentliche Chessdesk-Entwicklung.

Danach folgt:

**Arbeitspaket 1: Branding + FEN-Grundlage**

mit:

- Chessdesk-Name in der Oberfläche;
- Europe/Vienna;
- erstes Schach-Content-Modell;
- FEN-Eingabe;
- FEN-Validierung;
- Brettdarstellung;
- Tests.

---

## 26. Ein-Satz-Definition

> **Chessdesk ist eine auf Superdesk basierende Open-Source-Redaktionsplattform für Schachnachrichten, Partien, Turniere, Analysen und Schachkultur.**
