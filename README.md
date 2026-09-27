# 🧪 Zahlenlabor — Zahlen zerlegen bis 100

Ein Lernspiel zur Zahlzerlegung und zum Teil-Ganzes-Verständnis: Eine Zahl
kommt in die Zahlenmaschine und wird in zwei Teile zerlegt — immer sichtbar
nach dem Prinzip **Ganzes = Teil 1 + Teil 2**.

**Zielgruppe:** Klasse 1 und 2, Schuleingangsphase, Förderunterricht
**Status:** Version 1.0 — veröffentlichungsbereit

## 🔬 Die drei Zahlenräume

- **bis 10** — Zielzahlen 2–10, Energiekugeln meist einzeln dargestellt
- **bis 20** — Zielzahlen 6–20, Energiekugeln ab 6 strukturiert (5er-Reihen,
  10er-Block + Rest)
- **bis 100** — Fokus auf Zahlbeziehungen statt einzelner Kugeln: Zehner
  zerlegen, Zehner-Einer-Beziehungen, fehlenden Teil ergänzen

Jeder Bereich nutzt eigene, mathematisch passende Aufgabenvarianten statt
einfach dieselbe Logik mit größeren Zahlen zu wiederholen.

## 🧬 Fünf Aufgabentypen

1. **Der fehlende Teil** — ein Teil ist gegeben, der andere fehlt (bis 20
   per Auswahl-Karten mit Kugeln, bis 100 per Zahlenfeld)
2. **Frei zerlegen** — alle Energiekugeln stehen bereit, das Kind verteilt
   sie frei auf zwei Behälter (nur bis 10/20); jede Verteilung mit
   Teil1+Teil2=Ganzes gilt als richtig, auch 0 als Teil
3. **Finde mehrere Zerlegungen** — mehrere unterschiedliche Zerlegungen
   derselben Zahl finden; vertauschte Paare (3|7 und 7|3) zählen als
   dieselbe Lösung
4. **Welche Zerlegung passt?** — Multiple-Choice mit mathematisch
   plausiblen, aber falschen Distraktoren
5. **Baue den anderen Teil** — ein Teil liegt bereits fest sichtbar vor,
   das Kind ergänzt die passende Menge im zweiten Behälter (nur bis 10/20)

Bei "bis 100" wird "Finde mehrere Zerlegungen" als Kartenauswahl aus
plausiblen Zehner-Zerlegungen umgesetzt, "Der fehlende Teil" und "Welche
Zerlegung passt?" wechseln zwischen Zehner-Einer-Erkennung (z. B.
`47 → 40 | ?`) und allgemeiner Zehner-Ergänzung (z. B. `80 → 30 | ?`).

Eine Runde besteht aus 8 richtig gelösten Experimenten, sichtbar als
Fortschrittsbalken und Energieanzeige. Bei falschen Antworten gibt es
keinen Punktabzug — die Aufgabe bleibt bestehen, ein freundlicher Hinweis
erscheint, das Kind darf erneut versuchen.

## 🛠️ Technik

Eine einzige, in sich geschlossene `index.html`-Datei — kein Build-Prozess,
keine Abhängigkeiten, kein Server nötig.

- Reines HTML, CSS und JavaScript (kein Framework)
- **Sprachausgabe** über die native `SpeechSynthesis`-API (Deutsch), über
  einen Lautsprecher-Button bei jeder Aufgabe abrufbar; funktioniert
  vollständig auch ohne verfügbare Sprachausgabe
- **Mathematisch garantiert korrekte Zerlegungen:** Bei allen Aufgaben wird
  zuerst Teil 1 und Teil 2 (bzw. bei "fehlender Teil" nur Teil 1) gewählt
  und das Ganze daraus berechnet, nie umgekehrt — ein falsches Ergebnis
  kann dadurch nicht entstehen. Distraktoren bei Multiple-Choice-Aufgaben
  verändern gezielt genau einen der beiden richtigen Werte und werden
  explizit gegen die Zielzahl geprüft, damit nie versehentlich eine zweite
  korrekte Option entsteht.
- **Automatische Größenanpassung:** Energiekugeln, das Zahlenfeld (bis 100)
  und die Zahlenmaschine passen ihre Größe live an den tatsächlich
  verfügbaren Platz an, statt sich auf feste Prozentwerte zu verlassen,
  die den tatsächlichen Platzbedarf umliegender Elemente (z. B. bei
  zweizeiligem Aufgabentext auf schmalen Bildschirmen) nicht kennen.
- Läuft vollständig offline, keine externen Ressourcen
- Responsiv für Smartboard, Desktop, Tablet und Smartphone
- Keine personenbezogenen Daten, keine Cookies, kein Tracking

## 📁 Projektstruktur

