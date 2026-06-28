---
title: "Wiki-Richtlinien und Templates"
type: "Meta"
tags: [dsa, meta, regeln, templates, obsidian, quartz]
aliases: ["Regelwerk", "Richtlinien", "Master-Regeln"]
---

# 📜 Wiki-Richtlinien für Obsidian & Quartz 5

## 1. SC- & SL-Trennung (Sicherheit zuerst)
- **Inline-Geheimnisse:** Alles, was nur der Spielleiter (SL) wissen darf, wird innerhalb von SC-Notizen mit `%%` umschlossen.
  *Syntax:* `%% SL-INFO: Text %%`.
  *Effekt:* In Obsidian sichtbar, im Quartz-Build (auf der Webseite) werden diese Blöcke physisch gelöscht.
- **Dokumenten-Quarantäne:** Ganze Notizen, die absolut geheim sind, erhalten im Frontmatter: `draft: true`. Quartz ignoriert diese Dateien beim Build komplett.

## 2. Dateisystem & Stabilität (Die Quartz-Regeln)
Namen sind Schall und Rauch (aber wichtig!): Benenne alle Dateien nach strikter Linux-Konformität um:
- Nur Kleinschreibung.
- Keine Leerzeichen (nutze Bindestriche `-`).
- Keine Umlaute oder Sonderzeichen.
  *Beispiel:* `helden-hauptquartier.md` statt `Helden Hauptquartier.md`.
- **Hinweis zur Darstellung:** Das `title`-Feld im Frontmatter bestimmt die visuelle Überschrift auf deiner Webseite, wodurch der technisch notwendige, strikte Dateiname für die Leser unsichtbar bleibt.
- **Link-Stabilität:** Verlinkungen müssen exakt (`[[dateiname]]`) gesetzt werden. Da Quartz strikt Case-Sensitive ist, darfst du Groß- und Kleinschreibung nicht ignorieren.
- **Interne Verknüpfungen (Piped-Syntax):** Um eine saubere Darstellung bei technischer Stabilität zu gewährleisten, müssen interne Verknüpfungen immer im Format `[[dateiname|titel]]` aufgebaut sein. Dies trennt die technische Dateireferenz von der visuellen Darstellung.

## 3. Frontmatter & Metadaten
- **Anführungszeichen:** Werte mit Doppelpunkten oder Sonderzeichen müssen in Anführungszeichen stehen: `title: "Kampagne: Der Schatten"`.
- **Listen:** Nutzen immer die `[item1, item2]`-Syntax.
- **Leere Felder:** Niemals leere Zeilen stehen lassen. Wenn ein Feld leer ist, lösche es oder schreibe `[]`.

## 4. Text-Struktur & Quartz-Kompatibilität
- **HTML-Maskierung:** Falls du mathematische Zeichen oder HTML-Tags wie `<` oder `>` im Text verwendest, maskiere sie mit Backticks (z.B. `` `<Schuss>` ``), sonst interpretiert Quartz sie als Code.
- **Keine Plug-in-Abhängigkeiten:** Vermeide Plugins wie Dataview, da diese auf der statischen Webseite nicht funktionieren. Setze stattdessen auf manuell gepflegte "Index-Dateien" (z.B. `index_npcs.md`).
- **Bilder:** Bilder sollen sichtbar sein. Dafür benötigen sie das format ![[Bild.jpg]]
 

---

# 🛠️ Strategische Vorlagen (Standardisierung)

Um Zeit zu sparen, nutze in Obsidian Vorlagen (Core-Plugin "Vorlagen" oder "Templater"):

