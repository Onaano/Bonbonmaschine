# 🍬 Bonbonmaschine — Zahlen zerlegen bis 100

Ein Lernspiel zur Zahlzerlegung und zum Teil-Ganzes-Verständnis: Eine Zahl
kommt in die Bonbonmaschine (im Stil eines Kaugummiautomaten) und wird dort
in zwei Teile zerlegt, die in zwei Tüten wandern — immer sichtbar nach dem
Prinzip **Ganzes = Teil 1 + Teil 2**.

**Zielgruppe:** Klasse 1 und 2, Schuleingangsphase, Förderunterricht
**Status:** Version 1.0 — veröffentlichungsbereit

## 🍭 Die drei Zahlenräume

- **bis 10** — Zielzahlen 2–10, Bonbons meist einzeln dargestellt
- **bis 20** — Zielzahlen 6–20, Bonbons ab 6 strukturiert (5er-Reihen,
  10er-Block + Rest)
- **bis 100** — Fokus auf Zahlbeziehungen statt einzelner Bonbons: Zehner
  zerlegen, Zehner-Einer-Beziehungen, fehlenden Teil ergänzen

Jeder Bereich nutzt eigene, mathematisch passende Aufgabenvarianten statt
einfach dieselbe Logik mit größeren Zahlen zu wiederholen.

## 🧩 Fünf Aufgabentypen

1. **Der fehlende Teil** — eine kurze Gleichung mit Lücke (z. B.
   „14 = 8 + ?"), Antwort per Auswahl-Karten (bis 10/20) oder Zahlenfeld
   (bis 100)
2. **Frei zerlegen** — alle Bonbons liegen sichtbar in der Glaskuppel der
   Maschine, das Kind tippt die beiden Tüten an, um sie zu befüllen; jede
   Verteilung mit Teil1+Teil2=Ganzes gilt als richtig, auch 0 als Teil.
   Ein „Zurücksetzen"-Button holt bei Bedarf alle Bonbons auf einmal
   zurück in die Maschine.
3. **Baue den anderen Teil** — eine Tüte ist schon fertig befüllt, das
   Kind tippt Bonbons aus der Kuppel in die zweite Tüte, bis die Zielzahl
   erreicht ist (nur bis 10/20)
4. **Welche Zerlegung passt?** — Multiple-Choice mit mathematisch
   plausiblen, aber falschen Distraktoren
5. **Finde mehrere Zerlegungen** — mehrere unterschiedliche Zerlegungen
   derselben Zahl finden; vertauschte Paare (3|7 und 7|3) zählen als
   dieselbe Lösung. Nach jedem gefundenen Paar kehren die Bonbons sichtbar
   in die Maschine zurück, bevor die nächste Zerlegung gesucht wird.

Bei „bis 100" wird „Finde mehrere Zerlegungen" als Kartenauswahl aus
plausiblen Zehner-Zerlegungen umgesetzt, „Der fehlende Teil" und „Welche
Zerlegung passt?" wechseln zwischen Zehner-Einer-Erkennung (z. B.
`47 = 40 + ?`) und allgemeiner Zehner-Ergänzung (z. B. `80 = 30 + ?`).

Eine Runde besteht aus 8 richtig gelösten Aufgaben, sichtbar als
Fortschrittsbalken oben. Bei falschen Antworten gibt es keinen Punktabzug
— die Aufgabe bleibt bestehen, ein freundlicher Hinweis erscheint, das
Kind darf erneut versuchen.

Texte sind bewusst sehr kurz gehalten (z. B. „6 + ? = 10" statt eines
ganzen Satzes), da viele Kinder in Klasse 1 noch nicht gut lesen können.
Ein Lautsprecher-Button liest jede Aufgabe auf Wunsch vor.

## 🛠️ Technik

Eine einzige, in sich geschlossene `index.html`-Datei — kein Build-Prozess,
keine Abhängigkeiten, kein Server nötig.

- Reines HTML, CSS und JavaScript (kein Framework)
- **Sprachausgabe** über die native `SpeechSynthesis`-API (Deutsch), rein
  manuell über den Lautsprecher-Button abrufbar (kein Auto-Vorlesen, damit
  es im Klassenraum nicht zusätzlichen Lärm erzeugt); funktioniert
  vollständig auch ohne verfügbare Sprachausgabe
