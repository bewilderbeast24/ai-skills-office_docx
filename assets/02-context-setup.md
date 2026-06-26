# Step: 02-context-setup

## Description
Load configurations, dependencies, and identify target files for the chosen mode.

## Purpose
- Gather the required input files or configuration details from the user or the workspace based on the chosen mode.
- Verify that necessary dependencies are available.

## Pre-stage Checkpoint
- Mode must be successfully selected in Step 01.

### Version Control
None.

## Workflow

### Process
- If mode is `read-analyze`: Identify the target `.doc` or `.docx` file in the workspace. Verify `pandoc`, Python, and LibreOffice/`pdftoppm` availability.
- If mode is `create-document`: Identify the desired content and style requirements. Ensure `docx` (Node.js module) is installed via `npm`.
- If mode is `edit-document`: Identify the target `.docx` file to be edited and the specific edits required.
- If mode is `accept-changes`: Identify the input and output `.docx` file paths.

### Output Format
- Context dictionary/variables representing the target file paths and validated tool availability.

## Post-stage Checkpoint

### Progress Tracking
- Update `.agents/skills-diary/docx-processing/[<instance-name>]/checklist.md` by marking "02-context-setup" as completed (`[x]`).

### Version Control
None.

### Human in the Loop (HITL)
- Ask user for clarification if the required input files or content cannot be confidently determined.

### Auto pilot
- Automatically resolve file paths from the user's initial prompt and proceed.