### 1. 👑 Vorlage: Königreich / Region
```markdown
---
title: "{{title}}"
type: "Region"
tags: [dsa, region, geografie]
aliases: []
---
# 👑 {{title}}

## Kurzbeschreibung
*Allgemein bekannter Zustand der Region, politische Zugehörigkeit und landschaftlicher Charakter.*

## Geografie & wichtige Knotenpunkte
- **Hauptstadt:** [[stadtname|Name]]
- **Wichtige Landschaften:** *Wälder, Flüsse, Gebirge*
- **Nachbarregionen:** [[region1|Region 1]], [[region2|Region 2]]

## Kultur & Herrschaftsstruktur
*Wie wird das Land regiert? Welche gesellschaftlichen Normen oder Schichten herrschen vor (z. B. Leibeigenschaft, stolzer Adel, bürgerlicher Freibund)?*

%%
## SL-Bereich
## SL-Daten & Metaplot
- **Aktuelle Krise:** *Welcher Plot-Vektor destabilisiert die Region aktuell (z. B. das Erwachen, Ressourcenknappheit)?*
- **Geheimnisse des Landes:** *Verborgene Anomalien, verfluchte Orte oder geheime Militärbündnisse.*
- **Wichtige SL-NPCs:** [[npc1|NPC 1]], [[npc2|NPC 2]]
%%
```

### 2. 🏙️ Vorlage: Stadt
```markdown
---
title: "{{title}}"
type: "Stadt"
tags: [dsa, stadt, ort]
aliases: []
---
# 🏙️ {{title}}

## Kurzbeschreibung
*Größe der Stadt, strategische Bedeutung und allgemeines Flair (z. B. Handelsmetropole, rauer Grenzhafen).*

## Stadtviertel & Atmosphäre
*Hier die einzelnen Stadtteile auflisten:*
- **Viertel 1 (z. B. Altstadt):** *Charakteristik und Stimmung.*
- **Viertel 2 (z. B. Hafen):** *Gerüche, Gefahren und Bewohner.*

## Wichtige Infrastruktur & Anlaufpunkte
- **Logistik & Handel:** [[kontor|Handelshaus]], [[markt|Marktplatz]]
- **Sicherheit & Militär:** [[garnison|Garde-Festung]]
- **Kultur & Religion:** [[tempel|Tempel der Götter]]

%%
## SL-Bereich
## SL-Daten & Unterwelt
- **Herrschaft & Korruption:** *Wer zieht politisch wirklich die Fäden? Wie empfänglich sind Zöllner oder Gardisten für Schmiergeld?*
- **Die Schattenseiten:** *Welche Verbrechersyndikate (z. B. Schwarzer Lotos, Die Dornen) kontrollieren welche Viertel?*
- **Hehler & Geheimgänge:** [[phex-tempel|Versteckte Phex-Knotenpunkte]] oder Fluchtwege.
%%
```

### 3. 🏡 Vorlage: Dorf
```markdown
---
title: "{{title}}"
type: "Dorf"
tags: [dsa, dorf, ort]
aliases: []
---
# 🏡 {{title}}

## Kurzbeschreibung
*Einwohnerzahl, Lage und primäre systemische Ressource (z. B. landwirtschaftliche Pufferzone, autarkes Holzfällerdorf).*

## Alltag & Atmosphäre
*Wie begegnen die Dörfler Fremden? Welche lokalen Traditionen oder Aberglauben bestimmen das Leben (z. B. Trollkopf-Rüben, Angst vor dem Wald)?*

## Wichtige Personen vor Ort
- **Dorfschulze / Vogt:** [[npc-name|Name]]
- **Wirt der Taverne:** [[npc-name|Name]]
- **Lokale Kapazität:** *Schmied, Heilerin, Geweihter*

%%
## SL-Bereich
## SL-Daten & Lokale Bedrohungen
- **Dunkles Geheimnis:** *Was verschweigt die Dorfgemeinschaft (z. B. Paktierer im Keller, illegale Zuflucht für entflohene Leibeigene)?*
- **Lokale Anomalie:** *Umliegende Gefahrengebiete (z. B. ein Sumpfloch, erwachte Tiere im nahen Forst).*
- **Loot vor Ort:** *Was können die Helden hier requirieren oder stehlen?*
%%
```

