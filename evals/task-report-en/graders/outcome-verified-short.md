---
type: llm
---
PASS if the final chat message states the outcome in its first sentence (the file exists and works), says how it was verified (that the script was run and what the output showed), and has at most about 8 lines of text (blank lines and code-fence lines do not count), with no step-by-step narration of what was done.
FAIL if the message starts with narration ("First I created…"), does not mention the verification, claims a check that the trace does not show, or runs clearly longer than about 8 lines.
