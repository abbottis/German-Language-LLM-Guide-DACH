# Skills – German Style for Claude & ChatGPT

Drei vorgefertigte Skill-Pakete als Drop-in-Lösung. Jede Skill bündelt alle relevanten Module (Kernregeln, Typografie, verbotene Muster und – falls vorhanden – das Locale-Modul) in einer einzigen `SKILL.md`-Datei. Das Format folgt der Claude-Skills-Konvention (Frontmatter mit `name` und `description`), funktioniert aber ebenso als Copy-Paste-Systemprompt für ChatGPT, Gemini, Mistral und andere LLMs.

Three ready-made skill packages as a drop-in solution. Each skill bundles all relevant modules (core rules, typography, banned patterns and – if applicable – the locale module) into a single `SKILL.md` file. The format follows the Claude Skills convention (frontmatter with `name` and `description`), but works equally well as a copy-paste system prompt for ChatGPT, Gemini, Mistral and other LLMs.

---

## Verfügbare Skills / Available Skills

| Skill | Sprache / Language | Zielpublikum / Target Audience |
|-------|---------------------|--------------------------------|
| [`german-style-de`](german-style-de/SKILL.md) | Deutsch (Deutschland) | Bundesdeutsches Hochdeutsch (de-DE) |
| [`german-style-at`](german-style-at/SKILL.md) | Deutsch (Österreich) | Österreichisches Deutsch (de-AT) |
| [`german-style-ch`](german-style-ch/SKILL.md) | Deutsch (Schweiz) | Schweizer Hochdeutsch (de-CH) |

---

## Verwendung in Claude / Use with Claude

### Claude.ai (Web / Desktop)

**DE:**
1. Öffne **Settings → Capabilities → Skills**.
2. Klicke auf **„Create skill"** und lade die gewünschte `SKILL.md` hoch (oder kopiere den Inhalt hinein).
3. Aktiviere die Skill in deinem Projekt oder Chat.
4. Claude erkennt automatisch über die `description` im Frontmatter, wann die Skill anzuwenden ist.

**EN:**
1. Open **Settings → Capabilities → Skills**.
2. Click **"Create skill"** and upload the desired `SKILL.md` (or paste the content).
3. Enable the skill in your project or chat.
4. Claude automatically detects when to apply the skill based on the `description` field in the frontmatter.

### Claude Code (CLI)

**DE:** Lege die gewünschte Skill-Mappe in `~/.claude/skills/` (global) oder `<projekt>/.claude/skills/` (projektweit) ab:

**EN:** Place the desired skill folder in `~/.claude/skills/` (global) or `<project>/.claude/skills/` (project-wide):

```bash
cp -r skills/german-style-at ~/.claude/skills/
```

Claude Code lädt die Skill automatisch, sobald die `description` zur Anfrage passt.
Claude Code automatically loads the skill as soon as the `description` matches the request.

---

## Verwendung in ChatGPT / Use with ChatGPT

### Custom GPT (empfohlen / recommended)

**DE:**
1. Öffne **Explore GPTs → Create**.
2. Im Tab **Configure** → Feld **Instructions**: gesamten Inhalt der `SKILL.md` einfügen (Frontmatter inklusive ist unproblematisch, kann aber auch entfernt werden).
3. Speichern. Der Custom GPT wendet den Stil bei jeder Antwort an.

**EN:**
1. Open **Explore GPTs → Create**.
2. In the **Configure** tab → field **Instructions**: paste the full content of the `SKILL.md` (frontmatter is harmless, but can be removed).
3. Save. The Custom GPT applies the style to every response.

### Standard ChatGPT (Custom Instructions)

**DE:**
1. **Settings → Personalization → Custom Instructions**.
2. Im Feld **„How would you like ChatGPT to respond?"** den Inhalt der `SKILL.md` einfügen (Frontmatter optional weglassen).
3. Speichern.

**EN:**
1. **Settings → Personalization → Custom Instructions**.
2. In the **"How would you like ChatGPT to respond?"** field, paste the content of the `SKILL.md` (frontmatter optional).
3. Save.

---

## Verwendung in anderen LLMs / Use with other LLMs

**DE:** Die Skill-Datei ist ein normaler Markdown-Text. Nutze sie als System-Prompt in:
- **Gemini**: System Instructions im API-Call oder in Gemini Gems.
- **Mistral / Mixtral**: System message im API-Call.
- **Llama / lokale Modelle**: System prompt der Inferenz-Engine (Ollama, llama.cpp, LM Studio).

Die Frontmatter (zwischen den `---`) kann bei Nicht-Claude-Systemen entfernt werden, schadet aber nicht, wenn sie bleibt.

**EN:** The skill file is plain Markdown. Use it as a system prompt in:
- **Gemini**: System instructions in the API call or in Gemini Gems.
- **Mistral / Mixtral**: System message in the API call.
- **Llama / local models**: System prompt of the inference engine (Ollama, llama.cpp, LM Studio).

The frontmatter (between the `---`) can be removed for non-Claude systems, but causes no harm if left in place.

---

## Welche Skill für welchen Fall? / Which skill for which case?

**DE:**
- **Zielpublikum Deutschland** → `german-style-de`
- **Zielpublikum Österreich** → `german-style-at` (enthält Wortschatz, Grammatik und Anrede für AT)
- **Zielpublikum Schweiz** → `german-style-ch` (kein ß, Guillemets «», Apostroph als Tausendertrennzeichen, Helvetismen)
- **DACH-übergreifend** → Im Zweifel `german-style-de` als Basis und im Prompt explizit auf neutrale Formulierungen hinweisen. Eine eigene DACH-Skill ist nicht sinnvoll, weil sich die Orthografie (ß vs. ss) zwischen den Ländern direkt widerspricht.

**EN:**
- **Audience Germany** → `german-style-de`
- **Audience Austria** → `german-style-at` (includes vocabulary, grammar and salutations for AT)
- **Audience Switzerland** → `german-style-ch` (no ß, guillemets «», apostrophe as thousands separator, Helvetisms)
- **Cross-DACH** → When in doubt, use `german-style-de` as a baseline and explicitly request neutral wording in the prompt. A dedicated DACH skill is not meaningful because the orthography (ß vs. ss) contradicts directly between countries.

---

## Verhältnis zu den Modul-Dateien / Relationship to the module files

**DE:** Die Skill-Pakete sind self-contained – sie kopieren den Inhalt der Module (`core.md`, `typography.md`, `banned-patterns.md`, `locale-de-AT.md`, `locale-de-CH.md`) in eine einzige Datei. Wer die Module lieber selbst zusammenstellen möchte (z. B. um nur Teile zu nutzen), arbeitet weiterhin direkt mit den Modulen im Repo-Root.

**EN:** The skill packages are self-contained – they copy the content of the modules (`core.md`, `typography.md`, `banned-patterns.md`, `locale-de-AT.md`, `locale-de-CH.md`) into a single file. Anyone preferring to assemble the modules manually (e.g. to use only parts) continues to work with the modules in the repository root.
