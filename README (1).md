# Merkwürdig

Ein persönlicher Alles-in-einem-Planer als einzelne HTML-Datei: Notizen, Aufgaben, Kalender, Listen und Alltagsmodule an einem Ort. Gedacht als Ersatz für getrennte Notiz- und Aufgaben-Apps. Optimiert für das Handy, funktioniert auch am Desktop.

Keine Build-Schritte, keine Abhängigkeiten, kein Tracking. Die ganze App steckt in `index.html` (HTML, CSS und Vanilla-JavaScript).

## Funktionen

**Planen**
- **Heute:** Tagesübersicht mit Terminen, Aufgaben, Überfälligem und allgemeinen Aufgaben. Blöcke sind einklappbar, auswählbar und sortierbar.
- **Notizen:** Text, Tags, Anpinnen, Archiv, Suche.
- **Aufgaben:** Fälligkeit oder „allgemein“ ohne Datum, Priorität, Unteraufgaben, Wiederholungen (täglich bis jährlich, auch „ab Erledigung“), Erinnerungen.
- **Kalender:** Monat, Woche (mit Uhrzeiten) und Agenda. Alles mit Datum erscheint automatisch im Kalender.
- **Kategorien:** Frei anlegbar (z. B. Uni, Arbeit, Privat) und jederzeit ausblendbar. Ausgeblendete Kategorien verschwinden überall, die Einträge bleiben erhalten.
- **Schnellerfassung:** Eine Zeile genügt, z. B. „Zahnarzt morgen 14:30“ oder „Müll rausbringen jeden Dienstag“. Datum, Uhrzeit, Wiederholung, `#kategorie` und `#tags` werden erkannt.

**Alltag (einzeln ein- und ausschaltbar)**
- **Listen:** Einkauf, Packlisten, Haushalt. Fertige Vorlagen, die frei bearbeitbar sind.
- **Urlaub:** Packliste aus Vorlagen, Programm, Buchungen, Kosten gegen Budget, Eintrag im Kalender.
- **Gewohnheiten:** 7-Tage-Raster, Serien, eigene Wochentage.
- **Dienstplan:** Diensttypen, Eintragen per Antippen oder Muster, Stundenauswertung, Import aus `.ics`, Text oder Foto.
- **Geburtstage**, **Budget**, **Dokumente und Fristen**, **Tagebuch** mit Stimmung.
- **Fokus-Timer**, **Wochenrückblick** mit Wochenzielen.

**Sonstiges**
- Papierkorb (30 Tage), Hell/Dunkel/Automatisch, Kalender-Export (`.ics`, inkl. Erinnerungen), JSON-Sicherung.

## Nutzung

### Lokal
`index.html` im Browser öffnen. Die Daten liegen im `localStorage` des Browsers. Sicherung und Wiederherstellung findest du unter Einstellungen, „Sicherung anzeigen“.

### Als Claude-Artifact (voller Funktionsumfang)
Die App ist für die Artifact-Umgebung von Claude gebaut. Dort stehen zusätzlich bereit:

| Funktion | Voraussetzung |
|---|---|
| Synchronisierung zwischen Geräten | Claude-Konto (Artifact-Datenspeicher) |
| Google-Kalender-Abgleich in beide Richtungen | Konnektor „Google Calendar“ |
| Sicherung in Google Drive | Konnektor „Google Drive“ |
| Smart-Eintrag (Text oder Foto zu Einträgen), Foto-Import von Dienstplänen | Claude-Funktion `sample` |
| Diktat | Chromium-Browser oder Claude-Desktop-App (nicht in der iPhone-App) |
| Kalenderdatei speichern | `downloads` |

Als lokale Datei laufen nur die Grundfunktionen. Alles andere blendet sich dann automatisch aus.

## Datenschutz

- Die Datei enthält keine persönlichen Daten und keine Zugangsdaten.
- Google-Daten werden nur nach deiner Freigabe geladen und liegen im Datenspeicher des jeweiligen Nutzers. Wer die App nur öffnet, sieht keine fremden Termine und muss selbst verbinden.
- Der Kalender-Abgleich läuft nur, solange die App geöffnet ist.

## Google-Kalender-Abgleich

Einstellungen, Daten, „Google Kalender“:

1. Mit Google Kalender verbinden und Kalender laden.
2. Pro Kalender wählen: **Aus**, **Nur lesen** oder **Lesen und schreiben**, dazu eine Kategorie.
3. Optional einen Kalender wählen, an den neue Termine aus der App gesendet werden.
4. Optional „Löschen auch in Google“ aktivieren (standardmäßig aus).

Bekannte Grenzen: Änderungen an Wiederholungsregeln werden nicht zurückgeschrieben. In „Nur lesen“-Kalendern überschreibt Google lokale Änderungen. Das Zurückschreiben bitte zuerst mit einem Test-Kalender ausprobieren.

## Dienstplan-Import (z. B. aus Supershift)

Es gibt drei Wege:
1. **Kalenderdatei (`.ics`)** aus dem Kalender-Export der Dienstplan-App.
2. **Text** einfügen, eine Zeile pro Tag, z. B. `24.11. Früh 06:00-14:00`.
3. **Foto oder Screenshot** des Plans, Claude liest die Dienste aus (bitte gegenprüfen).
4. **Google-Kalender**, in den der Plan synchronisiert wird: Titel auswählen, die echte Dienste sind.

## Technik

- Eine Datei, Vanilla-JS, Rendern über Template-Strings und Event-Delegation (`data-action`).
- Zustand in einem Objekt `S`, Persistenz in `localStorage` und optional im Artifact-Datenspeicher.
- Schriften: Bricolage Grotesque und Figtree, mit Systemschrift als Rückfall.
- Der Code ist in Teile gegliedert (Kern, Aufgaben, Dienstplan, Urlaub, Alltag, Werkzeuge, Listen, Google Kalender).

## Lizenz

Noch nicht festgelegt. Ergänze hier eine Lizenz deiner Wahl (z. B. MIT), bevor du das Repository öffentlich machst.
