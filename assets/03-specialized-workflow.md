# Step: 03-specialized-workflow

## Description
Execute the logic specific to the selected operational mode.

## Purpose
- Load and follow the specialized workflow instructions for the chosen mode to accomplish the user's goal.

## Pre-stage Checkpoint
- Required input files and context must be validated.

### Version Control
None.

## Workflow

### Process
- Based on the mode selected in Step 01, refer to the corresponding workflow document in the `assets/modes/` directory:
  - For `read-analyze`: Refer to `[03-01-read-analyze.md](modes/read-analyze/03-01-read-analyze.md)`.
  - For `create-document`: Refer to `[03-02-create-document.md](modes/create-document/03-02-create-document.md)`.
  - For `edit-document`: Refer to `[03-03-edit-document.md](modes/edit-document/03-03-edit-document.md)`.
  - For `accept-changes`: Refer to `[03-04-accept-changes.md](modes/accept-changes/03-04-accept-changes.md)`.
- **Constraint**: You MUST NOT utilize logic or rules defined for unselected modes. Confine execution to the rules in the selected mode's asset file.

### Output Format
- Processed `.docx` files, extracted text, or generated PDFs/images as determined by the specific mode.

## Post-stage Checkpoint

### Progress Tracking
- Update `.agents/skills-diary/docx-processing/[<instance-name>]/checklist.md` by marking the respective mode's workflow as completed (`[x]`).

### Version Control
None.

### Human in the Loop (HITL)
- Prompt for review of the modified or generated files before finalization.

### Auto pilot
- Proceed to the Outcome step automatically once the mode's operations are complete.
