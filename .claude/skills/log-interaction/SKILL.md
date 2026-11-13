---
name: log-interaction
description: Record an interaction in the social life workspace — a journal entry, the person's note and their next step. Use when the user tells you about meeting, messaging or missing someone.
---

# Log an interaction

1. **Journal entry.** If `journal/<YYYY-MM-DD>.md` does not exist, create it with `iwe new -t journal "<YYYY-MM-DD>"`. Fill `## What happened` with facts only, `## What I noticed` with the user's own observations, and `## Next time` with one concrete action. Set `outcome` to `connected`, `missed`, `declined` or `neutral`, and `venue` and `people` to slugs.
2. **Person.** If the user wants to see the person again and there is no `people/<slug>.md`, create it with `iwe new -t person "<Name>"`. Record only what the user said and what the person would be comfortable seeing. Add a line to `## Contact log`, newest first: `- <YYYY-MM-DD> — <what happened>`.
3. **Next step.** Set `last_contact`, `next_step` and `next_step_due` with `iwe update -k people/<slug> --set ...`. A next step is specific and small: "ask about the darkroom course", not "get closer".
4. **Venue.** If the place is new and the user expects to return, create `venues/<slug>.md` with `iwe new -t venue "<Place>"`.
5. **Indexes and log.** Add any new document to its folder's `index.md` as `* [Title](file.md) - description`. Note the change in `log.md` only for structural changes, not for every interaction.
6. Run `iwe schema validate`.

Never send a message for the user. If they want to follow up, draft it and let them send it.
