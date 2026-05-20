---
name: ai-writing-audit
description: Audit and correct text to remove signs of AI-generated writing. Use when reviewing any written content (marketing copy, articles, documentation, social posts) to identify and remove patterns that signal LLM generation. Triggers include requests to "make this sound less AI," "humanize this," "remove AI tells," "audit for AI patterns," "make this sound more natural," or any review of drafted content before publication.
---

# AI Writing Audit & Correction

Identify and remove patterns that signal AI-generated text, based on Wikipedia's "Signs of AI Writing" detection guide. Rewrites follow Descript brand voice: human, realistic, subversive.

## Two-Phase Workflow

Complete AUDIT fully before starting REWRITE. Do not skip phases.

### Phase 1: Audit

1. Read draft once, slowly.
2. Work through checklist in `references/checklist.md` in exact order.
3. For each offense:
   - Quote shortest offending snippet (≤12 words)
   - Append all applicable `[TAGS]`
   - One numbered line per offense; stack tags if multiple tells in one sentence
4. After last offense: `— END AUDIT: [n] issues found —`
5. If zero issues: `— AUDIT COMPLETE: 0 issues —` and skip Phase 2.

**Severity suffixes** (append when applicable):
- `+H` = high severity (strong tell or compounded patterns)
- `+S` = structural (affects document structure, not just wording)

### Phase 2: Rewrite

Before rewriting, load `references/descript-voice.md` for brand voice guidance.

**Core rewrite principles:**

1. Output complete corrected text with all flagged issues fixed.
2. Preserve everything not flagged—no new edits.
3. Do not add new content, claims, or citations.
4. Maintain original meaning and factual content.

**Descript voice filter (apply to all rewrites):**

- Write like you talk, not like a brand
- Say it like it really is, no faux enthusiasm or positive spin
- Be conversational and casual
- Favor the surprising, uncomfortable, or inobvious angle
- Never be presumptuous about reader's feelings or relationship with product
- Kill anything that sounds like a SaaS company or marketing copy
- Ask: "Would you least expect a brand to say this?" If no, rewrite again.

**Fix principles by tag type:**

| Tags | Action |
|------|--------|
| `[INFLATED]` `[SYMBOLISM]` `[PROMO]` | Delete puffery or replace with specific fact. No fact? Cut entirely. Avoid replacing with different puffery. |
| `[SUPERFICIAL-ING]` | Remove -ing phrase or convert to separate sentence with substance. |
| `[AI-LEX]` | Replace with plainer word you'd actually say out loud. |
| `[NOT-ONLY-BUT]` `[RULE-OF-3]` | Break parallelism; vary structure; state directly. |
| `[ELEGANT-VAR]` | Pick one term consistently, or use pronouns. |
| `[VAGUE-ATTR]` `[WEASEL]` | Name source specifically, add quantifier, or delete claim. |
| `[CHALLENGES-FUTURE]` | Restructure or cut; do not preserve formula. Be honest about difficulty without false hope. |
| `[EM-DASH]` | Replace with comma, colon, or parentheses. |
| `[INLINE-BOLD]` `[INLINE-LIST]` `[TITLE-CASE]` | Remove excess formatting; sentence case for headings. |
| `[DIRECT-ADDRESS]` `[COLLAB]` `[LETTER-FORMAT]` `[REFUSAL]` `[KNOWLEDGE-CUTOFF]` | Delete entirely. |
| `[OAICITE]` `[MARKDOWN]` `[PLACEHOLDER]` `[REF-BUG]` | Remove artifacts; fix or flag citations for human review. |

**Voice check (run after rewrite):**

Flag if any rewritten passage:
- Sounds like it's trying to make someone feel fake-good
- Uses "masterpiece," "unlock," "elevate," "empower," or similar
- Promises creative success or implies linear path to greatness
- Sounds like a brand trying to be your friend
- Could appear in any other SaaS company's marketing

## Output Format

```
## AUDIT

1. "quoted snippet" [TAG] [TAG +H]
2. "quoted snippet" [TAG]
...

— END AUDIT: [n] issues found —

## CORRECTED TEXT

[Full corrected text]

## CHANGELOG

• Location: brief description of change
• Location: brief description of change
...

## VOICE CHECK

[Note any remaining voice concerns, or "Passes voice check"]
```

CHANGELOG: one terse line per fix, referencing original snippet or location.

## References

- `references/checklist.md` — AI detection tags and patterns
- `references/descript-voice.md` — Brand voice guidelines for rewrites
