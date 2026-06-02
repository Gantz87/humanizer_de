# Humanizer DE

Ein Skill für Claude Code und OpenCode, der typische Anzeichen von KI-generierten Texten entfernt, damit diese natürlicher und menschlicher klingen. Jetzt auch für deutsche Texte.

## Installation

### Claude Code

Klone das Repository direkt in das Skills-Verzeichnis von Claude Code:

```bash
mkdir -p ~/.claude/skills
git clone https://github.com/blader/humanizer.git ~/.claude/skills/humanizer

```

Oder kopiere die Skill-Datei manuell, falls du dieses Repo bereits geklont hast:

```bash
mkdir -p ~/.claude/skills/humanizer
cp SKILL.md ~/.claude/skills/humanizer/

```

### OpenCode

Klone das Repository direkt in das Skills-Verzeichnis von OpenCode:

```bash
mkdir -p ~/.config/opencode/skills
git clone https://github.com/blader/humanizer.git ~/.config/opencode/skills/humanizer

```

Oder kopiere die Skill-Datei manuell, falls du dieses Repo bereits geklont hast:

```bash
mkdir -p ~/.config/opencode/skills/humanizer
cp SKILL.md ~/.config/opencode/skills/humanizer/

```

> **Hinweis:** OpenCode scannt aus Kompatibilitätsgründen auch `~/.claude/skills/`. Wenn du also beide Tools nutzt, reicht ein einziger Klonvorgang nach `~/.claude/skills/humanizer/` aus.

## Verwendung

### Claude Code

```
/humanizer

[Füge deinen Text hier ein]

```

### OpenCode

```
/humanizer

[Füge deinen Text hier ein]

```

Oder bitte das Modell in einem der beiden Tools direkt darum, den Text zu vermenschlichen:

```
Please humanize this text: [dein Text]

```

### Stil-Kalibrierung (Voice Calibration)

Um deinen persönlichen Schreibstil zu treffen, kannst du eine Arbeitsprobe von dir selbst bereitstellen:

```
/humanizer

Here's a sample of my writing for voice matching:
[Füge 2-3 Absätze deines eigenen Schreibstils ein]

Now humanize this text:
[Füge den KI-Text ein, der vermenschlicht werden soll]

```

Der Skill analysiert deinen Satzrhythmus, deine Wortwahl sowie persönliche Eigenheiten und wendet diese auf den umschriebenen Text an, anstatt ein generisches „sauberes“ Ergebnis zu liefern.

## Übersicht

