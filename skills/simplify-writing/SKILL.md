---
name: simplify-writing
description: Use when the user asks to simplify, make clearer, make plainer, reduce jargon, shorten without changing meaning, rewrite for clarity, explain in simpler terms, or clean up confusing text. Handles faithful, context-aware simplification for pasted text, docs, comments, messages, and explanations. Not for general editing, persuasion, expansion, tone-only rewriting, or copyediting unless simplification is the main goal.
disable-model-invocation: false
---

# Simplify

Rewrite content in clearer, simpler language while preserving the original meaning, key details, intent, and useful structure.

## Trigger Boundary

Use this skill for requests like:

- "simplify this"
- "make this clearer"
- "make this plainer"
- "reduce the jargon"
- "shorten this without changing the meaning"
- "rewrite for clarity"
- "explain this in simpler terms"
- "clean up this confusing text"

Do not use it for general editing, persuasion, expansion, tone-only rewriting, grammar-only copyediting, or full creative rewrites unless simplification is the main goal.

## Workflow

1. Identify the content to simplify, the requested output format, the intended audience, and any constraints the user gave. If no audience is specified, write for a plain adult reader using clear everyday language, roughly high-school level, without making the result childlike.
2. Be context-aware but restrained. Use supplied or obvious local context when the user provides files, paths, uploads, or surrounding task context. Use web search only for current, external, specialized, or named references that materially affect meaning. For ordinary pasted text, simplify directly with no search.
3. Treat supporting context as clarification, not permission to expand the source. Do not add new claims unless they are directly supported by the original content or verified context.
4. Preserve the original tone by default. If the source is casual, formal, urgent, technical, warm, or blunt, keep that feel while making it clearer. Normalize the tone only when the user asks or when the original tone makes the content harder to understand.
5. Preserve structure when it carries meaning. Keep headings, lists, numbered steps, tables, code identifiers, commands, quoted text, and required formatting unless the user asks to restructure. If the original format is messy, clean it up without changing the meaning.
6. Preserve syntax exactly unless the user explicitly asks to rewrite it. Simplify surrounding prose, comments, docstrings, labels, and explanations, but do not change executable code, commands, JSON/YAML keys, API names, identifiers, quoted strings, or required formatting if that could alter behavior or meaning.
7. Explain technical terms only when needed for clarity. Keep required terms, and add a short parenthetical or brief phrase when a reader would otherwise be stuck. Do not turn the answer into a glossary or tutorial unless requested.
8. Handle ambiguity as best-effort unless ambiguity would change meaning. If a phrase is unclear but the rest can be simplified, simplify what is clear and add `## Ambiguities`. Generate a `## Clarifying Questions` section only when the unclear part is central enough that simplifying would likely distort the meaning.
9. Return text in chat by default. Edit a source file only when the user explicitly asks to simplify, rewrite, or apply changes to that file.

## Output

Default to this format:

```markdown
## Simplified Version
[Simplified text]

## Context Used
[Context note]
```

Add this section only when non-blocking ambiguity remains:

```markdown
## Ambiguities
- [Brief note]
```

If clarification is required before a faithful simplification, use:

```markdown
## Clarifying Questions
1. [Question]

## Context Checked
[Context checked, if any]
```

Honor explicit user format requests. If the user asks for bullets, email copy, a one-liner, inline edits, JSON, or just the simplified text, use that format instead of the default sections.

## Context Reporting

In `## Context Used`, be specific enough to audit:

- For local context, list file paths or document names.
- For web context, list URLs or source names.
- For conversation-only context, write `Conversation context only.`
- If no external, local, or conversation context affected the rewrite, write `No additional context used.`

If outside context changes or qualifies the meaning of the original content, explain that briefly before the simplified version.
