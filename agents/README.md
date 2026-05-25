# Agent Prompts

Three LLM system prompts for different review tasks. Each file contains a prompt you paste as the system message, followed by pasting the paper content.

---

## Usage

1. Open your LLM interface (Claude, GPT-4o, Gemini, etc.).
2. Set the system prompt from the agent file.
3. Paste the paper text (or section) as the user message.
4. Review the structured output against the relevant checklists in `docs/`.

---

## Agent Overview

| Agent | Input | Output |
|---|---|---|
| [full-paper-review.md](full-paper-review.md) | Full manuscript (text or PDF-extracted) | CRITICAL / MAJOR / MINOR issues, top 3 problems, venue recommendation |
| [statistical-audit.md](statistical-audit.md) | Methods, results, and statistics sections | Numbered issues: Found / Problem / Fix |
| [venue-fit.md](venue-fit.md) | Abstract + paper summary | Venue scores (0–10), top 3 recommendations, rejection risks |

---

## Notes

- Run `full-paper-review.md` first to identify structural issues.
- Run `statistical-audit.md` on any paper that uses quantitative methods.
- Run `venue-fit.md` when the target venue is uncertain or when the paper has been rejected and needs re-routing.
- Fix CRITICAL issues before venue-specific checks.
