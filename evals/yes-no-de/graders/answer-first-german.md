---
type: llm
---

PASS if the answer is in German, its first sentence gives the answer (adding or removing keys during iteration raises a RuntimeError; changing values of existing keys works), and the whole answer is short: at most about 6 sentences plus an optional small code example.
FAIL if the answer is not in German, delays the answer behind background, or runs long.
