---
name: seo-marketing-content
description: >
  Use this skill to generate SEO-optimized marketing content for websites or social media platforms based on a keyword input. Trigger this skill whenever the user wants to: research a topic online and turn it into marketing content, write blog posts or web pages with SEO structure, create social media captions or posts from keyword research, generate content briefs from web-researched summaries, or produce platform-specific content (Instagram, Facebook, LinkedIn, TikTok, Twitter/X). Always use this skill when the user provides a keyword and wants content written for "web" or "social" output. Also trigger when user says things like "write me content for my website about [topic]", "create social media posts for [keyword]", "research and write marketing content about [topic]", "SEO article for [keyword]", or "generate content for [platform] based on [keyword]".
---

# SEO Marketing Content Skill

Generate research-backed, SEO-optimized marketing content for web or social platforms from a single keyword input.

---

## Workflow Overview

1. **Receive inputs** — keyword + output type (`web` or `social` + platform)
2. **Web research** — search for top-ranking content, competitors, trends
3. **Summarize findings** — extract key themes, angles, LSI keywords
4. **Generate content** — apply SEO rules or social best practices per platform

---

## Step 1: Parse User Inputs

Identify from the user's message:
- **Keyword**: the main topic/keyword (e.g., "organic skincare for sensitive skin")
- **Output type**: `web` or `social`
- **Platform** (if social): instagram / facebook / linkedin / tiktok / twitter / x
- **Language/locale** (if specified, default: English)
- **Tone** (if specified, default: professional but approachable)

If output type is missing, ask: *"Should I create this for a website (SEO article/landing page) or social media? If social, which platform?"*

---

## Step 2: Web Research

Run **3–5 web searches** to gather competitive intelligence:

```
Search queries to run (adapt to keyword):
1. "[keyword]" — top-ranking pages
2. "[keyword] tips / guide / benefits" — content angles
3. "[keyword] [current year]" — fresh/trending content
4. "best [keyword] [niche]" — listicle/comparison angles (optional)
5. "[keyword] site:reddit.com OR site:quora.com" — audience pain points (optional)
```

For each result, **extract**:
- Key themes and subtopics covered
- Commonly used headings (H2/H3 patterns)
- Notable statistics or data points (paraphrase, do NOT quote verbatim)
- Audience questions and pain points
- LSI (Latent Semantic Indexing) keywords — related terms that appear frequently

Compile a **Research Summary** (internal, not shown to user unless asked):
- Top 3–5 content angles
- 8–15 LSI/related keywords
- Key facts and insights (paraphrased)
- Content gaps (what competitors miss)

---

## Step 3: Generate Content

Branch based on output type:

### → If `web`

Read: `references/web-seo-rules.md` for full SEO formatting rules.

**Quick checklist:**
- [ ] SEO title (50–60 chars, keyword near front)
- [ ] Meta description (150–160 chars, includes keyword + CTA)
- [ ] H1 with primary keyword
- [ ] Introduction with keyword in first 100 words, hook, preview of content
- [ ] H2/H3 structure covering subtopics (use LSI keywords in headings)
- [ ] Body: 800–2000 words depending on topic complexity
- [ ] Include stats, examples, or lists for scannability
- [ ] Internal link placeholders: [Link: related topic]
- [ ] CTA section at end
- [ ] FAQ section (3–5 questions based on "People Also Ask" style)
- [ ] Keyword density: ~1–2% (natural usage, not stuffed)

**Output format:**
```
📄 SEO TITLE: ...
📝 META DESCRIPTION: ...
---
[Full article content with H1, H2, H3, body, FAQ, CTA]
---
🔑 TARGET KEYWORDS USED: [list]
📊 WORD COUNT: ~XXX words
```

---

### → If `social`

Read: `references/social-platform-rules.md` for platform-specific rules.

**Quick reference by platform:**

| Platform | Length | Format | Hashtags | Tone |
|----------|--------|--------|----------|------|
| Instagram | 138–150 chars (caption) | Hook + value + CTA | 5–10 | Inspiring, visual |
| Facebook | 40–80 chars optimal | Short + conversational | 1–2 | Friendly, community |
| LinkedIn | 150–300 chars or long-form 1200–1500 | Professional insight | 3–5 | Thought leadership |
| Twitter/X | ≤280 chars | Punchy, engaging | 1–2 | Witty or direct |
| TikTok | Video script: 150–300 words | Hook (0–3s) + body + CTA | 3–7 | Energetic, Gen-Z friendly |

**Output format for social:**
```
📱 PLATFORM: [name]
---
✍️ POST COPY:
[Post content]

#️⃣ HASHTAGS: [hashtags]

🎯 CTA: [Call to action]

💡 POSTING TIP: [Best time/format tip for this platform]
```

For TikTok, output a **video script** with:
- Hook (first 3 seconds)
- Main content points
- CTA / ending

---

## Step 4: Output & Offer Variations

After the main content:
1. **Offer a variation**: "Want a different angle or tone? I can write a [more casual / more authoritative / shorter] version."
2. **Offer cross-format**: "Should I also create social posts from this web article?" (or vice versa)
3. **Offer keyword list**: "Want the full LSI keyword list for more content ideas?"

---

## Quality Rules (Always Apply)

- **Never plagiarize**: All content must be original. Paraphrase research findings. No direct quotes from sources.
- **Natural keyword use**: Keywords flow naturally — no keyword stuffing.
- **Audience-first**: Content must provide genuine value, not just rank.
- **Accuracy**: Do not invent statistics. If no data found, use general language or omit.
- **Brand-neutral**: Unless the user specifies a brand/product, keep content generic and adaptable.

---

## Error Handling

- **No search results**: If web search returns nothing useful, inform the user and generate content from Claude's internal knowledge, noting it isn't research-backed.
- **Ambiguous keyword**: If keyword is too broad (e.g., "shoes"), ask for a narrower focus or niche.
- **Conflicting platform**: If user says "social" but no platform, default to **Instagram** and note the assumption.
