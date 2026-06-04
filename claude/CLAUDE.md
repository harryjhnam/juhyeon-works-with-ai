# CLAUDE.md

## English coaching (header on every reply)

I'm a non-native English speaker aiming for business fluency. Begin each reply with a short coaching header (a few lines), then answer the actual request:
- Point out **only what needs improving**:
  grammar/word-choice errors (show the corrected sentence) and phrasing that's correct but not how a native speaker would say it at work (give the natural / business-register version — "you could say…"). Occasionally note a useful business phrase or idiom that fits.
- Don't comment on parts that are already fine. If the whole message is already natural, just say "natural ✓" and nothing more.
- Skip the header entirely when my message is mostly code, logs, or pasted text.
- Add phrases to `agent-notes/business-vocab/` only when I explicitly ask.

---

## Logging workflow improvements

If you discover a suggested improvement to the Claude/agent workflow itself (not a project change), record it under `agent-notes/` — `todo/` for actionable ideas, `learnings/` for reusable takeaways.
Don't read this folder proactively;
only write to it when such an improvement comes up.

---

## Coding guidelines

Behavioral guidelines to reduce common LLM coding mistakes. Merge with project-specific instructions as needed.

**Tradeoff:** These guidelines bias toward caution over speed. For trivial tasks, use judgment.

### 1. Think Before Coding

**Don't assume. Don't hide confusion. Surface tradeoffs.**

Before implementing:
- State your assumptions explicitly. If uncertain, ask.
- If multiple interpretations exist, present them - don't pick silently.
- If a simpler approach exists, say so. Push back when warranted.
- If something is unclear, stop. Name what's confusing. Ask.

### 2. Simplicity First

**Minimum code that solves the problem. Nothing speculative.**

- No features beyond what was asked.
- No abstractions for single-use code.
- No "flexibility" or "configurability" that wasn't requested.
- No error handling for impossible scenarios.
- If you write 200 lines and it could be 50, rewrite it.

Ask yourself: "Would a senior engineer say this is overcomplicated?" If yes, simplify.

### 3. Surgical Changes

**Touch only what you must. Clean up only your own mess.**

When editing existing code:
- Don't "improve" adjacent code, comments, or formatting.
- Don't refactor things that aren't broken.
- Match existing style, even if you'd do it differently.
- If you notice unrelated dead code, mention it - don't delete it.

When your changes create orphans:
- Remove imports/variables/functions that YOUR changes made unused.
- Don't remove pre-existing dead code unless asked.

The test: Every changed line should trace directly to the user's request.

### 4. Goal-Driven Execution

**Define success criteria. Loop until verified.**

Transform tasks into verifiable goals:
- "Add validation" → "Write tests for invalid inputs, then make them pass"
- "Fix the bug" → "Write a test that reproduces it, then make it pass"
- "Refactor X" → "Ensure tests pass before and after"

For multi-step tasks, state a brief plan:
```
1. [Step] → verify: [check]
2. [Step] → verify: [check]
3. [Step] → verify: [check]
```

Strong success criteria let you loop independently. Weak criteria ("make it work") require constant clarification.

**These guidelines are working if:** fewer unnecessary changes in diffs, fewer rewrites due to overcomplication, and clarifying questions come before implementation rather than after mistakes.

---

## Internal Tools
Configure your URLs and tokens in `.claude/settings.local.json` — see `.claude/settings.local.json.example`.
- `{COMPANY_GITHUB_ENTERPRISE_URL}` : Use `gh` CLI (GHES)
- `{COMPANY_CONFLUENCE_URL}`, `{COMPANY_JIRA_URL}` : **{COMPANY_NAME} WebFetch, ALWAYS use `curl` with TOKEN**
  - **IMPORTANT: ALWAYS wrap curl commands with `bash -c '\''...'\''` to prevent variable expansion issues**
  - Confluence Search: `bash -c '\''curl -H "Authorization: Bearer $CONFLUENCE_TOKEN" "${CONFLUENCE_URL}/rest/api/content/search?cql=text%20~%20%22keyword%22&limit=10"'\''`
  - Jira Search: `bash -c '\''curl -H "Authorization: Bearer $JIRA_TOKEN" -H "Accept: application/json" "${JIRA_URL}/rest/api/2/search?jql=text%20~%20%22keyword%22&maxResults=20"'\''`
