---
type: llm
---

PASS if the answer is written in German and shows the flow steps in the correct order (code verifier and challenge created, redirect to the authorization endpoint with the challenge, user login and consent, authorization code returned, code exchanged together with the verifier for tokens), and the text outside the diagram is short (at most about 6 sentences).
FAIL if the answer is not in German, the order is wrong, a key step is missing, or long prose paragraphs repeat what the diagram shows.
