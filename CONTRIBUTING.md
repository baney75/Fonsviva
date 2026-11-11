# Contributing to Fonsviva

## Coauthorship

Docs and code here are coauthored. Credit everyone who worked on a change, including AI agents, with Co-authored-by lines in the commit:

```
Co-authored-by: Donovan Baney <donovan@dbaney.com>
Co-authored-by: Gil Rodrigues <work@gildrb.com>
```

## Design work

1. Take a card on the Notion board for Fonsviva, assign yourself and move it to In progress.
2. Design it in Penpot or Figma, following `DESIGN.md`.
3. Export the screens to `design/exports/` and open a pull request. Link the PR and the design file on the card.
4. Update `DESIGN.md` when you set a new rule, component or pattern, so agents building the UI follow it.
5. Move the card to Done when you're satisfied. Designers close their own cards.

## Code, skills and docs

- Read `AGENTS.md` first. It applies to people as well as agents.
- New or changed skills follow `skills/README.md` and need tests.
- Any claim about what Fonsviva can do needs a passing test (see `TESTING.md`).
- Work on a branch, open a pull request into `main`, and keep CI green. See `RELEASES.md` for how changes reach Dev and Stable.
