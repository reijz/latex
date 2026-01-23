# LaTeX Templates for Academic Papers

This repository contains LaTeX templates for writing academic papers.

## Repository Structure

```
latex/
  |-- informs-template/     # INFORMS journal submissions (flat structure)
  |-- common-template/      # General templates (flat structure)
  |-- latex-coding-style.md # LaTeX coding guidelines
```

## Getting Started

### For INFORMS Journal Submissions

1. Copy the `informs-template/` folder to your project
2. Rename `template-informs.tex` to your paper name
3. Compile with pdflatex + bibtex

```bash
cp -r informs-template/ my-informs-paper/
cd my-informs-paper/
mv template-informs.tex my-paper.tex
pdflatex my-paper.tex && bibtex my-paper && pdflatex my-paper.tex && pdflatex my-paper.tex
```

Change the journal by modifying the document class option:

```latex
\documentclass[opre,sglanonrev]{informs4}  % Operations Research
\documentclass[mnsc,dblanonrev]{informs4}  % Management Science
\documentclass[moor,sglanonrev]{informs4}  % Math of OR
```

Review options:
- `sglanonrev` - Single anonymous (non-blind)
- `dblanonrev` - Double anonymous (blind)

### For General Papers (Working Papers, Course Projects)

1. Copy the `common-template/` folder to your project
2. Use `template-plain.tex` for general papers
3. Use `template-RGC.tex` for RGC grant proposals

```bash
cp -r common-template/ my-paper/
cd my-paper/
mv template-plain.tex my-paper.tex
pdflatex my-paper.tex && bibtex my-paper && pdflatex my-paper.tex && pdflatex my-paper.tex
```

## Template Contents

### informs-template/
```
informs-template/
  |-- template-informs.tex  # Main template
  |-- preamble.tex          # Packages, macros (supplements informs4.cls)
  |-- informs4.cls          # Document class (fonts, hyperref, natbib, theorems)
  |-- informs2014.bst       # Bibliography style
  |-- ref.bib               # Sample bibliography
  |-- tikz/                 # TikZ figures (optional)
  |     |-- setup.tex       # TikZ/pgfplots packages
  |     |-- figure-*.tex    # Figure source files
  |-- pictures/             # Other graphics (JPG, PNG, PDF)
```

### common-template/
```
common-template/
  |-- template-plain.tex    # General paper template
  |-- template-RGC.tex      # RGC grant proposal template
  |-- preamble.tex          # Packages, theorems, macros
  |-- ref.bib               # Sample bibliography
  |-- tikz/                 # TikZ figures (optional)
  |     |-- setup.tex       # TikZ/pgfplots packages
  |     |-- figure-*.tex    # Figure source files
  |-- pictures/             # Other graphics (JPG, PNG, PDF)
```

### Preamble Contents

Both templates use a `preamble.tex` file that provides:

**Packages:**
- Math: amsmath, amssymb, amsthm, mathtools, mathrsfs, bm
- Tables: booktabs, multirow, array
- Figures: graphicx, caption, subcaption
- Typography: microtype, babel, setspace
- Hyperlinks: hyperref, bookmark
- Bibliography: natbib
- Algorithms: algorithm2e (optional)

**Theorem environments:**
- theorem, lemma, proposition, corollary
- definition, assumption, remark, example

**Common macros:**
- Number sets: `\R`, `\Z`, `\N`, `\Q`, `\C`
- Probability: `\E`, `\Var`, `\Cov`, `\pr`, `\ind{}`
- Operators: `\argmin`, `\argmax`
- Brackets: `\abs{}`, `\norm{}`, `\inner{}{}`, `\floor{}`, `\ceil{}`, `\pos{}`
- Convergence: `\dto`, `\pto`, `\asto`

**Note:** The INFORMS template's `preamble.tex` is lighter because `informs4.cls` already includes many packages.

### TikZ Support

TikZ packages are in `tikz/setup.tex`. If your paper doesn't use TikZ figures, remove this line from your template:

```latex
\input{tikz/setup.tex}
```

This reduces compilation time and avoids loading unnecessary packages.

## Bibliography

The `ref.bib` files are **samples**. You should:

1. Create your own `.bib` file for your research project, or
2. Replace the contents with your own references

Keep only the references you actually cite in your paper.

## Coding Style

See [latex-coding-style.md](latex-coding-style.md) for guidelines on writing clean, maintainable LaTeX code.

Key points:
- One sentence per line (helps with git diff and backward search)
- Use proper labeling: `\label{eq:name}`, `\label{thm:name}`, `\label{sec:name}`
- Use `equation` environment, avoid `\[...\]`
- Create figures with TikZ/pgfplot
- Never comment out large chunks of code - delete or highlight instead
