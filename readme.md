# LaTeX Templates for Academic Papers

This repository contains LaTeX templates for writing academic papers.

## Getting Started

When you clone this repository, follow these steps:

### Step 1: Choose and Rename Your Template

Pick the template that fits your needs and rename it to your paper name:

```bash
# For INFORMS journals (OR, MS, MOOR, MSOM, etc.)
mv template-informs.tex my-paper-title.tex

# For general working papers or course projects
mv template-plain.tex my-paper-title.tex

# For RGC proposals
mv template-RGC.tex my-proposal.tex
```

### Step 2: Delete Unnecessary Files

Remove the templates and reference folders you don't need:

```bash
# Remove unused templates
rm template-*.tex

# Remove reference folders
rm -rf INFORMS-MNSC-Template-6-10-2024/
rm -rf INFORMS-OPRE-Template-2-21-2025/
```

### Step 3: Write Your Paper

**Use ONE main file** for your entire paper. Keep everything in a single `.tex` file unless the paper becomes very long.

For INFORMS journals, the Electronic Companion (EC) can be separated into a second file if needed:
- `my-paper.tex` - Main paper
- `my-paper-ec.tex` - Electronic Companion (optional)

### Step 4: Compile

```bash
pdflatex my-paper.tex
bibtex my-paper
pdflatex my-paper.tex
pdflatex my-paper.tex
```

## Directory Structure

```
latex/
  |-- my-paper.tex        # Your main paper (renamed from template)
  |-- ref.bib             # Bibliography database
  |-- style/              # Style files - DO NOT MODIFY
  |-- tikz/               # TikZ figures and settings
```

## For INFORMS Submissions

Change the journal by modifying the document class option:

```latex
\documentclass[opre,sglanonrev]{style/informs4}  % Operations Research
\documentclass[mnsc,dblanonrev]{style/informs4}  % Management Science
\documentclass[moor,sglanonrev]{style/informs4}  % Math of OR
```

Review options:
- `sglanonrev` - Single anonymous (non-blind)
- `dblanonrev` - Double anonymous (blind)

## Coding Style

See [latex-coding-style.md](latex-coding-style.md) for guidelines on writing clean, maintainable LaTeX code.

Key points:
- One sentence per line (helps with git diff and backward search)
- Use proper labeling: `\label{eq:name}`, `\label{thm:name}`, `\label{sec:name}`
- Use `equation` environment, avoid `\[...\]`
- Create figures with TikZ/pgfplot
- Never comment out large chunks of code - delete or highlight instead
