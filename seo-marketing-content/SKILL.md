---
name: marketing-content-writer
description: >
  Use this skill whenever the user wants to create SEO-optimized marketing content for websites or
  social media platforms based on a keyword or topic. Triggers include: "write marketing content",
  "create SEO content", "generate social media post", "write a blog post about [topic]",
  "content for [keyword]", "web content", "social content", "Instagram/Facebook/LinkedIn post",
  or any request to research a topic and turn it into polished marketing copy.
  Always use this skill when the user provides a keyword + a target platform (web or social).
  This skill searches the web for current content, summarizes insights, and produces
  publication-ready output tailored to SEO (for web) or engagement (for social).
---

# Marketing Content Writer

A skill that researches a keyword across the web, synthesizes top-ranking content, and produces
SEO-optimized web copy or social media posts — chosen by a simple `web` or `social` parameter.

---

## Workflow

### Step 1 – Clarify inputs (if not already provided)

Collect these before proceeding:

| Input | Description | Required |
|---|---|---|
| `keyword` | The topic or search term to research | YES |
| `platform` | `web` (SEO blog/article) or `social` (Instagram / Facebook / LinkedIn / Twitter) | YES |
| `social_channel` | Which social channel (only needed when platform = social) | If platform = social |
| `tone` | e.g. professional, casual, inspirational, urgent | Optional (default: professional) |
| `language` | Output language | Optional (default: English) |

If `keyword` and `platform` are missing, ask for them before starting.

---

### Step 2 – Web Research

Use `web_search` to gather current, authoritative content about the keyword.

**Search strategy:**
1. Primary search: `{keyword} guide 2024` or `{keyword} tips`
2. Competitor angle: `best {keyword}` or `{keyword} benefits`
3. For social: `{keyword} trending` or `{keyword} viral`

Run 3-5 searches to gather diverse perspectives. Use `web_fetch` on 2-3 top results for deeper content when snippets are insufficient.

**Extract and note:**
- Key themes, facts, statistics, unique angles
- Commonly used subheadings and structure patterns
- Gaps or angles competitors miss (differentiation opportunity)
- Relevant keywords and LSI terms (for SEO)

---

### Step 3 – Content Generation

Branch on `platform`:

#### If `platform = web` → SEO Article/Blog Post

Follow the SEO rules in `references/seo-rules.md`.

Output structure:
```
[SEO Title] – include primary keyword, under 60 chars
[Meta Description] – 150-160 chars, keyword + CTA
[H1] – matches or closely mirrors SEO title
[Introduction] – hook + keyword in first 100 words
[H2 sections] – 3-6 sections, each with keyword variations
[Conclusion + CTA] – summarize + action step
[Suggested Tags/Keywords] – 5-8 LSI terms
```

Word count targets:
- Short article: 600-800 words
- Standard blog: 1,000-1,500 words (default)
- Pillar page: 2,000+ words (only if user requests)

#### If `platform = social` → Social Media Post

Follow the channel rules in `references/social-rules.md`.

Channel defaults:

| Channel | Length | Style |
|---|---|---|
| Instagram | 150-300 words | Storytelling, emojis, hashtags |
| Facebook | 100-200 words | Conversational, question hook |
| LinkedIn | 200-400 words | Professional insight, no hard sell |
| Twitter/X | 280 chars max | Punchy, 1-2 hashtags |
| TikTok caption | 100-150 chars | Casual, trend-aware |

Always include:
- Hook in line 1 (stops the scroll)
- Call to action (CTA) near the end
- 3-10 relevant hashtags (Instagram: up to 10; LinkedIn: 3-5; Twitter: 1-2)

---

### Step 4 – Output Format

Present output in this order:

1. **Research Summary** (3-5 bullet points of key insights found)
2. **Generated Content** (clearly labeled, ready to copy-paste)
3. **Usage Tips** (1-3 quick notes: best posting time, A/B variation idea, etc.)

---

## Example Calls

### Example 1 – Web SEO Article

User prompt:
> Write web marketing content for keyword "matcha latte benefits"

Claude's process:
- Searches: "matcha latte benefits guide", "matcha latte health benefits", "matcha vs coffee"
- Fetches top 2 articles for depth
- Produces: SEO title, meta description, 1,200-word blog post with H2s, CTA, keyword list

---

### Example 2 – Instagram Post

User prompt:
> Create social content for keyword "sustainable fashion tips", platform: social, channel: Instagram, tone: inspirational

Claude's process:
- Searches: "sustainable fashion tips trending", "eco fashion viral posts"
- Produces: scroll-stopping hook, 200-word caption, 8 hashtags, CTA

---

### Example 3 – LinkedIn Post

User prompt:
> Keyword: "AI in healthcare", platform: social, channel: LinkedIn

Claude's process:
- Searches for recent developments, stats, executive perspectives
- Produces: thought-leadership post with data point hook, 3 insights, soft CTA, 4 hashtags

---

## Quality Checklist (run before presenting output)

**SEO (web):**
- [ ] Primary keyword in title, H1, first paragraph, at least 2 H2s
- [ ] Meta description is 150-160 chars and contains keyword
- [ ] No keyword stuffing (density ~1-2%)
- [ ] Includes internal link suggestion and at least 1 external authority link mention
- [ ] Readability: short sentences, active voice, no jargon walls

**Social:**
- [ ] Hook is in the first line (no "In today's world..." openers)
- [ ] CTA is specific ("Comment below", "Save this post", "Click the link in bio")
- [ ] Hashtags are relevant (not just popular)
- [ ] Fits character/word limit for channel
- [ ] Emojis used purposefully (not excessively)

---

## Reference Files

- `references/seo-rules.md` — Detailed SEO writing rules, on-page checklist, keyword placement guide
- `references/social-rules.md` — Per-channel social media rules, hook formulas, hashtag strategy