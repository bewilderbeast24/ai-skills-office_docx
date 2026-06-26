# Step: 03-01-read-analyze

## Description
Extract text, read XML, or convert a DOCX to images/PDF.

## Purpose
- To provide text or visual access to the contents of a `.doc` or `.docx` file for analysis or extraction.

## Pre-stage Checkpoint
- Ensure the target file exists.
- If the file is a legacy `.doc`, it must be converted to `.docx` before extraction.

### Version Control
None.

## Workflow

### Process
1. **Convert `.doc` to `.docx` (if needed):**
   ```bash
   python scripts/office/soffice.py --headless --convert-to docx document.doc
   ```
2. **Reading Content (Text Extraction):**
   To extract text with tracked changes visible, run:
   ```bash
   pandoc --track-changes=all document.docx -o output.md
   ```
3. **Reading Content (Raw XML):**
   To unpack and analyze raw XML, run:
   ```bash
   python scripts/office/unpack.py document.docx unpacked/
   ```
4. **Converting to Images/PDF:**
   To convert to PDF and then to images, run:
   ```bash
   python scripts/office/soffice.py --headless --convert-to pdf document.docx
   pdftoppm -jpeg -r 150 document.pdf page
   ```

### Output Format
- Extracted `.md` file, an `unpacked/` directory, or generated `.pdf`/`.jpeg` files.

## Post-stage Checkpoint

### Progress Tracking
- Update `.agents/skills-diary/docx-processing/[<instance-name>]/checklist.md` by marking "03-01-read-analyze" as completed (`[x]`).

### Version Control
None.

### Human in the Loop (HITL)
- Provide extracted text or links to generated images to the user.

### Auto pilot
- Return the extracted content or file paths directly.
