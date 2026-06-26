# Step: 01-mode-selection

## Description
Present options to the user to determine the specific mode of DOCX processing required.

## Purpose
- Determine if the user wants to read/analyze a document, create a new document, edit an existing document, or accept tracked changes.
- Capture the choice to dictate the specialized workflow path.

## Pre-stage Checkpoint
- Ensure skill directory is properly initialized.

### Version Control
None.

## Workflow

### Process
- Use the `ask_user` tool (or equivalent interactive prompt) to present the following operational modes:
  1. `read-analyze`: Read, extract text, or convert an existing .doc/.docx file to images/pdf.
  2. `create-document`: Generate a new .docx file using `docx-js`.
  3. `edit-document`: Unpack, edit XML (including adding tracked changes or comments), and repack an existing .docx file.
  4. `accept-changes`: Accept tracked changes in a document using LibreOffice.
- Save the user's selected mode into the agent's internal state.

### Output Format
- A selected mode string (e.g., "read-analyze", "create-document", "edit-document", "accept-changes") held in internal memory.

## Post-stage Checkpoint

### Progress Tracking
- Update `.agents/skills-diary/docx-processing/[<instance-name>]/checklist.md` by marking "01-mode-selection" as completed (`[x]`).

### Version Control
None.

### Human in the Loop (HITL)
- Wait for the user to make a selection.

### Auto pilot
- If the user query clearly implies a specific mode (e.g. "create a new memo", "read this doc"), automatically select the corresponding mode and proceed.