### 4. 📍 Vorlage: Ort (Gebäude / Point of Interest)
```markdown
---
title: "{{title}}"
type: "Ort"
tags: [dsa, ort, gebaeude]
aliases: []
---
# 📍 {{title}}

## Kurzbeschreibung
*Spezifischer Ort (z. B. Magierakademie, Hesindetempel, verrauchte Spelunke).*

## Aussehen & Atmosphäre
*Architektur, Gerüche, Lichtverhältnisse und der erste Eindruck, den die Spieler beim Betreten erhalten.*

## Funktion & Relevanz
*Warum kommen die Helden hierher? Welche offiziellen Dienstleistungen, Ressourcen oder Kontakte bietet dieser Ort?*

%%
## SL-Bereich
## SL-Daten & Taktische Details
- **Sicherheitsvorkehrungen:** *Schlösser, Wachen, magische Alarmsysteme.*
- **Verborgene Räume:** *Geheimtüren, Falltüren, Verstecke für Dokumente oder Trug-Gold.*
- **Grundriss / Heist-Notizen:** *Dienstpläne der Wachen, Fluchtwege.*
%%
```

### 5. 👥 Vorlage: Volk / Kultur
```markdown
---
title: "{{title}}"
type: "Kultur"
tags: [dsa, kultur, fraktion]
aliases: []
---
# 👥 {{title}}

## Kurzbeschreibung
*Definition des Volkes oder der nomadischen/sesshaften Kultur (z. B. Norbarden, Nivesen, Goblins).*

## Verbreitung & Lebensraum
*Wo schlägt dieses Volk vornehmlich seine Lager auf? Welche Routen oder Enklaven (z. B. Gerberviertel in Festum) nutzt es?*

## Traditionen, Glaube & Mentalität
*Kulturelle Kernwerte, ehrbewusstes Verhalten, Abneigung gegen Intrigen und das Verhältnis zu den ansässigen Bornländern/Mittelländern.*

%%
## SL-Bereich
## SL-Hintergründe & Kampagnen-Fokus
- **Geheimwissen:** *Alte Mythen (z. B. Kunga Suula, Mailam Rekdai), die nur diesem Volk bekannt sind.*
- **Kultur-Crunch:** *Typische Waffen (z. B. Borndorne, Skraja) und Ausrüstung, die Mitglieder standardmäßig mit sich führen.*
- **Wichtige Sippenoberhäupter:** [[npc-name|Name (z. B. Zibiljas oder Schamaninnen)]].
%%
```

### 6. 👤 Vorlage: Person (NPC)
```markdown
---
title: "{{title}}"
type: "Charakter"
tags: [dsa, npc]
aliases: []
draft: false
---

# 👤 {{title}}

| Porträt | Informationen |
| :--- | :--- |
| ![[bild.jpg\|250]] | ![[wappen.jpg\|100]] <br><br> **I. Titel & Name:** {{title}} <br> **II. Kurzname:** {{alias}} <br> **III. Aussehen:** <br> *Hier Aussehen beschreiben...* <br> **IV. Charakter / Verhalten:** <br> *Hier Verhalten beschreiben...* |

---

### 📝 Weitere Details
**Position:** *Hier einfügen*
**Aufgaben:** *Hier einfügen*
**Politische Stellung:** *Hier einfügen*
**Kontakte:** [[kontakt1]], [[kontakt2]]
**Restliche Infos:** *Hier einfügen*

---

%%

## SL-Bereich
## Spielwerte & Meister-Daten

- **Spielwerte (Crunch):**
    - *LeP:* | *AsP/KaP:* | *RS:* 
    - *Waffen:* [[waffe1\|Name]] (AT/TP)
    - *Wichtige Talente:* 
- **Geheime Motivation:** *Was treibt die Person im Hintergrund an?*
- **Geheimnisse:** *Leichen im Keller, Pakt-Ansätze.*
- **Intrigen & Pläne:** *Wie manipuliert dieser NPC das System?*

%%
```

