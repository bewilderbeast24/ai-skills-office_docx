# Step: 04-outcome

## Description
Finalize the operation based on mode-specific criteria and hand over to the user.

## Purpose
- Ensure the resulting files are valid and ready for the user.
- Provide a summary of the actions taken.

## Pre-stage Checkpoint
- The specialized workflow (Step 03) must be fully complete and any generated files must exist on the file system.

### Version Control
None.

## Workflow

### Process
- Verify that the target files were successfully created or modified (e.g., run `validate.py` on the output if applicable).
- Summarize the changes or present the extracted data to the user.
- If temporary unpacked directories were used (e.g. in `edit-document`), clean them up.

### Output Format
- Final response to the user containing the results or paths to the generated `.docx` files.

## Post-stage Checkpoint

### Progress Tracking
- Update `.agents/skills-diary/docx-processing/[<instance-name>]/checklist.md` by marking "04-outcome" as completed (`[x]`).

### Version Control
None.

### Human in the Loop (HITL)
- Hand over the final results to the user.

### Auto pilot
- Complete the sequence and report final state automatically.
