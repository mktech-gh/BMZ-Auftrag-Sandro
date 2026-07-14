# Baumaschinen-Werkstatt – Annahme & Rapportierung

Eine offline-fähige Tablet-App, 1:1 nachgebaut nach dem offiziellen Formular "2.1 Reparaturannahme / Reparaturauftrag" (Stand 18.04.2025):

1. **Reparaturannahme** – Kunde, Maschine/Fahrzeug (inkl. Inventar-Nr., Chassis-Nr., Betriebsstunden etc.), auszuführende Arbeiten, Bemerkungen
2. **Reparaturauftrag** – Checkliste "Ausgeführte Arbeiten" (alle 28 Standardpunkte aus dem Formular, plus 4 freie Zusatzpunkte), Feld "Weitere Arbeiten", Zeiterfassung (Datum, Stunden, Monteur, Km, AHK) und Materialliste mit automatischer Summenberechnung sowie einer Auswahlliste gängiger Teile (Filter, Öle, Verschleissteile)

**Aufträge Mitarbeitern zuteilen:** In der Reparaturannahme gibt es das Feld "Zugewiesen an" mit einer selbst pflegbaren Mitarbeiterliste (in der Übersicht über "Mitarbeiter verwalten"). In der Übersicht lässt sich zusätzlich nach Mitarbeiter filtern.

Läuft komplett offline, auch auf der Baustelle ohne Internet. Die Daten liegen lokal auf dem jeweiligen Gerät.

**Hinweis zum Feld "AHK":** Ich habe die Spalte 1:1 aus eurem Formular übernommen, kenne aber die genaue Abkürzung nicht mit Sicherheit (vermutlich Anhängerkupplung). Aktuell ist es ein einfaches Textfeld — sag mir, falls es z.B. eine Checkbox oder ein Zahlenfeld sein soll, dann passe ich es an.

## Enthaltene Dateien
- `index.html` – die App
- `manifest.json`, `service-worker.js`, Icons – fürs Homescreen-Symbol und Offline-Betrieb

Alle Dateien im selben Ordner lassen.

## Installation auf dem Tablet
Damit "Zum Homescreen hinzufügen" ein echtes App-Icon erzeugt und Offline-Betrieb funktioniert, müssen die Dateien einmal über **https** erreichbar sein:

- **GitHub Pages** (kostenlos): Repository erstellen, Dateien hochladen, unter Settings → Pages aktivieren
- **Netlify Drop** (kostenlos, ohne Konto): Ordner auf [app.netlify.com/drop](https://app.netlify.com/drop) ziehen
- Oder eigener Webserver / NAS im Firmennetzwerk

Danach auf dem Tablet:
- **iPad (Safari):** Teilen-Symbol → "Zum Home-Bildschirm"
- **Android (Chrome):** Menü → "App installieren" (oder blauer Installieren-Button erscheint automatisch)

## Wichtig: Daten sind lokal pro Gerät
Jedes Tablet hat seine eigenen Daten. Für den Austausch zwischen Werkstatt-Tablet und Baustellen-Tablets:
- In der App auf **"Backup exportieren"** tippen → JSON-Datei
- Per E-Mail/AirDrop aufs andere Gerät bringen
- Dort **"Backup importieren"** tippen

Der Import ist so gebaut, dass er bestehende Aufträge nicht überschreibt, sondern nur **neue Rapport-Einträge ergänzt** – ideal, wenn z.B. der Monteur auf der Baustelle rapportiert und die Werkstatt am Feierabend importiert.

Für automatischen Echtzeit-Abgleich zwischen mehreren Geräten (ohne manuellen Export/Import) bräuchte es einen kleinen gemeinsamen Server im Hintergrund – bei Bedarf lässt sich das später ergänzen.
