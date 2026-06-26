# Step: 03-04-accept-changes

## Description
Produce a clean document with all tracked changes accepted.

## Purpose
- To automate the acceptance of all tracked modifications in a document using LibreOffice.

## Pre-stage Checkpoint
- Ensure the input document exists and LibreOffice is available in the environment.

### Version Control
None.

## Workflow

### Process
- Run the accept changes script on the target document:
  ```bash
  python scripts/accept_changes.py input.docx output.docx
  ```

### Output Format
- A clean `output.docx` file with all changes accepted.

## Post-stage Checkpoint

### Progress Tracking
- Update `.agents/skills-diary/docx-processing/[<instance-name>]/checklist.md` by marking "03-04-accept-changes" as completed (`[x]`).

### Version Control
None.

### Human in the Loop (HITL)
- Provide the cleaned document to the user for review.

### Auto pilot
- Return the cleaned document directly.
