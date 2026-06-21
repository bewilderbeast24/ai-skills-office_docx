# DOCX Processing AI Skill

A professional-grade AI skill designed for the comprehensive manipulation and management of Microsoft Word (.docx) documents. This toolkit enables AI agents to perform complex document operations—including reading, analyzing, creating, and editing—with high structural precision and formatting consistency.

## Overview

The `docx-processing` skill provides a structured framework for interacting with Word documents. It is optimized for tasks ranging from simple text extraction to the generation of complex professional documents featuring tables of contents, headings, and integrated imagery.

## Installation

To integrate this skill into an AI agent environment, clone the repository into the `.agents/skills/` directory:

```bash
git clone https://github.com/bewilderbeast24/ai-skills-docx_processing.git docx-processing
```

## Operational Modes

The skill operates in four specialized modes to ensure focused execution and document integrity:

### 1. Read and Analyze
Extracted content, metadata, and structural information from existing documents. This mode is used for summarization, data extraction, and content auditing.

### 2. Create Document
Generates new documents from scratch or based on predefined templates. It supports professional formatting such as:
- Dynamic Tables of Contents
- Multi-level Headings
- Custom Headers and Footers
- Stylized Tables and Lists

### 3. Edit Document
Modifies existing documents through precise structural adjustments. Capabilities include:
- Image insertion and replacement
- Targeted find-and-replace operations
- Section restructuring
- Metadata updates

### 4. Accept Tracked Changes
Automates the resolution of document revisions. This mode programmatically accepts or rejects tracked changes and manages document comments, ensuring a clean final version.

## Technical Architecture

The skill leverages a hybrid approach to document manipulation:
- **XML-Level Manipulation**: For high-performance editing, the skill unpacks `.docx` containers and modifies the underlying OpenXML structure directly.
- **LibreOffice Integration**: Utilizes the `soffice` engine for complex operations that require a full document layout engine, such as resolving tracked changes.
- **Python Backend**: Employs robust Python scripts to orchestrate document I/O, validation, and metadata management.

## Execution Workflow

The skill follows a standardized lifecycle to ensure reliable outcomes:

1.  **Mode Selection**: The agent identifies the user's intent and selects the appropriate operational mode.
2.  **Context Setup**: Necessary assets, templates, and target files are identified and prepared.
3.  **Specialized Execution**: The mode-specific logic is executed (e.g., XML modification or LibreOffice macro execution).
4.  **Outcome Validation**: The resulting document is verified for structural integrity and formatting before delivery.

## Requirements

- **Python 3.8+**
- **LibreOffice**: Required for tracked changes and advanced conversion tasks.
- **Agent Framework**: Designed for AI agents capable of interpreting `.md` based skill definitions.

## Project Structure

- `SKILL.md`: Core skill definition and logic.
- `scripts/`: Implementation scripts for document manipulation.
- `assets/`: Workflow definitions and operational assets.
- `references/`: Templates and checklists for execution tracking.