Basiert auf dem Wikipedia-Leitfaden [„Signs of AI writing“](https://en.wikipedia.org/wiki/Wikipedia:Signs_of_AI_writing) (Anzeichen für KI-Texte), der vom WikiProject AI Cleanup gepflegt wird. Dieser umfassende Leitfaden basiert auf Beobachtungen von Tausenden von Beispielen KI-generierter Texte.

Der Skill beinhaltet zudem eine finale Audit-Prüfung auf „offensichtlich KI-generierte“ Merkmale und führt eine zweite Überarbeitung durch, um verbleibende KI-Floskeln aus dem ersten Entwurf herauszufiltern.

### Zentrale Erkenntnis von Wikipedia

> „LLMs nutzen statistische Algorithmen, um vorherzusagen, welches Wort als nächstes folgen sollte. Das Ergebnis tendiert meist zum statistisch wahrscheinlichsten Resultat, das auf die größte Vielfalt von Fällen zutrifft.“

## 30 erkannte Muster (mit Vorher-/Nachher-Beispielen)

### Inhaltliche Muster (Content Patterns übernommen aus dem Original)

| # | Muster | Vorher | Nachher |
| --- | --- | --- | --- |
| 1 | **Bedeutungsaufblähung** | „markiert einen Meilenstein in der Evolution von...“ | „wurde 1989 gegründet, um regionale Statistiken zu erfassen“ |
| 2 | **Relevanz-Heischerei (Name-Dropping)** | „erwähnt in NYT, BBC, FT und The Hindu“ | „In einem Interview mit der NYT im Jahr 2024 argumentierte sie...“ |
| 3 | **Oberflächliche Verlaufs-Analysen** | „symbolisiert... reflektiert... zeigt auf...“ | Entfernen oder mit echten Quellen untermauern |
| 4 | **Werbliche Sprache** | „eingebettet in der atemberaubenden Region“ | „ist eine Stadt in der Region Gonder“ |
| 5 | **Vage Zuschreibungen** | „Experten glauben, dass es eine entscheidende Rolle spielt“ | „laut einer Umfrage aus dem Jahr 2019 von...“ |
| 6 | **Formelhafte Herausforderungen** | „Trotz Herausforderungen... floriert es weiterhin“ | Spezifische Fakten über tatsächliche Herausforderungen nennen |

### Sprachliche Muster (Language Patterns)

| # | Muster | Vorher | Nachher |
| --- | --- | --- | --- |
| 7 | **KI-Vokabular** | „Tatsächlich... zusätzlich... Vermächtnis... Landschaft... aufzeigen“ | „auch... bleiben häufig“ |
| 8 | **Vermeidung von Hilfsverben** | „dient als... zeichnet sich aus durch... besticht durch“ | „ist... hat“ |
| 9 | **Negative Parallelismen / Angehängte Verneinungen** | „Es ist nicht nur X, es ist Y“, „..., kein Raten“ | Den Punkt direkt auf den Punkt bringen |
| 10 | **Dreierregel (Rule of three)** | „Innovation, Inspiration und Einblicke“ | Eine natürliche Anzahl von Elementen verwenden |
| 11 | **Synonym-Karussell** | „Protagonist... Hauptfigur... zentrale Gestalt... Held“ | „Protagonist“ (wiederholen, wenn es am klarsten ist) |
| 12 | **Künstliche Bandbreiten** | „vom Urknall bis zur dunklen Materie“ | Themen direkt auflisten |
| 13 | **Passiv / Subjektlose Fragmente** | „Keine Konfigurationsdatei erforderlich“ | Den Akteur nennen, wenn es der Klarheit dient |

### Stilistische Muster (Style Patterns)

| # | Muster | Vorher | Nachher |
| --- | --- | --- | --- |
| 14 | **Gedankenstriche (— / –)** | „Institutionen—nicht die Menschen—doch dies geht weiter—“ | Streichen: Punkte, Kommas, Doppelpunkte oder Klammern nutzen |
| 15 | **Übermäßiger Fettdruck** | „**OKRs**, **KPIs**, **BMC**“ | „OKRs, KPIs, BMC“ |
| 16 | **Listen mit integrierten Überschriften** | „**Leistung:** Die Leistung wurde verbessert“ | In Fließtext umwandeln |
| 17 | **Überschriften in Groß-/Kleinschreibung (Title Case)** | „Strategische Verhandlungen Und Partnerschaften“ | „Strategische Verhandlungen und Partnerschaften“ |
| 18 | **Emojis** | „🚀 Startphase: 💡 Wichtige Erkenntnis:“ | Emojis entfernen |
| 19 | **Typografische Anführungszeichen** | `sagte „das Projekt“` | `sagte „das Projekt“` |
| 26 | **Wortpaare mit Bindestrich** | „bereichsübergreifend, datengesteuert, kundenorientiert“ | Bindestriche bei geläufigen Wortpaaren weglassen |
| 27 | **Floskeln pseudopersuasiver Autorität** | „Im Kern kommt es darauf an, dass...“ | Den Punkt direkt formulieren |
| 28 | **Ankündigende Wegweiser** | „Tauchen wir ein“, „Hier ist, was Sie wissen müssen“ | Direkt mit dem Inhalt beginnen |
| 29 | **Fragmentierte Überschriften** | „## Leistung“ + „Geschwindigkeit zählt.“ | Die Überschrift die Arbeit machen lassen |
| 30 | **Diff-orientiertes Schreiben** | „Diese Funktion wurde hinzugefügt, um X zu ersetzen...“ | Beschreiben, was sie tut, nicht was sich geändert hat |

### Kommunikationsmuster (Communication Patterns)

| # | Muster | Vorher | Nachher |
| --- | --- | --- | --- |
| 20 | **Chatbot-Artefakte** | „Ich hoffe, das hilft! Lassen Sie mich wissen, wenn...“ | Restlos entfernen |
| 21 | **Disclaimer bei Wissensgrenzen** | „Obwohl die Details in den verfügbaren Quellen begrenzt sind...“ | Quellen finden oder den Satz entfernen |
| 22 | **Unterwürfiger/Kriecherischer Ton** | „Tolle Frage! Sie haben absolut recht!“ | Direkt antworten |

### Füllwörter und Relativierungen (Filler and Hedging)

| # | Muster | Vorher | Nachher |
| --- | --- | --- | --- |
| 23 | **Füllfloskeln** | „Um zu“, „Aufgrund der Tatsache, dass“ | „Für“, „Weil“ |
| 24 | **Übermäßige Relativierung** | „könnte potenziell möglicherweise“ | „kann“ / „dürfte“ |
| 25 | **Generische Schlussfolgerungen** | „Die Zukunft sieht rosig aus“ | Spezifische Pläne oder Fakten nennen |

### Deutsch-spezifische Ergänzungen (neue Muster): 

| # | Muster | Vorher | Nachher |
| --- | --- | --- | --- |
| 7 | **Deutsche KI-Vokabeln** | „facettenreich“, „tiefgreifend“, „wegweisend“, „diesbezüglich“ | Präzise, natürliche deutsche Begriffe verwenden |
| 9 | **Nominalisierungsstil** | „Die Durchführung der Analyse erfolgt durch das Team“ | „Das Team analysiert“ (Verwaltungsdeutsch vermeiden) |
| 14 | **Passivkonstruktionen** | „Es wird darauf hingewiesen“, „Es ist zu beachten“, „Es sei erwähnt“ | Aktiv formulieren, Akteur direkt benennen |
| 18 | **Falsche Anführungszeichen** | "Text" oder “Text” (englische/gerade Zeichen) | „Text“ (korrekte deutsche Anführungszeichen) |
| 23 | **Deutsche Füllphrasen** | „Im Folgenden wird dargestellt“, „Zusammenfassend lässt sich festhalten“ | Direkt mit dem Inhalt starten |
| 26 | **Anglizismus-Bindestriche** | „cross-funktional“, „data-driven“ | „bereichsübergreifend“, „datenbasiert“ |

## Vollständiges Beispiel

**Vorher (Klingt nach KI):**

> Tolle Frage! Hier ist ein Essay zu diesem Thema. Ich hoffe, das hilft!
> Das KI-gestützte Codieren dient als dauerhaftes Vermächtnis für das transformative Potenzial großer Sprachmodelle und markiert einen Meilenstein in der Evolution der Softwareentwicklung. In der sich heute schnell entwickelnden technologischen Landschaft verändern diese bahnbrechenden Werkzeuge — eingebettet an der Schnittstelle von Forschung und Praxis — die Art und Weise, wie Ingenieure Ideen entwickeln, iterieren und liefern, was ihre entscheidende Rolle in modernen Arbeitsabläufen unterstreicht.
> Im Kern ist das Wertversprechen klar: Prozesse rationalisieren, die Zusammenarbeit verbessern und die Abstimmung fördern. Es geht nicht nur um Autovervollständigung; es geht darum, Kreativität im großen Stil freizusetzen, um sicherzustellen, dass Organisationen agil bleiben, während sie den Nutzern nahtlose, intuitive und leistungsstarke Erlebnisse bieten. Das Werkzeug dient als Katalysator. Der Assistent fungiert als Partner. Das System steht als Fundament für Innovation.
> Branchenbeobachter haben festgestellt, dass sich die Akzeptanz von Hobby-Experimenten zu unternehmensweiten Rollouts beschleunigt hat, von Solo-Entwicklern bis hin zu bereichsübergreifenden Teams. Die Technologie wurde in der New York Times, Wired und The Verge vorgestellt. Zusätzlich zeigt die Fähigkeit, Dokumentationen, Tests und Refactorings zu generieren, wie KI zu besseren Ergebnissen beitragen kann, was das komplexe Zusammenspiel zwischen Automatisierung und menschlichem Urteilsvermögen aufzeigt.
> * 💡 **Geschwindigkeit:** Die Code-Generierung ist erheblich schneller, was Reibungsverluste reduziert und Entwickler stärkt.
> * 🚀 **Qualität:** Die Ausgabequalität wurde durch verbessertes Training gesteigert, was zu höheren Standards beiträgt.
> * ✅ **Akzeptanz:** Die Nutzung wächst weiter, was breitere Branchentrends widerspiegelt.
> 
> 
> Obwohl spezifische Details auf der Grundlage der verfügbaren Informationen begrenzt sind, könnte potenziell argumentiert werden, dass diese Werkzeuge eine gewisse positive Wirkung haben könnten. Trotz der für aufstrebende Technologien typischen Herausforderungen — einschließlich Halluzinationen, Voreingenommenheit und Rechenschaftspflicht — floriert das Ökosystem weiterhin. Um dieses Potenzial voll auszuschöpfen, müssen sich die Teams an Best Practices ausrichten.
> Zusammenfassend lässt sich sagen, dass die Zukunft rosig aussieht. Es liegen aufregende Zeiten vor uns, während wir diese Reise zur Exzellenz fortsetzen. Lassen Sie mich wissen, wenn ich einen Abschnitt für Sie erweitern soll!

**Nachher (Vermenschlicht):**

> KI-Programmierassistenten können die langweiligen Teile des Jobs beschleunigen. Sie sind großartig für Boilerplate: Konfigurationsdateien und den kleinen Glue-Code, den man nicht selbst schreiben möchte. Sie können auch dabei helfen, einen Test zu skizzieren, aber man muss ihn trotzdem Korrektur lesen.
> Der gefährliche Teil ist, wie selbstbewusst die Vorschläge aussehen. Ich habe schon Code übernommen, der kompiliert wurde und den Linter passiert hat, nur um später festzustellen, dass er am Thema vorbeiging, weil ich nicht mehr richtig aufgepasst habe.
> Wenn man es wie eine Autovervollständigung behandelt und jede Zeile überprüft, ist es nützlich. Wenn man es benutzt, um das Denken zu vermeiden, hilft es einem nur dabei, Bugs schneller auszuliefern.
> Die einzige echte Absicherung sind Tests. Ohne sie beurteilt man meistens nur Bauchgefühle.

## Referenzen

* [Wikipedia: Signs of AI writing](https://en.wikipedia.org/wiki/Wikipedia:Signs_of_AI_writing) - Hauptquelle
* [WikiProject AI Cleanup](https://en.wikipedia.org/wiki/Wikipedia:WikiProject_AI_Cleanup) - Pflegende Organisation

## Versionshistorie

* **1.0.0** - Erstveröffentlichung. Fork von Humanizer 2.7.0 von blade

## Lizenz

MIT
