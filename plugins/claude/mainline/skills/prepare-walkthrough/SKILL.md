---
name: prepare-walkthrough
description: Prepare a short summary of a Mainline story so a second person can be walked through the change, covering each acceptance scenario with its test, the shape of the change, tests changed or removed, and anything unfinished. Use when every scenario in a Mainline story has a passing test, when work-a-story hands over, or when the person asks to get a story ready for its walkthrough. Do not use for general code review or for changes not tied to a Mainline story.
---

# Prepare a walkthrough

Before a person is walked through a story's change, give them a summary they can read in two minutes.

## Gather the facts

1. Call `get_story` with the story's full ID for its title, short ID and acceptance scenarios as the team wrote them. If the Mainline tools are not available, stop and say so.
2. Find the story's commits by its short ID, for example `git log --oneline -F --grep "[ABC12345]"`. Check `git status` for work not yet committed.
3. Read what those commits changed, with `git show --stat` and `git show`.
4. Run the tests for each scenario, and the whole suite, so what you report is current.

## Write the summary

Use these four parts, in this order. Keep lines short and leave out anything the reader does not need to follow the change.

- **Behaviour.** One line per scenario, in the order Mainline lists them: the scenario, named exactly as Mainline has it, the test that covers it (file and test name), and whether it passes.
- **Shape of the change.** The areas and files touched. Group by area when there are many files. Call out anything structural: a migration, a new or upgraded dependency, a changed interface or API, new configuration or a feature flag.
- **Tests changed or removed.** Each existing test that was changed or removed, what changed and why.
- **Not finished or worth a closer look.** Loose ends, known limits, behaviour outside the scenarios that you noticed, and anything you were unsure about.

Write "None" under a part with nothing in it. Use this shape:

```
[ABC12345] <story title>

Behaviour
- <scenario>: <test file and name>. Passing.

Shape of the change
- <areas and files touched>
- Structural: <migration, dependency, interface, flag>, or none.

Tests changed or removed
- <test>: <what changed>, because <why>.

Not finished or worth a closer look
- <item>
```

## Finish

- If every scenario has a passing test, end with: "ABC12345 is ready for its walkthrough. A person records the walkthrough in Mainline." Use the story's real short ID.
- If any scenario has no passing test, say which, and say the story is not ready for its walkthrough yet.
- Do not mark anything in Mainline, push or deploy as part of this skill.
