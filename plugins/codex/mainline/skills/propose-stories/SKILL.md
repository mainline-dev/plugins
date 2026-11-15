---
name: propose-stories
description: Turn a specification, plan or research document into proposed Mainline stories, written as an import file in the format Mainline asks for, for people to review in the Ticket Museum. Use when the person asks to propose, draft or import Mainline stories from a document. Do not use for writing code, or for tickets in trackers other than Mainline.
---

# Propose stories

Turn a document the person gives you into proposed stories. You are proposing, not deciding. Each proposal waits in the Ticket Museum for a person to read, edit and promote it. Nothing becomes a story until then.

## 1. Get the document

- If the person has not given you a document, such as a file, pasted text or a page you can read, ask for one.
- Work only from that document. Never invent entries. Do not add stories from your own ideas, the codebase or earlier conversation.

## 2. Get the format

- Call `get_import_format` and follow it exactly: the file type, the field names, which fields are required, and any rules or limits it states. Do not add fields it does not describe.
- If the Mainline tools are not available, stop and say so. Do not guess the format.

## 3. Draft the entries

- Each entry must trace back to something the document says. Where the document describes separate pieces of work, make them separate entries.
- Use the document's own wording where you can, so reviewers can see where each entry came from.
- If the document leaves out something the format requires, do not fill the gap yourself. Leave that entry out and tell the person what is missing.

## 4. Write the file and stop

- Write the file. Use the file name the format suggests, or `mainline-proposals` with the format's extension if it suggests none. If that file already exists, ask before overwriting it.
- Run nothing else: no scripts, tests, commits or uploads.
- Tell the person where the file is, and to upload it to the Ticket Museum in Mainline, where each proposal waits for a person to read, edit and promote it. Nothing becomes a story until then. List anything from the document you left out, and why.
