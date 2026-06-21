---
name: docx-processing
description: "Use when the user wants to create, read, edit, or manipulate Word documents (.docx files). Triggers include: any mention of 'Word doc', 'word document', '.docx', or requests to produce professional documents with formatting like tables of contents, headings, page numbers, or letterheads. Also use when extracting or reorganizing content from .docx files, inserting or replacing images in documents, performing find-and-replace in Word files, working with tracked changes or comments, or converting content into a polished Word document. If the user asks for a 'report', 'memo', 'letter', 'template', or similar deliverable as a Word or .docx file, use this skill. Do NOT use for PDFs, spreadsheets, Google Docs, or general coding tasks unrelated to document generation."
---

# docx-processing

## Skill Overview
This skill acts as a comprehensive toolkit for dealing with Word Documents (.doc and .docx). It provides four distinct operational modes for analyzing content, creating new documents from scratch, editing existing documents (including XML manipulations), and accepting tracked changes.

## Workflow Sequence

| Stage | Description | Workflow | Input | Output |
| :--- | :--- | :--- | :--- | :--- |
| **1. Mode Selection** | Present options to the user and capture choice. | `[assets/01-mode-selection.md](assets/01-mode-selection.md)` | Options | Selected Mode |
| **2. Context Setup** | Load configurations/assets for the chosen mode. | `[assets/02-context-setup.md](assets/02-context-setup.md)` | Selected Mode | Context |
| **3. Specialized Workflow** | Execute the logic specific to the selected mode. | `[assets/03-specialized-workflow.md](assets/03-specialized-workflow.md)` | Context | Results |
| **4. Outcome** | Finalize based on mode-specific criteria. | `[assets/04-outcome.md](assets/04-outcome.md)` | Results | Final Output |

## Pre-stage Checkpoint
- **Human in the Loop (HITL)**: By default, ask for user confirmation when choosing the mode and at the conclusion of the operation before delivering the final document.
- **Autopilot**: If the user's initial prompt explicitly requests a specific mode (e.g., "create a new memo", "read this doc"), the agent can autonomously select the correct mode and bypass HITL until the final step.

## Core Operation Flow

### Initialization
Before proceeding to Step 1, the agent MUST initialize the checklist in `.agents/skills-diary/docx-processing/[<instance-name>]/checklist.md` using the template at `[references/checklist.md](references/checklist.md)`.

### Global Stages
- **Step 1: Mode Selection**: Follow the instructions in `[assets/01-mode-selection.md](assets/01-mode-selection.md)` to capture the user's intended mode interactively or autonomously. Save this selection in the agent's internal state.
- **Step 2: Context Setup**: Follow `[assets/02-context-setup.md](assets/02-context-setup.md)` to identify files and dependencies.

### Mode-Specific Workflow (Step 3)
Depending on the selected mode, only follow the logic in the corresponding workflow document under `assets/modes/`:

#### Execution: Mode read-analyze
- Follow `[assets/modes/read-analyze/03-01-read-analyze.md](assets/modes/read-analyze/03-01-read-analyze.md)`

#### Execution: Mode create-document
- Follow `[assets/modes/create-document/03-02-create-document.md](assets/modes/create-document/03-02-create-document.md)`

#### Execution: Mode edit-document
- Follow `[assets/modes/edit-document/03-03-edit-document.md](assets/modes/edit-document/03-03-edit-document.md)`

#### Execution: Mode accept-changes
- Follow `[assets/modes/accept-changes/03-04-accept-changes.md](assets/modes/accept-changes/03-04-accept-changes.md)`

**CRITICAL CONSTRAINT**: The agent MUST NOT utilize logic, assets, or references defined for any unselected mode. Strict segregation is required.

### Finalization
- **Step 4: Outcome**: Conclude the operation by following `[assets/04-outcome.md](assets/04-outcome.md)`. Verify outputs and hand them over to the user.

## Handover & Confirmation
The skill is successfully completed when the requested document operation is finished and valid `.docx` files, images, or extracted text are presented to the user.

A successful execution creates a directory tree representation of the output similar to:
```text
<project-dir>/
    document.docx
    ...
```

## Additional Instructions
All temporary scripts generated while execution of skills (scripts which will be deleted after execution) will be written in `.agents/skills-diary/temp-scripts/<timestamp>/` as directory
