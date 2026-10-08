# glance

AI output that humans understand at a glance.

Models now do more of the work, so people spend more of their time reading, checking, and
supervising what the model produced. Walls of text are the slowest format for that. glance makes
the model pick the fastest format for each answer: short plain text, a diagram, or an HTML page.

## What changes

```text
answer ready
     │
     ▼
┌──────────────┐  one fact, short answer     ┌──────────────────────────────┐
│ choose the   ├────────────────────────────►│ text: answer first,          │
│ format       │                             │ short plain sentences        │
│              │  flow, structure, sequence  ├──────────────────────────────┤
│              ├────────────────────────────►│ diagram in the chat          │
│              │                             │ (Unicode, renders anywhere)  │
│              │  report, plan, comparison   ├──────────────────────────────┤
│              ├────────────────────────────►│ HTML page + 2-4 line summary │
└──────────────┘                             └──────────────────────────────┘
     │
     ▼
Deeper: 1 <specific direction> · 2 <specific direction> · 3 <specific direction>
```

- **Text:** the answer comes first. Short, complete sentences in plain words. No preamble, no recap,
  no filler. Unlike pure compression styles, glance keeps sentences whole, so the reader never has
  to reconstruct missing words.
- **Diagrams:** flows, architectures, and hierarchies are drawn, not described. In a terminal glance
  draws with Unicode box characters, because raw Mermaid code is not a picture.
- **HTML pages:** reports, reviews, plans, and comparisons become one self-contained page (light and
  dark mode, readable on a phone). If your environment can publish pages (for example artifacts),
  glance uses that. Otherwise it writes the file to your temp directory, never into your project.
- **Go deeper:** larger answers end with two to four directions that are specific to the answer.
  Run `/glance:deeper 2` or `/glance:deeper <topic>` to expand exactly one of them.

glance changes what you read, not how the model works. Coding behavior, testing, and commit
messages stay as they are. Security warnings, error output, and confirmations before destructive
actions are always written in full.

## Example

Question: *"How does our login flow work?"*

Without glance, a typical answer is six paragraphs. With glance:

````text
Login uses a session cookie, issued after the password check in `auth/login.ts`.

```text
browser ──POST /login──► login.ts ──verify──► users table
   ▲                        │
   └──Set-Cookie: sid───────┘  session stored in Redis, 7 days
```

Deeper: 1 Why sessions and not JWT · 2 What happens on expiry · 3 Brute-force protection
````

## Install

Claude Code:

```bash
claude plugin marketplace add MerlinO05/glance
claude plugin install glance@glance
```

Restart Claude Code. glance is active right away: it ships as an output style that turns on when
the plugin is enabled. It replaces any output style you selected while it is enabled.

To turn it off:

```bash
claude plugin disable glance
```

## Language

The rules are written in English. The model answers in the language you write in.

## Evaluate it yourself

The repository contains an eval suite. It runs each case with and without the plugin and reports
the score difference:

```bash
claude plugin eval ./
```

Result of the last run (11 cases, 3 runs per case and arm, Claude Sonnet as model and judge,
2026-10-08):

| | with glance | without | Δ |
|---|---|---|---|
| Mean score | 0.96 | 0.55 | +0.41 |
| Cases at or above 0.8 | 11 / 11 | 2 / 11 | |

The biggest gains are diagrams for flows (+0.67) and HTML pages for reports and plans (+0.73 to
+1.00). No case scored lower with glance than without it. LLM-judged scores vary between runs, so
treat single numbers as indicative.

## Scope

- Version 0.1 targets Claude Code.
- Explanatory videos are out of scope. The model makes one only if you ask.
- Output styles apply to the main conversation. Subagents keep their own instructions, which is
  fine: their output goes to the model, not to you.

## License

MIT
