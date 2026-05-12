# AI Skills — Repository README

## What Are AI Skills?

AI Skills are structured instruction sets that extend Claude's capabilities for specific, repeatable tasks. Each skill is a plain-text file (or folder of files) that tells Claude *exactly* how to approach a particular job — what steps to follow, what rules to apply, what output format to produce, and how to handle edge cases.

Think of a skill as a reusable standard operating procedure. Rather than re-explaining your requirements every time you want a blog post written or a spreadsheet reformatted, you load a skill once and Claude follows its logic automatically, consistently, every time.

Skills are not plugins or code executed at runtime. They are **prompting blueprints** — human-readable documents that shape Claude's reasoning and output within a conversation or automated pipeline.

---

## What Skills Are in This Repo?

This repository contains a library of ready-to-use skills across common work categories:

| Skill | What It Does |
|---|---|
| `docx` | Creates, edits, and formats Microsoft Word documents (.docx) |
| `pdf` | Reads, creates, merges, splits, and processes PDF files |
| `pdf-reading` | Extracts and analyzes content from existing PDF files |
| `pptx` | Builds and edits PowerPoint presentation decks (.pptx) |
| `xlsx` | Creates and manipulates Excel spreadsheets (.xlsx) |
| `frontend-design` | Generates production-grade web UIs, components, and layouts |
| `file-reading` | Routes any uploaded file type to the correct reading strategy |
| `product-self-knowledge` | Keeps Claude accurate on Anthropic product facts and pricing |
| `seo-marketing-content` | Researches topics and writes SEO-optimized web and social content |

Each skill lives in its own folder and contains at minimum a `SKILL.md` — the core instruction file. Some skills include additional reference files, scripts, or format guides in subfolders.

---

## How Skills Work

### The Core File: `SKILL.md`

Every skill is anchored by a `SKILL.md` file. It contains:

- **Frontmatter** — a `name` and `description` field that tells Claude *when* to use the skill
- **Workflow steps** — ordered instructions Claude follows to complete the task
- **Rules and constraints** — quality standards, output formats, and error handling
- **Output templates** — exactly how the final result should be structured

### Reference Files

Complex skills include supporting reference documents inside the skill folder. For example, the `seo-marketing-content` skill has:

```
seo-marketing-content/
├── SKILL.md                          # Core instructions
└── references/
    ├── web-seo-rules.md              # SEO formatting standards
    ├── social-platform-rules.md      # Per-platform social media rules
    └── content-types.md              # Format guide by content type
```

Claude reads these reference files as part of executing the skill, keeping the main `SKILL.md` concise while supporting deeper specialization.

---

## How to Use a Skill

### In Claude.ai (Chat Interface)

1. Copy the contents of the relevant `SKILL.md` (and any reference files, if the skill uses them) into your conversation, or attach the files directly.
2. Make your request as you normally would.
3. Claude will follow the skill's workflow to produce the output.

**Example:**
> *[Paste contents of `seo-marketing-content/SKILL.md`]*
> "Write an SEO blog post for the keyword: sustainable home office furniture."

### In a System Prompt (API / Automated Pipelines)

For consistent, repeatable use — such as in a product, workflow, or API integration — paste the skill content directly into your **system prompt**. This means every conversation automatically inherits the skill's behavior without any manual loading.

```
System prompt:
[Paste full SKILL.md content here]

User message:
Write an SEO article about ergonomic standing desks.
```

### With the `available_skills` Block (Claude Computer Use / Operator Setups)

In operator environments where Claude has file system access, skills can be mounted at a known path (e.g., `/mnt/skills/`) and declared in an `<available_skills>` block in the system prompt. Claude will read the relevant `SKILL.md` at task time rather than requiring it to be pasted inline.

```xml
<available_skills>
  <skill>
    <name>seo-marketing-content</name>
    <description>Use when writing SEO articles or social media content from a keyword.</description>
    <location>/mnt/skills/seo-marketing-content/SKILL.md</location>
  </skill>
</available_skills>
```

Claude checks this list before responding to relevant requests, reads the skill file, and applies it automatically.

---

## How to Create a New Skill

A skill is just a well-structured Markdown file. Follow this template:

```markdown
---
name: your-skill-name
description: >
  One or two sentences explaining what this skill does and when Claude
  should use it. Be specific — this is what triggers skill selection.
---

# Your Skill Name

Brief summary of the skill's purpose.

## Step 1: Parse Inputs
What information Claude should extract from the user's request.

## Step 2: [Core Workflow]
Ordered steps Claude should follow.

## Step 3: Generate Output

**Output format:**
\```
[Show exactly what the output should look like]
\```

## Quality Rules
- Rule 1
- Rule 2

## Error Handling
- If X happens, do Y.
```

**Tips for writing effective skills:**

- **Be explicit, not implicit.** Don't assume Claude will infer steps — write them out.
- **Include output templates.** Show Claude the exact format you want, with examples.
- **Write a sharp description.** The `description` field is what determines whether Claude triggers the skill correctly. Make it specific and use trigger phrases your users are likely to say.
- **Add reference files for complexity.** If a skill has many sub-rules (e.g., different rules per platform or file type), move those details into a `references/` subfolder to keep `SKILL.md` readable.
- **Include error handling.** Anticipate edge cases — missing inputs, ambiguous requests, failed lookups — and tell Claude what to do.

---

## Folder Structure Convention

```
skills/
├── your-skill-name/
│   ├── SKILL.md               # Required — core instructions
│   ├── LICENSE.txt            # Optional — usage terms
│   └── references/            # Optional — supporting rule files
│       ├── rules-part-a.md
│       └── rules-part-b.md
```

Keep one skill per folder. Use lowercase, hyphenated folder names matching the `name` field in the frontmatter.

---

## License

Individual skills may carry their own license terms in a `LICENSE.txt` file within the skill folder. Check each skill's folder before redistributing or modifying.
