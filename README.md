# Spielleiter-Werkstatt

Ein browserbasiertes Werkzeug für Spielleiterinnen und Spielleiter von Pen-&-Paper-Rollenspielen – kompatibel mit der 5. Edition (Regelfassung 2024). Datenbanken, Initiative-Tracker, Würfelroller und eine SRD-Bibliothek, alles in einer einzigen Datei, offline lauffähig und als App installierbar.

**➡️ Live-Version:** https://true5h4d0w.github.io/Spielleiter-Werkstatt-/

---

## Funktionen

- **Sieben vernetzte Datenbanken:** Spielercharaktere, NSC, Orte, Monster, Gegenstände, Zauber und Quests
- **Verknüpfungen:** beliebige Beziehungen zwischen Einträgen (z. B. „NSC lebt in Ort", „Quest spielt an Ort") mit Sprung zum verknüpften Eintrag
- **Initiative-Tracker:** Kampfverwaltung mit Rundenzähler, Trefferpunkten, Zuständen und automatischem Würfeln; zieht Teilnehmer direkt aus den eigenen Datenbanken oder der SRD-Bibliothek
- **Würfelroller:** W20-Proben mit Vorteil/Nachteil, ein Würfeltablett (W4–W100) und eigene Formeln wie `2d6+3`, inklusive Wurf-Verlauf
- **SRD-Bibliothek:** kuratierter Startbestand an Monstern, Gegenständen und Zaubern, angelehnt an das System Reference Document 5.2, mit „In Kampagne kopieren"
- **Mehrere Kampagnen** parallel verwaltbar
- **Sichern & Laden:** vollständige Datensicherung als JSON, zum Umzug zwischen Geräten oder als Backup
- **Offline-fähig (PWA):** lässt sich auf dem Startbildschirm installieren und funktioniert ohne Internetverbindung

## Installation als App

1. Die Live-Adresse im Browser öffnen (Chrome, Brave, Safari …)
2. **Android:** Menü → „Zum Startbildschirm hinzufügen" bzw. „App installieren"
3. **iPhone:** Teilen-Symbol → „Zum Home-Bildschirm"

Danach startet die App im Vollbild mit eigenem Icon und läuft offline.

## Selbst hosten

Es wird kein Server und kein Backend benötigt – nur statisches Hosting über HTTPS. Diese Dateien gehören dafür in **denselben Ordner**:

```
index.html              – die App
manifest.webmanifest    – PWA-Manifest
sw.js                   – Service Worker (Offline-Cache)
icon-192.png            – App-Icon
icon-512.png            – App-Icon
```

Über **GitHub Pages** (Settings → Pages → Deploy from branch → `main` / `root`) ist alles in wenigen Minuten online. Zum lokalen Ausprobieren genügt es, `index.html` direkt im Browser zu öffnen (die Installierbarkeit als PWA funktioniert dann allerdings nicht, da dafür HTTPS nötig ist).

## Hinweise zu den Daten

Alle Eingaben werden **lokal im Browser** gespeichert (`localStorage`) – sie sind an das jeweilige Gerät und den jeweiligen Browser gebunden und verlassen den Rechner nicht. Vor einem Gerätewechsel oder größeren Änderungen lohnt sich ein Klick auf **↧ Sichern**; die erzeugte JSON-Datei lässt sich anderswo über **↥ Laden** wieder einspielen.

> ⚠️ „Website-Daten löschen" im Browser entfernt auch die gespeicherten Kampagnen. Vorher sichern!

## Technik

Reines **HTML, CSS und JavaScript** ohne Frameworks oder Abhängigkeiten. Persistenz über `localStorage`, Offline-Fähigkeit über einen Service Worker und ein Web App Manifest. Eine einzelne HTML-Datei trägt die komplette Anwendung.

### Eigene Änderungen / Updates

Wird `index.html` geändert, muss in `sw.js` die Cache-Version hochgezählt werden (z. B. `const CACHE = "slw-v3";` → `"slw-v4";`). Sonst liefert der Service Worker weiterhin die zwischengespeicherte alte Fassung aus. Große Dateien am besten über **Add file → Upload files** ersetzen statt per Copy-&-Paste im Editor.

## Lizenz & Rechtliches

Die Inhalte der SRD-Bibliothek sind angelehnt an das **System Reference Document 5.2** von Wizards of the Coast LLC und stehen unter der [Creative Commons Attribution 4.0 International License (CC BY 4.0)](https://creativecommons.org/licenses/by/4.0/). Die Werte sind eine kuratierte Näherung; für offizielle Angaben bitte das SRD 5.2 heranziehen.

„Dungeons & Dragons" und „D&D" sind Marken von Wizards of the Coast. Dieses Projekt ist nicht mit Wizards of the Coast verbunden und nutzt ausschließlich frei lizenzierte SRD-Inhalte.

Der eigene Quellcode dieses Projekts steht unter der MIT-Lizenz (oder einer Lizenz deiner Wahl – ggf. eine `LICENSE`-Datei ergänzen).