- **Mathematisch garantiert korrekte Zerlegungen:** Bei allen Aufgaben wird
  zuerst Teil 1 und Teil 2 (bzw. bei „fehlender Teil" nur Teil 1) gewählt
  und das Ganze daraus berechnet, nie umgekehrt — ein falsches Ergebnis
  kann dadurch nicht entstehen. Distraktoren bei Multiple-Choice-Aufgaben
  verändern gezielt genau einen der beiden richtigen Werte und werden
  explizit gegen die Zielzahl geprüft, damit nie versehentlich eine zweite
  korrekte Option entsteht.
- **Automatische Größenanpassung:** Bonbons, das Zahlenfeld (bis 100)
  und die Bonbonmaschine passen ihre Größe live an den tatsächlich
  verfügbaren Platz an, statt sich auf feste Prozentwerte zu verlassen,
  die den tatsächlichen Platzbedarf umliegender Elemente nicht kennen.
- **Sicherheitsnetz gegen Hänger:** Sollte das Spiel durch einen
  unerwarteten Fehler in einer Erfolgs-Animation stecken bleiben, gibt es
  sich nach wenigen Sekunden automatisch wieder frei; der
  „Zurücksetzen"-Button funktioniert zudem immer, unabhängig vom
  internen Zustand.
- Läuft vollständig offline, keine externen Ressourcen
- Responsiv für Smartboard, Desktop, Tablet und Smartphone
- Keine personenbezogenen Daten, keine Cookies, kein Tracking

## 📁 Projektstruktur

```
zahlenlabor-projekt/
├── index.html      ← das komplette Spiel
├── README.md
├── .gitignore
└── arbeitsblaetter/
    ├── teilnehmeruebersicht.html + .pdf
    ├── arbeitsblatt-bis-10.html + .pdf
    ├── arbeitsblatt-bis-20.html + .pdf
    └── arbeitsblatt-bis-100.html + .pdf
```

## ▶️ Lokal ausprobieren

Einfach `index.html` im Browser öffnen — kein Server, keine Installation
nötig.

## 🌐 Veröffentlichung

### GitHub

1. Neues Repository auf [github.com](https://github.com) anlegen.
2. `index.html`, `README.md` und `.gitignore` hochladen.

### Netlify / Vercel

Reine statische HTML/CSS/JS-Seite ohne Build-Schritt — beide Plattformen
erkennen das automatisch, keine Konfiguration nötig.

**Netlify (per Drag & Drop, ganz ohne GitHub):**
1. Auf [app.netlify.com](https://app.netlify.com) einloggen.
2. Den Ordner mit der `index.html` direkt in den Browser ziehen
   („Deploy manually").
3. Netlify vergibt sofort einen Link.

**Vercel (über GitHub):**
1. Mit GitHub bei [vercel.com](https://vercel.com) einloggen.
2. „Add New…" → „Project" → Repository importieren → „Deploy".

## 📝 Arbeitsblätter

Passend zum Spiel gibt es eine Teilnehmerübersicht (A4 quer, 30 Kinder ×
10 Runden zum Abhaken) sowie je ein Arbeitsblatt für „bis 10", „bis 20"
und „bis 100" im selben Bonbonmaschine-Design — mit denselben
Aufgabentypen wie im digitalen Spiel (fehlender Teil, freie Verteilung
in Tüten zum Ausmalen, Multiple Choice, Zehner-Zerlegung bei „bis 100").
Alle Aufgaben sind automatisiert auf mathematische Korrektheit geprüft.

## 🔄 Entwicklungsverlauf (Auszug)

Das Spiel hieß ursprünglich „Zahlenlabor" mit einer abstrakten
Zahlenmaschine (Trichter, drehende Zahnräder, „Energiekugeln" in
„Behältern"). Nach Nutzer-Feedback grundlegend überarbeitet zur
**Bonbonmaschine**:

- **Automat statt Trichter:** erkennbarer Kaugummiautomat mit Glaskuppel
  und rotem Gehäuse statt abstrakter Technik-Optik
- **Bonbons statt Energiekugeln, Tüten statt Behälter** — durchgängig
  umbenannt, passend zum kindgerechten Thema
- **Bonbons sichtbar „in der Maschine":** liegen in der Kuppel, statt
  vorab schon in einem Behälter zu stecken — der Fluss „oben rein, unten
  links/rechts raus" ist dadurch sofort verständlich
- **Keine drehenden Zahnräder mehr** — durch einen einfachen Leucht-Puls
  bei richtiger Lösung ersetzt
- **Texte radikal gekürzt** und automatisches Sprach-Vorlesen zunächst
  ergänzt, dann auf Nutzer-Wunsch wieder auf rein manuell umgestellt
  (Klassenraum-Lärm)
- **Start-Button-Falle behoben:** „bis 10" ist jetzt vorausgewählt, der
  Start-Button ist von Anfang an aktiv

## ✅ Qualitätssicherung

- Mehrere kritische Fehler im Verlauf gefunden und behoben, u. a.:
  fehlerhafte Distraktor-Formel bei „Zehner + Einer" (bis 100) konnte
  versehentlich eine zweite korrekte Option erzeugen; doppelte
  Kartenpaare bei „Finde mehrere Zerlegungen" (bis 100) machten die
  Aufgabe unlösbar; eine CSS-Regel (`pointer-events:none`) blockierte
  zeitweise sämtliche Klicks auf Bonbons in der Kuppel
- 90+ automatisiert gelöste Aufgaben über alle drei Bereiche, 0 Mathefehler
- Volle Runden (8/8) in allen drei Bereichen mehrfach wiederholt getestet
- Sprachausgabe verursacht keinen Fehler, wenn `SpeechSynthesis` im
  Browser nicht verfügbar ist
- Doppelklick/Doppeltipp vergibt kein doppeltes Fortschritts-Inkrement
- 0 als Teil einer freien Zerlegung wird korrekt akzeptiert
- Alle 6 vorgeschriebenen Bildschirmgrößen (375×667 bis 1920×1080)
  geprüft: kein horizontales Scrollen, keine abgeschnittenen Inhalte

## 📄 Lizenz

© Förderfreude Games. Alle Rechte vorbehalten.
