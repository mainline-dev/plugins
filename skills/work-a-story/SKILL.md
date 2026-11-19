---
name: work-a-story
description: Build one Mainline story by working through its acceptance scenarios one at a time, each with a failing test first and then the smallest change that passes it, then stopping for a walkthrough. Use when the person asks to work on, build, implement, start or pick up a Mainline story, or names a Mainline story ID such as ABC12345. Do not use for coding that is not tied to a Mainline story.
---

# Work a story

You are building one story from the team's Mainline map. People on the team wrote and approved its acceptance scenarios. Your job is to make them pass in small, safe steps, then stop so a person can be walked through the change.

The Mainline tools come from the Mainline MCP server: `list_maps`, `get_map`, `get_story`, `get_feature_file` and `get_import_format`, and on mainline.dev `read_docs`. They cannot change the map, although reading a story marks it as agent-assisted. If they are not available, stop and tell the person to sign in to the server as the Mainline plugin README describes. Never guess what a story or scenario says.

## 1. Choose one story

- If the person gave a story ID, call `get_story` with it. `get_story` needs the story's full ID. If you only have the 8-character short ID shown on the story card, such as `ABC12345`, find the story in `get_map` (calling `list_maps` first) and use its full `id`.
- If the person did not give an ID, call `get_map` and ask which story to work on. If you do not know which map, call `list_maps` first and ask.
- Work on one story at a time. Do not start a second story until the first is ready for its walkthrough.

## 2. Check the scenarios

- If the story has no acceptance scenarios, stop and say so. Do not write them yourself.
- The scenarios belong to the team. Use them exactly as written. Do not reword them, in tests or in conversation.
- If a scenario looks wrong, contradicts another or cannot be tested, stop. Tell the person which scenario and why, and wait. People change scenarios in Mainline; you do not.

## 3. One scenario at a time

Take the scenarios one at a time, and finish each one before you start the next:

1. Write an executable test for this scenario only. Use the project's existing test framework, layout and naming, and any feature files or step definitions already present. Make the test traceable to its scenario, for example by using the scenario's name as the test name.
2. Run it and confirm it fails for the expected reason: the behaviour is missing. A failure from a typo, a missing import or broken setup does not count. Fix the test until it fails for the right reason.
3. Make the smallest change that passes it.
4. Run the whole suite, not only the new test. If something else breaks, fix the code.
5. Commit, as step 5 describes.

Then move on to the next scenario. Tidy the code only while the suite is passing, and run it again afterwards.

## 4. Protect existing tests

- Never weaken, skip, disable or delete an existing test to get a pass.
- If an existing test must change, for example because the story deliberately changes behaviour it checks, name the test and say why before you change it.

## 5. Commit and integrate

- Commit when each scenario passes, and more often if it helps, as long as every commit leaves the whole suite passing.
- Put the story's short ID in square brackets in every commit message, for example `[ABC12345] Show the delivery date on the order summary`.
- Integrate the way the team does: follow the branching, rebasing and review conventions you can see in the repository and its contributing notes. If they are unclear, ask.
- Do not push or deploy unless the person has told you to.

## 6. Keep unfinished work hidden

If the change is not ready for users, keep it hidden by the team's usual means, such as their existing feature flags. If you are not sure how the team does this, ask before adding anything new.

## 7. Leave the record to people

Never mark a scenario done or a story released. People do that in Mainline, and the server will not let you.

## 8. Stop for the walkthrough

When every scenario has a passing test and the whole suite passes, stop. Do not start another story. Run the `prepare-walkthrough` skill so a person can be walked through the change.
