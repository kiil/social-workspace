---
type: guide
title: Social life workspace
description: Getting started with the social life workspace.
---

# Social life workspace

A social life as a graph of notes: practice guides on meeting people and keeping them, plus three kinds of records — the venues worth investing in, the people you want to stay in touch with, and a short journal of interactions worth learning from. It covers four tracks with one shared core: friendship, community, professional network and romance. Start at [the framework map](guides/framework.md) or the [Quick-Start Guide](guides/quick-start-guide.md).

The bundle conforms to [OKF v0.2](https://github.com/GoogleCloudPlatform/knowledge-catalog/blob/main/okf/SPEC.md): every document has frontmatter with a `type`, every folder has an `index.md`, and changes go in [log.md](log.md).

## Worked example

The records ship with a small fictional example:

- [Harbour Art Museum](venues/harbour-art-museum.md) — a venue you *belong to* as a regular.
- [Westbay Sailing Club](venues/westbay-sailing-club.md) — a venue you *contribute to* as a volunteer instructor.
- [Sam Rivera](people/sam-rivera.md) — an acquaintance with a next step.
- [2026-11-10](journal/2026-11-10.md) — a missed hello, and what to do next time.

Every person and place in them is invented. Replace them with your own, or delete them, before you start.

## Daily use

``` bash
iwe new -t journal "2026-11-13"            # → journal/2026-11-13.md
iwe new -t person "First Last"             # → people/first-last.md
iwe new -t venue "Place name"              # → venues/place-name.md
iwe update -k people/first-last --set last_contact=2026-11-13 --set next_step_due=2026-11-27
iwe find --filter 'type: person, next_step_due: {$exists: true}' --project 'title,next_step,next_step_due' --sort 'next_step_due:1'
iwe find --filter 'type: guide, track: friendship' --project 'title,description'
iwe schema validate
```

The agent instructions are in [AGENTS.md](AGENTS.md). The skill in `.claude/skills/log-interaction/` describes how to record an interaction.

## Privacy

This workspace is about other people. Write down only what you would be comfortable with them reading, keep it out of public repositories, and never store anything they told you in confidence.
