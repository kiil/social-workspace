---
type: guide
title: Agent workspace instructions
description: How an agent works in this social life workspace.
---

# Agent workspace instructions

Reply in the user's language. Write field names, filenames and documentation in English.

This workspace supports the user's social life: friendships, community, professional network and romance. `guides/` holds practice guides; `venues/`, `people/` and `journal/` hold the user's own records. Start at [the framework map](guides/framework.md). Use `iwe` for every structural operation (`iwe find`, `iwe retrieve`, `iwe new -t <template>`, `iwe update --set`) and run `iwe schema validate` after changes.

The records with `is_example: true` ship with the template. Every person and place in them is fictional. Offer to delete them once the user has recorded real ones, and never treat them as facts about the user.

## OKF v0.2

The workspace is an OKF v0.2 bundle.

- Every document except `index.md` and `log.md` has frontmatter with a non-empty `type`, plus `title` and `description`.
- Every folder has an `index.md` with no frontmatter (only the root one carries `okf_version`), made of headings with bullets in the form `* [Title](path.md) - description`. When you add, rename or delete a document, update the `index.md` of its folder in the same change.
- Record each meaningful change in [log.md](log.md) under an ISO date heading, newest first.
- When you write or substantially rewrite a guide, add `generated: {by: <agent>/<version>, at: <ISO datetime>}`. Only the user can add `verified`.
- Links are relative and end in `.md`.

## Who owns which fact

- `people/<slug>.md` owns what is known about one person and the next step: `relationship`, `met`, `met_at`, `last_contact`, `next_step`, `next_step_due`. Change them with `iwe update -k people/<slug> --set field=value`.
- `journal/<date>.md` records what happened in one interaction and what to try next time. It links to the people and venue involved.
- `venues/<slug>.md` records why a place works and how to use it, following the pattern of the worked examples.
- `guides/` holds general advice. Do not write facts about the user or other people there.

## Privacy and other people

- These notes are about third parties. Record only what the user tells you, and only what the person would be comfortable seeing written down. No health details, no secrets told in confidence, no addresses or phone numbers unless the user insists.
- Never send a message, post, like or follow on the user's behalf, and never create an account. Draft the text, show it, and let the user send it. Log the contact afterwards, when the user confirms it happened.
- Never help with deception, pressure, or getting past someone's no. [Boundaries and Consent](guides/boundaries-consent.md) applies to everything here.
- If the user describes distress beyond everyday nerves, point to [Inner Blocks and Light Social Anxiety](guides/blocks-social-anxiety.md) and suggest professional help, without diagnosing.

## Queries

``` bash
iwe find --filter 'type: person, next_step_due: {$exists: true}' --project 'title,next_step,next_step_due' --sort 'next_step_due:1'
iwe find --filter 'type: person, relationship: acquaintance' --project 'title,met,last_contact'
iwe find --filter 'type: journal-entry, outcome: missed' --project 'title,venue,people'
iwe find --filter 'type: venue' --project 'title,mode,recurrence'
iwe find --filter 'type: guide' --project 'title,track' --sort 'track:1'
```
