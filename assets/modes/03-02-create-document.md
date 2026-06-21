# Step: 03-02-create-document

## Description
Generate a new `.docx` file from scratch using `docx-js`.

## Purpose
- To programmatically create correctly structured, professional `.docx` files following strict stylistic rules.

## Pre-stage Checkpoint
- Required content and structure must be defined.
- `docx` node module must be installed (`npm install -g docx` or local).

### Version Control
None.

## Workflow

### Process

1. **Setup:**
   ```javascript
   const { Document, Packer, Paragraph, TextRun, Table, TableRow, TableCell, ImageRun, Header, Footer, AlignmentType, PageOrientation, LevelFormat, ExternalHyperlink, InternalHyperlink, Bookmark, FootnoteReferenceRun, PositionalTab, PositionalTabAlignment, PositionalTabRelativeTo, PositionalTabLeader, TabStopType, TabStopPosition, Column, SectionType, TableOfContents, HeadingLevel, BorderStyle, WidthType, ShadingType, VerticalAlign, PageNumber, PageBreak } = require('docx');
   const doc = new Document({ sections: [{ children: [/* content */] }] });
   Packer.toBuffer(doc).then(buffer => fs.writeFileSync("doc.docx", buffer));
   ```
2. **Validation:**
   After creating the file, validate it. If it fails, unpack, fix XML, and repack.
   ```bash
   python scripts/office/validate.py doc.docx
   ```

3. **Critical Rules for docx-js Execution:**
   - **Set page size explicitly**: default is A4; use US Letter (12240 x 15840 DXA) for US docs.
   - **Landscape**: pass portrait dimensions (short edge as width, long edge as height) and set `orientation: PageOrientation.LANDSCAPE`.
   - **Never use `\n`**: use separate Paragraph elements.
   - **Never use unicode bullets**: use `LevelFormat.BULLET` with numbering config.
   - **PageBreak must be in Paragraph**: standalone creates invalid XML.
   - **Preserve image aspect ratio**: compute height from width using source dimensions.
   - **ImageRun requires `type`**: png/jpg/etc.
   - **ImageRun uses `data`, not `path`**: fetch/read bytes first.
   - **SVG images require `fallback`**: provide a PNG/JPG.
   - **Use meaningful `altText`**: `name` is required.
   - **Always set table `width` with DXA**: never PERCENTAGE.
   - **Tables need dual widths**: `columnWidths` array AND cell `width` must match.
   - **Always add cell margins**: use `margins: { top: 80, bottom: 80, left: 120, right: 120 }`.
   - **Use `ShadingType.CLEAR`**: never SOLID for table shading.
   - **Never use tables as dividers/rules**: use paragraph borders.
   - **TOC requires HeadingLevel only**: no custom styles on heading paragraphs.
   - **Override built-in styles**: use exact IDs ("Heading1", etc.) and include `outlineLevel`.

### Output Format
- A single generated `doc.docx` file.

## Post-stage Checkpoint

### Progress Tracking
- Update `.agents/skills-diary/docx-processing/[<instance-name>]/checklist.md` by marking "03-02-create-document" as completed (`[x]`).

### Version Control
None.

### Human in the Loop (HITL)
- Ask the user to review the generated `.docx` file.

### Auto pilot
- Return the path to the generated document.
