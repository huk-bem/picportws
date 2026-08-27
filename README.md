# Rahmwerk

Ein browserbasiertes Werkzeug, um Fotos mit einem individuell konfigurierbaren
Bilderrahmen zu versehen, als Mockup in einem Raumfoto zu platzieren und mit
einem Wasserzeichen zu versehen. Läuft vollständig client-seitig (HTML5
Canvas) — keine Uploads an einen Server, keine Abhängigkeiten, kein Build-Schritt.

**Live-Version:** https://claude.ai/code/artifact/105e0107-0a3c-4ab8-9a76-8b479910bdb1
(privat, über den Teilen-Button der Seite freigebbar) — oder lokal:
`index.html` im Browser öffnen.

## Funktionen

### 1. Rahmen
- **Material**: Eiche, Nussbaum, Metall gebürstet, Metall schwarz, Messing,
  Matt (farbig), Hochglanz (farbig) — als kleine Vorschau-Kacheln wählbar.
- **Farbe**: frei wählbar für die Finish-Materialien Matt/Hochglanz.
- **Rahmenbreite**: Regler für die Dicke des Rahmenprofils.
- **Passepartout (Rand nach innen)**: Regler für die Breite des Passepartouts
  zwischen Foto und Rahmen, plus vier Passepartout-Farben.
- **Außenabstand (Rand nach außen)**: Regler für den Freiraum um den Rahmen
  herum (z. B. für Wandmontage-Wirkung).
- **Schlagschatten**: an/aus für den freistehenden „Galerie“-Look.

### 2. Foto im Rahmen platzieren
- **Öffnungsformat**: dem Foto folgen oder ein festes Format wählen
  (1:1, 4:5, 5:4, 2:3, 3:2, 9:16, 16:9) — dadurch werden Zuschnitt/Skalierung
  wirklich sichtbar.
- **Einpassung**: Einpassen (ganz sichtbar), Ausfüllen (füllt die Öffnung,
  beschneidet), Verzerren (auf die Öffnung strecken).
- **Zoom** sowie **Position horizontal/vertikal** per Regler oder direkt per
  Ziehen auf der Vorschau.

### 3. Wand / Raumszene
- Framed Picture auf einem Raumfoto platzieren: **Wohnzimmer**, **Büro**,
  **Lobby** (prozedural gezeichnete Illustrationen) oder ein **eigenes
  Raumfoto** hochladen.
- **Platzierung des Rahmens**: 3×3-Positionsraster plus Feinjustierung
  (horizontal/vertikal) und Größenregler relativ zur Wandbreite.
- Weicher Schlagschatten unter dem Bild für realistische Wirkung.

### 4. Wasserzeichen
- **Typ**: Text oder Bilddatei (Logo).
- **Ebene**: hinter dem Foto (scheint z. B. bei reduzierter Foto-Deckkraft
  durch) oder vor dem Foto (klassischer Copyright-Stempel).
- **Deckkraft** prozentual regelbar; bei „hinter dem Foto“ zusätzlich
  „Sichtbarkeit durchs Foto“ (macht das Foto teiltransparent).
- Drehung, Kachel-/Wiederholungsmuster oder feste Position (3×3-Raster).

### 5. Export
- PNG (verlustfrei) oder JPEG (mit Qualitätsregler).
- Export entweder nur des gerahmten Bilds oder der kompletten Wandszene.
- Speichert über die Browser-Download-Funktion; Fallback per Rechtsklick auf
  die Vorschau („Grafik speichern unter …“), falls der automatische Dialog
  nicht verfügbar ist.

## Technik

- Eine einzelne selbstständige `index.html` — kein Build, keine Abhängigkeiten
  außer Google Fonts (Fraunces, IBM Plex Sans, IBM Plex Mono).
- Rendering komplett über die Canvas-2D-API; Rahmen-Materialien und
  Raum-Hintergründe werden prozedural gezeichnet (keine externen Bildassets
  nötig).
- Unterstützt alle gängigen Bildformate, die der Browser über `<img>` lädt
  (JPG, PNG, WebP, GIF, SVG, BMP, AVIF …).
- Einstellungen (Rahmen, Wand, Wasserzeichen — ohne Fotoinhalte) werden lokal
  im Browser gespeichert (`localStorage`) und beim nächsten Besuch
  wiederhergestellt.
- Hell-/Dunkelmodus werden automatisch anhand der Systemeinstellung
  unterstützt.

## Lokal starten

Kein Server nötig — einfach `index.html` im Browser öffnen:

```bash
open index.html   # macOS
# oder: xdg-open index.html (Linux) / doppelklicken
```
