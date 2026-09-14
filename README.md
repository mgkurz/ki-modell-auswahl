# ki-modell-auswahl

Interaktive Übung zur Auswahl des passenden KI-Sprachmodells für Unterrichtssettings in **AIS.chat**.

Die Übung läuft als statische Single-Page-Anwendung direkt im Browser, ohne Backend, ohne Tracking. Lehrkräfte wählen ein Unterrichtsszenario aus, woraufhin die in AIS.chat verfügbaren Modelle markiert werden, die für dieses Szenario geeignet sind.

**Live-Version:** <https://mgkurz.github.io/ki-modell-auswahl/>

## Inhalt

- Fünf Unterrichtsszenarien: Dialog und kreatives Schreiben, schnelle und sparsame Antworten, Sprachen und Übersetzen, Mathematik und Logik, Allround-Einsatz.
- Acht in AIS.chat verfügbare Modelle (Stand Mitte September 2026): GPT-5.6-luna, Claude Sonnet 4.6, Gemini 3.1 Lite, GPT-5.5, GPT-5 nano, Mistral Nemo Instruct, Llama-3.3-70B, Llama-3.1-8B. Frühere Stände stehen in [MODELLHISTORIE.md](MODELLHISTORIE.md).

## Technik und Gestaltung

Eine einzige HTML-Datei, kein Build-Schritt, kein Backend, keine externen Abhängigkeiten zur Laufzeit. Gestaltet nach dem AIS.chat-Styleguide. Schrift (Barlow), Logo, Hintergrundmuster und Symbole sind als Base64 beziehungsweise Inline-SVG eingebettet, es wird also beim Aufruf kein fremder Server kontaktiert.

## Einsatzkontext

Die Übung wurde für den Selbstlernkurs „Fit für AIS.chat" der Hessischen Lehrkräfteakademie erstellt (SchulMoodle Hessen). Sie ist als Embed oder als Link nutzbar. Sie kann ohne Anpassung in anderen Bundesländern eingesetzt werden, sofern dort dieselben Modelle über AIS.chat angeboten werden.

## Hinweise zur Pflege

### Wann geprüft wird

Die Modellliste in AIS.chat ändert sich. Sie wird deshalb alle zwei Monate geprüft
(Erinnerung liegt in Todoist). Ablauf: `app.ais-chat.schule` öffnen, das Aufklappmenü
„Aktuelles Sprachmodell" öffnen, zwei Screenshots mit unterschiedlich aktivem Modell
machen (die Beschreibung des aktiven Modells zeigt AIS.chat nicht an) und mit dem
obersten Abschnitt in [MODELLHISTORIE.md](MODELLHISTORIE.md) vergleichen. Ohne
Änderung ist der Termin damit erledigt.

### Was bei einer Änderung anzupassen ist

Alle Modelldaten stehen gebündelt am Anfang des `<script>`-Blocks in `index.html`:

1. Das `modelle`-Array: ein Eintrag je Modell mit `id`, `name`, `beschreibung` und
   optional `badge` (`'NEU'`) oder `blatt: true` (Symbol 🌱 für sparsame Modelle).
   Die Reihenfolge im Array ist die Reihenfolge auf der Seite: nach Anbieter und
   Stärke sortiert, neue Modelle zuoberst.
2. Die Konstante `STAND`, zum Beispiel `'September 2026'`. Sie erscheint automatisch
   im Fußzeilen-Hinweis und im Overlay „Nutzungsbedingungen".
3. Das `recommendations`-Objekt, falls ein Modell wegfällt oder neu zuzuordnen ist.
   Die IDs müssen zu denen im `modelle`-Array passen.

Dazu außerhalb der Datei: einen neuen Abschnitt in `MODELLHISTORIE.md` (neuester
zuoberst, mit Tabelle und Diff zum Vorstand) und die Modellaufzählung oben in dieser
README. Die Zähler in der Statistik-Leiste rechnen sich selbst aus, nur die Anzahl der
Szenarien steht fest im Markup.

### Veröffentlichen

Die Übung wird auf zwei Wegen ausgeliefert, aus derselben Datei:

- **GitHub Pages** (frei nachnutzbare OER-Fassung): Ein Push auf `main` geht direkt
  live. Vorher gegenlesen.
- **Selbstlernkurs „Fit für AIS.chat"** (SchulMoodle Hessen): Dort ist `index.html`
  als Arbeitsmaterial vom Typ „Datei" hinterlegt, bewusst nicht als eingebettete
  Seite von GitHub Pages. Beim Einbetten würde die IP-Adresse jeder Lehrkraft an
  GitHub Inc. übertragen, beim Upload nach Moodle entfällt dieser Drittlandtransfer.
  Nach jeder Änderung also: Aktivität bearbeiten, alte Datei löschen, neue
  `index.html` hochladen, speichern.

Ob die Kursfassung aktuell ist, zeigt der Stand in der Fußzeile der Seite.

### Aktualisieren ohne Git

Falls jemand vertretungsweise nur die Kursfassung aktualisieren muss: Die jeweils
aktuelle Datei liegt unter <https://mgkurz.github.io/ki-modell-auswahl/index.html> und
lässt sich im Browser speichern. Sie ist vollständig eigenständig, es gibt keine
Bilder oder Schriften nachzuladen. Diese Datei in Moodle hochladen, fertig. Wer den
Inhalt selbst ändern muss, kann `index.html` in jedem Texteditor öffnen und die drei
oben genannten Stellen am Anfang des `<script>`-Blocks anpassen. Das Repository zieht
später nach.

## Lizenz

Lizenziert unter der [Creative Commons Namensnennung. Weitergabe unter gleichen Bedingungen 4.0 International (CC BY-SA 4.0)](https://creativecommons.org/licenses/by-sa/4.0/deed.de).

© 2026 Martin Kurz, Hessische Lehrkräfteakademie.

Namensnennung bei Weiterverwendung: „Martin Kurz, Hessische Lehrkräfteakademie, lizenziert unter CC BY-SA 4.0". Bearbeitungen und Weitergaben unter gleicher Lizenz erwünscht.

Nicht von dieser Lizenz erfasst sind die eingebetteten Fremdinhalte: AIS.chat-Logo und Hintergrundmuster sind Kennzeichen des Anbieters und beim Weitergeben unter eigenem Namen zu ersetzen oder zu entfernen. Die Schrift [Barlow](https://openfontlicense.org) steht unter der SIL Open Font License 1.1, die Symbole von [Phosphor Icons](https://phosphoricons.com) unter der MIT-Lizenz.