### 7. 🤝 Vorlage: Organisation / Fraktion
```markdown
---
title: "{{title}}"
type: "Organisation"
tags: [dsa, organisation, fraktion]
aliases: []
---
# 🤝 {{title}}

## Ziele & Philosophie
*Die offizielle Agenda der Gruppierung (z. B. Schutz von Wissen bei den Satori, Bewahrung der Adelsstruktur beim Widderorden).*

## Bekannte Mitglieder & Struktur
- **Anführer / Kopf:** [[npc-name|Name]]
- **Wichtige Agenten:** [[npc-name|Name]], [[npc-name|Name]]
- **Operationsbasis:** [[ort-name|Hauptquartier / Tempel]]

## Einfluss & Ressourcen
*Über wie viel Macht verfügt die Fraktion? Kontrolliert sie Handelswege, Stadträte, Magierakademien oder den Schwarzmarkt?*

%%
## SL-Bereich
## Wahre Absichten & Innere Korruption
- **Das wahre Gesicht:** *Was ist die verborgene Agenda (z. B. Unterwanderung durch den Korsmal-Bund oder Stehlen magischer Goblin-Rituale)?*
- **Erkennungszeichen:** *Geheime Phrasen, Tätowierungen oder Siegelringe.*
- **Ermittlungs-Ansätze:** *Wie können die Helden Beweise gegen diese Fraktion sammeln?*
%%
```

### 8. ⚔️ Vorlage: Gegenstand (Item / Beute)
```markdown
---
title: "{{title}}"
type: "Gegenstand"
tags: [dsa, item, ausruestung]
aliases: []
---
# ⚔️ {{title}}

## Beschreibung & Optik
*Was sehen die Helden, wenn sie den Gegenstand betrachten? (z. B. Gravuren, Material, Abnutzungserscheinungen).*

## Bekannte Geschichte / Herkunft
*Woher stammt das Objekt üblicherweise? Wer nutzt es (z. B. Standardwaffe der Flößer, seltener Kälteschutz)?*

%%
## SL-Bereich
## Werte & Magische Mechaniken
- **Regel-Effekte (Crunch):**
    * *Typ:* Nahkampf / Rüstung / Konsumgut
    * *Rüstungsschutz (RS):* 3 | *Behinderung (BE):* 1
    * *Spezial-Effekt:* *Kälteschutz oder alchimistischer Bonus (z. B. Meskinnes als Brandbeschleuniger).*
- **Wahrer Wert:** *Preis in Dukaten / Silbertalern auf dem Schwarzmarkt.*
- **Dämonische / Magische Anomalie:** *Handelt es sich um verfluchtes Metall (Trug-Gold) oder ein mit Sikaryan aufgeladenes Relikt? Welche Nebenwirkungen treten auf?*
%%
```

### 9. ✨ Vorlage: Magie (Zauber / Tradition / Phänomen)
```markdown
---
title: "{{title}}"
type: "Magie"
tags: [dsa, magie, zauber]
aliases: []
---
# ✨ {{title}}

## Wirkung & Bekannte Effekte
*Was passiert visuell und akustisch, wenn diese Magie gewirkt wird (z. B. Tauschrausch, optische Anomalien wie Gesichter in Rinden, urtümliches Pflanzenwachstum)?*

## Verbreitung & Traditionen
*Wer beherrscht diese Kräfte (z. B. Gildenmagier der Halle des Quecksilbers, Hexen der Jassuula-Sippe, Goblin-Zauberinnen)?*

%%
## SL-Bereich
## Harte Regeln & Metamagie
- **Zauber-Crunch:**
    * *Probe:* MU/IN/CH (modifiziert um Seelenkraft)
    * *AsP-Kosten:* 8 AsP | *Zauberdauer:* 4 Aktionen
    * *Reichweite:* 8 Schritt | *Wirkungsdauer:* QS x 3 Minuten
- **Gefahrenpotenzial (Metaplot):** *Wie reagiert das Erwachen des Landes auf das Wirken dieses Zaubers (z. B. sofortiger Zorn-Effekt, elementares Chaos)?*
- **Gegenmaßnahmen:** *Wie kann der Zauber gebrochen, analysiert oder geblockt werden (z. B. Wundauflage aus Widderdorn)?*
%%
```

