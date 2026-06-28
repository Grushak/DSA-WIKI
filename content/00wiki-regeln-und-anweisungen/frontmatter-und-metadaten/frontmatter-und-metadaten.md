---
title: "Frontmatter & Metadaten (Detailerklärung)"
type: "meta"
tags: [dsa, meta, regeln, obsidian, quartz, yaml]
aliases: [frontmatter, metadaten]
draft: false
---

# 📜 Frontmatter & Metadaten (Detailerklärung)

## Kurzbeschreibung
Das Frontmatter ist der durch `---` umschlossene Block ganz oben in einer Markdown-Datei. Es enthält strukturierte Metadaten (YAML), die für das Routing, die Tags und die Suchfunktion der Quartz-5-Webseite zwingend erforderlich sind. Diese Seite erklärt im Detail die drei wichtigsten Regeln, um Build-Abstürze zu verhindern.

---

## 1. Anführungszeichen (Sonderzeichen maskieren)
Der YAML-Parser in Quartz stolpert über bestimmte Zeichen, wenn sie als Teil des Textes gedacht sind, aber wie Code aussehen. Das gefährlichste Zeichen ist der **Doppelpunkt (`:`)**. 

Wenn in einem Titel ein Doppelpunkt vorkommt, denkt Quartz, hier beginnt eine neue Daten-Zuweisung, und das System stürzt ab. Um das zu verhindern, muss der gesamte Wert in doppelte Anführungszeichen (`"..."`) gesetzt werden.

> [!danger] Falsch (Führt zum Absturz)
> `title: Kampagne: Der Schatten`
> `ort: [[Festum]] (Halle des Quecksilbers)` *(Hier brechen die eckigen Klammern das System)*

> [!success] Korrekt (System-stabil)
> `title: "Kampagne: Der Schatten"`
> `ort: "[[festum|Festum]] (Halle des Quecksilbers)"`

**Fazit:** Gewöhne dir an, Textwerte (wie `title` oder Freitext-Felder) immer in Anführungszeichen zu setzen. Das ist die sicherste Methode.

---

## 2. Listen & Arrays (`[item1, item2]`-Syntax)
Metadaten wie `tags` oder `aliases` enthalten oft mehrere Werte. In Obsidian gibt es verschiedene Wege, Listen zu erstellen (z.B. mit Spiegelstrichen untereinander). Quartz 5 verarbeitet diese Listen jedoch am schnellsten und fehlerfreisten, wenn sie in der sogenannten "Inline-Array-Syntax" geschrieben werden.

> [!danger] Falsch (oder fehleranfällig in Quartz)
> `tags:`
> `- dsa`
> `- npc`

> [!success] Korrekt (System-stabil)
> `tags: [dsa, npc, stadt]`
> `aliases: ["Der Schwarze", "Magister"]`

**Fazit:** Nutze immer die eckigen Klammern `[]` und trenne die Begriffe mit einem Komma und einem Leerzeichen.

---

## 3. Leere Felder (Keine "Null"-Werte)
Wenn du eine Vorlage lädst, enthält diese oft Felder, die du für den aktuellen Eintrag vielleicht gar nicht brauchst (z. B. `aliases:` bei einem unwichtigen NPC). 

Lässt du das Feld einfach leer stehen, liest der Quartz-Parser den Wert als `null` (nicht existent). Dies kann bei Plugins, die Arrays erwarten (wie der Suchfunktion oder dem Graph), zu kritischen Fehlern führen.

> [!danger] Falsch (Führt zu "Null"-Error)
> `aliases:` 
> `draft: false`

> [!success] Korrekt (System-stabil)
> `aliases: []`
> `draft: false`

**Fazit:** Lösche ungenutzte Zeilen im Frontmatter entweder komplett heraus, oder weise ihnen ein explizit leeres Array (`[]`) oder leere Anführungszeichen (`""`) zu.

---

%%
## SL-Bereich
## Interne Wartungsnotizen
- **Automatisierung:** Um diese drei Fehlerquellen zu eliminieren, wurde das Plugin "Linter" eingerichtet. Es korrigiert fehlende Anführungszeichen und wandelt leere Felder beim Drücken von `Strg + S` automatisch in `[]` um.
- **Troubleshooting:** Wenn der GitHub-Build mit einem Fehler wie `bad indentation of a mapping entry` fehlschlägt, ist zu 99% ein unmaskiertes Sonderzeichen im Frontmatter der zuletzt bearbeiteten Datei schuld.
%%