# Step: 03-03-edit-document

## Description
Edit an existing `.docx` file using the unpack-edit-pack method.

## Purpose
- To modify an existing document's contents, apply tracked changes, or insert comments accurately.

## Pre-stage Checkpoint
- Ensure the target `.docx` file exists.

### Version Control
None.

## Workflow

### Process

**Step 1: Unpack**
```bash
python scripts/office/unpack.py document.docx unpacked/
```

**Step 2: Edit XML**
Edit files in `unpacked/word/`.
- Use the Edit tool directly for string replacement.
- Use "Grok" as the author for tracked changes/comments unless specified.
- **CRITICAL: Use smart quotes for new content** (`&#x201C;`, `&#x201D;`, `&#x2018;`, `&#x2019;`).
- Adding comments: Use `comment.py` to handle boilerplate.
  ```bash
  python scripts/comment.py unpacked/ 0 "Comment text with &amp; and &#x2019;"
  ```
  Then manually add markers (`<w:commentRangeStart>`, `<w:commentRangeEnd>`) to `document.xml` as siblings of `<w:r>`.

- **XML Tracked Changes Guide**:
  - **Insertion**: Use `<w:ins>` wrapper.
  - **Deletion**: Use `<w:del>` wrapper with `<w:delText>` inside.
  - Make minimal edits (only mark what changes).
  - Deleting entire paragraphs requires placing `<w:del/>` inside `<w:pPr><w:rPr>`.

- **Images**:
  1. Add to `word/media/`
  2. Add relationship to `word/_rels/document.xml.rels`
  3. Add content type to `[Content_Types].xml`
  4. Reference in `document.xml` using `<w:drawing>`

**Step 3: Pack**
```bash
python scripts/office/pack.py unpacked/ output.docx --original document.docx
```
(Pack includes auto-repair for ID issues and whitespace).

### Output Format
- A modified `output.docx` file.

## Post-stage Checkpoint

### Progress Tracking
- Update `.agents/skills-diary/docx-processing/[<instance-name>]/checklist.md` by marking "03-03-edit-document" as completed (`[x]`).

### Version Control
None.

### Human in the Loop (HITL)
- Ask the user to review the edited `.docx` file.

### Auto pilot
- Return the path to the edited document.