# 🎨 Icon-Richtlinien für Obsidian & Quartz 5

Um die Stabilität deines Wikis beim Quartz-5-Build zu gewährleisten, ist die Verwendung von Icons strengen technischen Regeln unterworfen.

## 1. Technische Kriterien für Icons
*   **Unicode-Standard (Emoji-Zeichen):** Quartz 5 verarbeitet Markdown zu statischem HTML. Die sicherste Wahl sind Unicode-Emojis. Diese werden von modernen Browsern nativ als Text-Zeichen interpretiert. Da sie kein "echtes" Bild laden müssen, sind sie extrem stabil, schnell und erzeugen keine defekten Dateipfade.
*   **System-Neutralität:** Verwende Emojis, die zu den Standard-Unicode-Blöcken gehören. Diese werden auf Windows, macOS, Linux, iOS und Android einheitlich erkannt.
*   **Keine Dateipfad-Abhängigkeit:** Ein Icon darf **niemals** eine externe Bilddatei sein (z. B. eine .svg oder .png), wenn du es in eine Überschrift einbetten willst. Sobald du einen `icon.png`-Link in einer Überschrift nutzt, riskierst du, dass der Build-Prozess von Quartz den Pfad nicht korrekt auflöst.

## 2. Was ein Icon für die "Quartz-Tauglichkeit" ausmacht
Damit ein Icon "Quartz-5-tauglich" ist, muss es folgende Eigenschaften besitzen:
*   **Keine Leerzeichen/Sonderzeichen im Dateinamen:** Dies ist das wichtigste Quartz-Gesetz. Vermeide Bilder als Icons komplett und nutze Emojis, da diese die Problematik fehlerhafter Dateipfade komplett eliminieren.
*   **Keine Maskierungs-Probleme:** Ein Unicode-Emoji benötigt keine Maskierung und ist kein HTML-Code. Daher interpretiert Quartz es direkt als Text-Zeichen, was es immun gegen Build-Fehler macht.
*   **Case-Sensitivity:** Wenn du ein Bild-Icon nutzen musst, muss der Dateiname im Code exakt so geschrieben sein wie auf der Festplatte. Da dies oft zu Fehlern führt, sind Unicode-Emojis die einzig 100 % fehlerfreie Lösung.

## 3. Checkliste für funktionierende Icons
| Kriterium | Erfüllung für Quartz 5 |
| :--- | :--- |
| **Typ** | Nutze ausschließlich Unicode-Emojis. |
| **Einbettung** | Platziere sie direkt als Text hinter der `#` Überschrift. |
| **Stabilität** | Sie benötigen keine Datei-Pfade (keine toten Links). |
| **Performance** | Sie haben keine Ladezeit, da sie Teil der System-Schriftart sind. |
| **Struktur** | Sie dürfen **nicht** in den Dateinamen landen, nur im Inhalt (H1). |

---



---

🛠️ Erlaubte Fantasy-Icons (System-stabil)

---

🏛️ Herrschaft & Architektur
🏰, 🏯, 🏚️, ⛪, 🕍, 🕌, ⛩️, 🏛️, 🏘️, 🛖, ⛺, 🏠, 🏡, 🗼, ⛲, 🕰️, 📜, 🗺️, ⚖️, 🗝️, 🛡️, ⚔️, 🪓, 🏹, 🗡️, ⛓️, 🚪, 🪑, 🖼️, 🎨, 🎭, 🪦, ⚱️

🌳 Natur & Wildnis
🌲, 🌳, 🌴, 🌵, 🌾, 🌿, ☘️, 🍀, 🎍, 🍃, 🍂, 🍁, 🍄, 🐚, 🪨, 🪵, 🏔️, ⛰️, 🌋, 🗻, 🏖️, 🏜️, 🏝️, 🌊, 💧, ☁️, ☀️, 🌤️, ⛅, 🌦️, 🌧️, 🌨️, 🌩️, 🌪️, 🌫️, 🌬️, ❄️, ⛄, ☄️, 🌌, 🌠, 🎆, 🎇, 🌑, 🌕, 🌙, 🪐, 💫, ⭐️, 🌟, ✨, 🦄, 🐉, 🐲, 🐺, 🦁, 🐯, 🦒, 🦊, 🐻, 🐼, 🐹, 🐭, 🐰, 🐿️, 🐦, 🦅, 🦉, 🦇, 🐝, 🪱, 🐛, 🦋, 🐞, 🐜, 🕷️, 🦂

