# German Language LLM Guide (DACH)

[![Version](https://img.shields.io/github/v/release/abbottis/German-Language-LLM-Guide-DACH?label=version&color=blue)](https://github.com/abbottis/German-Language-LLM-Guide-DACH/releases)
[![LLM Compatibility](https://img.shields.io/badge/LLMs-Claude_%7C_GPT_%7C_Gemini_%7C_Llama_%7C_Mistral-green)](https://github.com/abbottis/German-Language-LLM-Guide-DACH)
[![License: MIT](https://img.shields.io/badge/license-MIT-yellow.svg)](LICENSE)

**Drop-in prompt modules that make LLMs write natural German instead of robot German. Covers grammar, typography, banned phrases, and regional variants for Germany, Austria, and Switzerland.**

LLMs produce German that is grammatically correct but stylistically off – full of nominalizations, repetitive sentence openers, English punctuation, and the same handful of filler phrases. This repository provides modular prompt blocks you can drop into any system prompt to fix that.

---

**Prompt-Module für natürliches, menschlich klingendes Deutsch in LLM-Ausgaben.**

LLMs erzeugen grammatisch korrektes, aber stilistisch auffälliges Deutsch – voller Substantivierungen, repetitiver Satzanfänge, englischer Zeichensetzung und immer derselben Füllphrasen. Dieses Repository liefert modulare Prompt-Bausteine, die du in jeden System-Prompt einbauen kannst.

---

## Why does this exist? / Warum gibt es das?

Every major LLM has the same problem with German output:

- **Nominalization overload** – "Die Durchführung der Optimierung" instead of "Wir optimieren"
- **Robotic sentence structure** – Every sentence starts with the subject
- **English punctuation habits** – Straight quotes ("") instead of German „"
- **Phrase recycling** – "Tauchen wir ein", "In der heutigen Zeit", "nahtlos"
- **List mania** – Bullet points instead of prose, even where prose reads better
- **Monotone rhythm** – Every sentence the same length and complexity

These modules tackle each problem individually, so you can pick what you need.

---

Jedes große LLM hat dasselbe Problem mit deutscher Ausgabe:

- **Substantivierungs-Inflation** – „Die Durchführung der Optimierung" statt „Wir optimieren"
- **Roboterhafter Satzbau** – Jeder Satz beginnt mit dem Subjekt
- **Englische Zeichensetzung** – Gerade Anführungszeichen ("") statt „"
- **Phrasen-Recycling** – „Tauchen wir ein", „In der heutigen Zeit", „nahtlos"
- **Aufzählungsmanie** – Bullet-Listen statt Fließtext
- **Monotoner Rhythmus** – Jeder Satz gleich lang und gleich komplex

Diese Module behandeln jedes Problem einzeln – nimm, was du brauchst.

---

## Modules / Module

| File | Purpose | Required? |
|------|---------|-----------|
| [`core.md`](core.md) | Grammar, syntax, style – the foundation | **Yes** |
| [`typography.md`](typography.md) | Punctuation, quotes, dashes, special characters | Recommended |
| [`banned-patterns.md`](banned-patterns.md) | Forbidden LLM phrases and clichés | Recommended |
| [`locale-de-AT.md`](locale-de-AT.md) | Austrian German adaptations | Optional |
| [`locale-de-CH.md`](locale-de-CH.md) | Swiss German adaptations | Optional |

### How to use / Anwendung

**Minimal setup** – copy `core.md` into your system prompt:

```
You are a helpful assistant.

<german_style>
{paste contents of core.md}
</german_style>
```

**Full setup** – combine the modules you need:

```
<german_style>
{core.md}
{typography.md}
{banned-patterns.md}
</german_style>
```

**With locale** – add one locale module for regional adaptation:

```
<german_style>
{core.md}
{typography.md}
{banned-patterns.md}
{locale-de-AT.md}
</german_style>
```

The modules are designed to be concatenated. Order doesn't matter, but `core.md` should come first for readability.

---

Die Module sind zum Aneinanderreihen gedacht. Die Reihenfolge spielt keine Rolle, aber `core.md` sollte der Lesbarkeit halber vorn stehen.

---

## Skills (Claude & ChatGPT)

For users who prefer a single drop-in file per locale, the [`skills/`](skills/) folder contains three pre-bundled skills (DE, AT, CH). Each `SKILL.md` is self-contained and works as a Claude Skill (with frontmatter), as a ChatGPT Custom GPT instruction, or as a system prompt for any other LLM.

| Skill | Audience |
|-------|----------|
| [`skills/german-style-de`](skills/german-style-de/SKILL.md) | Germany (de-DE) |
| [`skills/german-style-at`](skills/german-style-at/SKILL.md) | Austria (de-AT) |
| [`skills/german-style-ch`](skills/german-style-ch/SKILL.md) | Switzerland (de-CH) |

See [`skills/README.md`](skills/README.md) for installation instructions in Claude.ai, Claude Code, ChatGPT, Gemini, Mistral and local models.

---

Wer lieber eine einzige Drop-in-Datei pro Locale nutzt, findet im Ordner [`skills/`](skills/) drei vorgefertigte Skills (DE, AT, CH). Jede `SKILL.md` ist self-contained und funktioniert sowohl als Claude Skill (mit Frontmatter) als auch als ChatGPT-Custom-GPT-Instruction oder als System-Prompt für jedes andere LLM. Installationsanleitungen für Claude.ai, Claude Code, ChatGPT, Gemini, Mistral und lokale Modelle siehe [`skills/README.md`](skills/README.md).

---

## Contributing / Beitragen

Found a phrase that every LLM overuses in German? Open an issue or PR. The `banned-patterns.md` file is the easiest entry point.

For locale modules: if you're a native speaker of Austrian or Swiss German and spot inaccuracies, corrections are very welcome.

---

Du hast eine Phrase entdeckt, die jedes LLM im Deutschen überstrapaziert? Öffne ein Issue oder einen PR. Die Datei `banned-patterns.md` ist der einfachste Einstiegspunkt.

Für die Locale-Module: Wenn du Muttersprachler*in des österreichischen oder Schweizer Deutsch bist und Ungenauigkeiten findest, sind Korrekturen sehr willkommen.

---

## Changelog

### v1.2.0 – 2026-05-14

- *Neu:* Ordner [`skills/`](skills/) mit drei vorgefertigten, self-contained Skill-Paketen für Claude (Frontmatter-Format) und ChatGPT/Gemini/Mistral (Copy-Paste-System-Prompt): `german-style-de`, `german-style-at`, `german-style-ch`.
- *Neu:* [`skills/README.md`](skills/README.md) als Kurz-Doku (DE/EN) mit Installationsanleitungen für Claude.ai, Claude Code, ChatGPT (Custom GPT & Custom Instructions), Gemini, Mistral und lokale Modelle.
- *README:* Abschnitt „Skills (Claude & ChatGPT)" ergänzt.

### v1.1.0 – 2026-05-14

**`locale-de-CH.md`**

- *Wortschatz korrigiert:* „Handy → Natel" entschärft (Natel im aktiven Wortschatz im Rückgang), „Bitte / Danke → Merci" auf „Danke → Merci" reduziert (sachlich falsche Kombination), „Brötchen → Weggli / Brötli" auf „Brötchen (CH-Schriftsprache), regional Weggli" geändert.
- *Wortschatz erweitert:* Alltag (Depot, Anlass, Coiffeur, Lavabo, Abwaschmaschine, Tumbler, Fixleintuch, Kübel, Guetzli, Gipfeli, Glace, Rüebli, Randen, Poulet, Zucchetti), Verkehr (Occasion, Garagist, Garage, Perron), Sport (Penalty, Goalie).
- *Grammatik:* Fugen-e bei Komposita, Verb-Erststellung im uneingeleiteten Nebensatz, „bereits" am Satzanfang.
- *Orthografie:* Umlaute am Wortanfang in Eigennamen (Ae/Oe/Ue).

**`locale-de-AT.md`**

- *Wortschatz erweitert:* Essen (Faschiertes, Eierschwammerl, Fisolen, Karfiol, Kohlsprossen, Ribisel, Powidl, Weichsel, Vogerlsalat, Kren, Schlagobers, Beiried, Lungenbraten), Alltag (Mistkübel, Hausübungen, Schularbeit, Bankomat, Sessel, Gewand, Zündholz, Leiberl, Rauchfang, Rauchfangkehrer, Ordination, Primar), Verkehr (Bahnhofbuffet).
- *Grammatik:* „sich ausgehen", „gehören" + Partizip II, Genus-Abweichungen (das Cola, das E-Mail, das Joghurt).
- *Orthografie (neuer Abschnitt):* ß bleibt erhalten (Abgrenzung zur Schweiz), Datumsformat.
- *Anrede & Ton:* „Grüß Gott" als säkularer Standardgruß, „Mahlzeit" als kollegialer Tagesgruß.

### v1.0.0 – Initial release

Erstveröffentlichung mit `core.md`, `typography.md`, `banned-patterns.md`, `locale-de-AT.md`, `locale-de-CH.md`.

---

## License / Lizenz

[MIT](LICENSE)