```
zahlenlabor-projekt/
├── index.html      ← das komplette Spiel
├── README.md
└── .gitignore
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

## 🔄 Design-Überarbeitung nach Nutzer-Feedback

Die ursprüngliche Zahlenmaschine (Trichter mit Zahnrädern) wurde nach direktem
Feedback grundlegend überarbeitet:

- **Automat statt Trichter:** Die Maschine ist jetzt ein erkennbarer
  Kaugummi-/Kirmesautomat mit Glaskuppel oben und rotem Gehäuse mit
  Ausgabe-Mechanismus unten — nach Vorbild eines klassischen
  Süßigkeitenautomaten.
- **Kugeln sichtbar "in der Maschine":** Bei "Frei zerlegen", "Finde
  mehrere Zerlegungen" und "Baue den anderen Teil" liegen die zu
  verteilenden Energiekugeln jetzt sichtbar in der Glaskuppel des
  Automaten (nicht mehr vorab in einem Behälter). Antippen einer Tüte
  holt eine Kugel aus der Kuppel dorthin, Antippen einer Kugel in der
  Tüte schickt sie zurück — der Fluss "oben rein, unten links/rechts
  raus" ist dadurch sofort verständlich.
- **Tüten statt Kästen:** Die beiden Behälter sind jetzt als Tüten
  geformt (schmaler oben, breiter unten) statt einfacher Rechtecke.
- **Keine drehenden Zahnräder mehr:** Diese wurden als verwirrend
  empfunden und durch einen einfachen Leucht-Puls bei richtiger Lösung
  ersetzt.
- **Klarerer Mehrfach-Zerlegungs-Ablauf:** Bei "Finde mehrere
  Zerlegungen" wird nach jedem gefundenen Paar jetzt explizit erklärt
  und visuell gezeigt, dass die Kugeln in die Maschine zurückkehren und
  erneut verteilt werden müssen.

## ✅ Qualitätssicherung

Vor der Freigabe automatisiert geprüft:

- **Mehrere kritische Fehler gefunden und behoben:**
  1. Bei der Multiple-Choice-Variante von "Zehner + Einer" (bis 100)
     konnte die automatische Distraktor-Generierung durch eine fehlerhafte
     Formel (`wrongB = ganzes − cand`) versehentlich eine zweite
     rechnerisch korrekte Option erzeugen. Die Distraktor-Logik wurde
     grundlegend neu geschrieben: sie verändert gezielt nur einen der
     beiden richtigen Werte und prüft explizit, dass die neue Summe nicht
     der Zielzahl entspricht.
  2. Bei "Finde mehrere Zerlegungen" (bis 100) konnten zwei angezeigte
     Karten versehentlich dieselbe Zerlegung darstellen (z. B. `30 | 40`
     und `40 | 30` als zwei separate Karten) — die Aufgabe wurde dadurch
     unlösbar, sobald ein Kind beide anklickte. Die Kartenliste wird jetzt
     vor der Anzeige nach normalisiertem Zerlegungs-Schlüssel dedupliziert.
  3. Bei "Finde mehrere Zerlegungen" wurde ein DOM-Element per ID gesucht,
     bevor es tatsächlich im Dokument eingehängt war — behoben durch
     früheres Anhängen an das Dokument.
  4. Das Zahlenfeld (bis 100) konnte auf schmalen/kurzen Bildschirmen mehr
     Höhe beanspruchen als verfügbar war, wodurch die unterste Reihe
     (0/Löschen/OK) unsichtbar wurde. Behoben durch dynamische Anpassung
     von Schriftgröße und Abständen anhand der tatsächlich verfügbaren
     Position statt fester vh-Werte.
- **Redundante Kugel-Darstellung bereinigt:** Bei "Frei zerlegen" und
  "Finde mehrere Zerlegungen" wurden Kugeln anfangs doppelt gezeigt (einmal
  im Behälter, einmal als separate antippbare Reihe darunter) — jetzt sind
  die Kugeln im Behälter selbst direkt antippbar, keine Verdopplung mehr.
- 90 automatisiert gelöste Aufgaben über alle drei Bereiche, 0 Mathefehler
- Volle Runden (8/8) in allen drei Bereichen mehrfach wiederholt getestet
- Sprachausgabe verursacht keinen Fehler, wenn `SpeechSynthesis` im
  Browser nicht verfügbar ist
- Doppelklick/Doppeltipp vergibt kein doppeltes Fortschritts-Inkrement
- 0 als Teil einer freien Zerlegung wird korrekt akzeptiert
- Alle 6 vorgeschriebenen Bildschirmgrößen (375×667 bis 1920×1080)
  geprüft: kein horizontales Scrollen, keine abgeschnittenen Inhalte,
  Zahlenfeld und Energiekugeln vollständig sichtbar

## 📄 Lizenz

© Förderfreude Games. Alle Rechte vorbehalten.