📜 Wissen, Magie & Alchemie
🔮, 🧪, ⚗️, 🔭, 🕯️, 💡, 🏮, 🧨, 📖, 📚, 📒, 📔, 📓, 📕, 📗, 📘, 📙, 📃, 📄, 📑, 🧾, 🗞️, 📰

💰 Handel, Seefahrt & Logistik
💰, 🪙, ⛵, ⚓, 🛶, 🎁, 📮, 📯

🧭 Himmelsrichtungen & Positionen
⬆️, ↗️, ➡️, ↘️, ⬇️, ↙️, ⬅️, ↖️, 📍, 🗺️, 🧭, 

⚠️ Wichtig & Warnung
⚠️, 🚫, ❗, ❓, ❔, ❕, ‼️, ⁉️,

👤 Gesellschaft & Personen
👤, 👥, 🫂, 👪, 👣, 🗣️, 👂, 🦷, 👅, 🧠, 🫀, 🫁

# 🛠️ Erlaubte Fantasy-Icons (System-stabil)

### 🏛️ Herrschaft & Architektur
🏰, 🏯, 🏚️, ⛪, 🕍, 🕌, ⛩️, 🏛️, 🏘️, 🛖, ⛺, 🏠, 🏡, 🗼, ⛲, 🕰️, 📜, 🗺️, ⚖️, 🗝️, 🛡️, ⚔️, 🪓, 🏹, 🗡️, ⛓️, 🚪, 🪑, 🖼️, 🎨, 🎭, 🪦, ⚱️

### 🌳 Natur & Wildnis
🌲, 🌳, 🌴, 🌵, 🌾, 🌿, ☘️, 🍀, 🎍, 🍃, 🍂, 🍁, 🍄, 🐚, 🪨, 🪵, 🏔️, ⛰️, 🌋, 🗻, 🏖️, 🏜️, 🏝️, 🌊, 💧, ☁️, ☀️, 🌤️, ⛅, 🌦️, 🌧️, 🌨️, 🌩️, 🌪️, 🌫️, 🌬️, ❄️, ⛄, ☄️, 🌌, 🌠, 🎆, 🎇, 🌑, 🌕, 🌙, 🪐, 💫, ⭐️, 🌟, ✨, 🦄, 🐉, 🐲, 🐺, 🦁, 🐯, 🦒, 🦊, 🐻, 🐼, 🐹, 🐭, 🐰, 🐿️, 🐦, 🦅, 🦉, 🦇, 🐝, 🪱, 🐛, 🦋, 🐞, 🐜, 🕷️, 🦂

### 📜 Wissen, Magie & Alchemie
🔮, 🧪, ⚗️, 🔭, 🕯️, 💡, 🏮, 🧨, 📖, 📚, 📒, 📔, 📓, 📕, 📗, 📘, 📙, 📃, 📄, 📑, 🧾, 🗞️, 📰

### 💰 Handel, Seefahrt & Logistik
💰, 🪙, ⛵, ⚓, 🛶, 🎁, 📮, 📯

### 🧭 Himmelsrichtungen & Positionen
⬆️, ↗️, ➡️, ↘️, ⬇️, ↙️, ⬅️, ↖️, 📍, 🗺️, 🧭, 

### ⚠️ Wichtig & Warnung
⚠️, 🚫, ❗, ❓, ❔, ❕, ‼️, ⁉️,

### 👤 Gesellschaft & Personen
👤, 👥, 🫂, 👪, 👣, 🗣️, 👂, 🦷, 👅, 🧠, 🫀, 🫁