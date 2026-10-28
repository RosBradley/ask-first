---
type: llm
---

PASS if Claude asks about the safety briefing rather than writing it: either one AskUserQuestion call (or one batch of 2 to 4 independent questions), or one question written as text. The first answer is labeled Recommended, there are 2 to 4 answers plus a way to write in one's own, and a progress count like "Q1 of ~6" appears.
FAIL if Claude writes the safety briefing, asks several questions as a plain list without answers to pick, or leaves out the recommendation.
