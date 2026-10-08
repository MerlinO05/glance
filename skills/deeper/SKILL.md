---
name: deeper
description: Expand one direction of the previous answer, one level deeper, in the same glance format. Takes a number from the last "Deeper:" line or a free topic.
argument-hint: "[number | topic]"
disable-model-invocation: true
---

# deeper

The reader wants to go one level deeper into the previous answer. Request: `$ARGUMENTS`

## 1. Resolve the direction

- **A number** (for example `2`): take that direction from the last `Deeper:` line you wrote.
- **A topic** (any other text): use it as the direction. Interpret it relative to the previous
  answer.
- **Several numbers** (for example `1 3`): cover each direction in its own section, in that order.
- **Nothing**: take direction 1 from the last `Deeper:` line. If there is no such line, name the
  part of the previous answer that you compressed most and expand that.
- **The number does not exist**, or there was no previous answer: say so in one sentence and list
  the available directions.

## 2. Expand only that direction

- Start with one sentence that names the direction, so the reader knows where they are. Write it
  in the reader's language and name the topic itself, not its number ("Interactive rebase lets
  you…", not "Direction 2 is…").
- Go exactly one level deeper. Explain the mechanism, the evidence, a concrete example, or the
  trade-off, whichever the direction asks for.
- Do not repeat what the previous answer already said. Refer to it in a few words instead.
- If the direction needs facts you have not checked, check them first (read the file, run the
  command, look up the source). Do not fill a gap with plausible text.
- Apply the same format rules as every answer: answer first, plain sentences, choose text,
  diagram, or page by the shape of the content.

## 3. End

- End with a new `Deeper:` line that offers two to four directions one level further down, unless
  the topic is exhausted. In that case, end without the line.
