# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository Overview

This repository contains a LaTeX thesis investigating fairness in Multi-Agent Artificial Intelligence (MAAI) systems. The thesis replicates the fairness experiments of Frohlich & Oppenheimer (1992), originally conducted with human participants, using multiple AI agents.

## Building the Document

### Compile the thesis
```bash
pdflatex main.tex
bibtex main
pdflatex main.tex
pdflatex main.tex
```

The output will be `main.pdf`.

### Quick compilation (without bibliography updates)
```bash
pdflatex main.tex
```

## Document Structure

The thesis follows a modular structure where each chapter is maintained in a separate `.tex` file:

- `main.tex` - Master document that includes all chapters and handles document setup
- `90_Cover.tex` - Cover page
- `00_Abstract.tex` - Abstract
- `91_Affirmation.tex` - Affirmation/declaration page
- `10_Abbreviations.tex` - List of abbreviations
- `01_Introduction.tex` - Introduction chapter
- `02_Background.tex` - Background and literature review
- `03_Methodology.tex` - Research design and methodology (includes experimental design and statistical testing procedures)
- `04_Results.tex` - Experimental results
- `05_Discussion.tex` - Discussion of findings
- `06_Conclusion.tex` - Conclusion
- `07_Appendix.tex` - Appendix (currently commented out in main.tex)
- `references.bib` - Bibliography file containing all citations

### Key Content Areas

**Methodology (03_Methodology.tex)** contains:
- Baseline experiment design by Frohlich & Oppenheimer
- MAAI replication procedure
- Technical architecture (4 layers: Initialization, Orchestration, AI Agent Management, Data)
- Statistical testing procedures for 4 hypotheses

**Research Hypotheses:**
1. AI agents exhibit different fairness judgments than humans
2. LLM origin (American vs Chinese) affects fairness judgments
3. Intelligence asymmetries create manipulation vulnerabilities
4. Input language (English/Mandarin/Spanish) affects outcomes

## LaTeX Conventions

### Document Class and Formatting
- 12pt font, one-sided article class
- A4 paper with 3cm margins (left, right, top) and 4cm bottom
- One-and-a-half line spacing (`\onehalfspacing`)
- No paragraph indentation (`\parindent` set to 0)
- Page numbers in header (right side)

### Custom Commands
- `\cmark` - Checkmark symbol (✓)
- `\xmark` - X mark symbol (✗)
- `\nmark` - Neutral mark symbol
- `\boldcheckmark` - Bold checkmark

### Table Formatting
- Uses `booktabs` package for professional tables (use `\toprule`, `\midrule`, `\bottomrule`)
- Custom column types defined: `P{width}` (centered), `L{width}` (left-aligned)
- Array stretch set to 1.25 for better readability
- Tables should include captions with short and long forms: `\caption[Short]{Long description}`

### Figures
- Stored in `Figures/` directory
- Includes both architecture diagrams (`.jpg`, `.png`) and results visualizations
- Use `\includegraphics[width=...]` to control sizing
- Always include descriptive captions with `\caption[Short]{Long description}`
- Reference figures using `\ref{fig:label}` or `\Cref{fig:label}` (cleveref package)

### Citations
- Uses `natbib` package with `apalike` style
- Cite using `\citet{}` for textual citations (Author (Year))
- Cite using `\citep{}` for parenthetical citations ((Author, Year))
- All references in `references.bib`

### Cross-References
- Uses `cleveref` package for smart references
- Use `\Cref{label}` to automatically include reference type (e.g., "Table 1", "Figure 2")
- Use `\label{sec:name}` for sections, `\label{tab:name}` for tables, `\label{fig:name}` for figures

### Lists
- No item separation (`noitemsep`) and no top separation (`topsep=0pt`) for compact lists
- Use `\begin{enumerate}` for numbered lists
- Use `\begin{itemize}` for bullet lists

## Working with Content

### Adding a New Section
Sections are added directly within the chapter files. Follow the existing structure:
```latex
\section{Section Title}
\label{sec:descriptive_label}
Content here...

\subsection{Subsection Title}
Content here...
```

### Adding Citations
1. Add the BibTeX entry to `references.bib`
2. Use `\citep{key}` or `\citet{key}` in the text
3. Recompile with bibtex: `pdflatex main.tex && bibtex main && pdflatex main.tex && pdflatex main.tex`

### Adding Tables
Follow this pattern:
```latex
\begin{table}[!ht]
\centering
\caption[Short caption for list]{Full descriptive caption}
\label{tab:descriptive_label}
\begin{tabular}{lrr}
\toprule
Header 1 & Header 2 & Header 3 \\
\midrule
Data row 1 & value & value \\
Data row 2 & value & value \\
\bottomrule
\end{tabular}
\end{table}
```

### Adding Figures
Follow this pattern:
```latex
\begin{figure}[!ht]
    \centering
    \includegraphics[width=0.8\linewidth]{Figures/filename.png}
    \caption[Short caption for list]{Full descriptive caption}
    \label{fig:descriptive_label}
\end{figure}
```

## Language and Babel

The document supports both English (primary) and German (`ngerman`) through the babel package. English is the active language throughout the thesis.

## Mathematical Notation

The thesis includes formal hypothesis testing with mathematical notation:
- Use `\[ ... \]` for displayed equations
- Use `$...$` for inline math
- Common notation: `\mathcal{C}` for sets, `\exists` and `\forall` for quantifiers
- Probability notation: `P_{\text{condition}}(outcome)`

## Imporant for writing
Do not use bold or cursive formatting, unless absolutely necessary
Use American English 
## Genearal Writing tipps
Yoda

Use "that" without the preceding comma if the following information is essential for understanding the sentence. Use ", which" in case the following information is nonessential.
Always use "because" instead of "since" to avoid ambiguity
Refrain from writing phrases like "we test this". Be more specific: "we test this relationship."

Use American English (AE)---it is the most typical version of scientific writing.
Try not to be colloquial (coll) and adapt an academic writing style. Tools like DeepLWrite can help you with that, where you can enable "academic" as a style (top right).
Make sure you review your paper before submission with an editing tool like Grammarly (which is free for many universities).
Regarding tenses: You can either follow precisely these rules for tenses. Or just use the present tense throughout your whole paper. The decision is yours; there is nothing in between. My preferred choice is the latter.
Always use the package cleveref for cross-referencing of figures, chapters, tables, etc., with \Cref
If you are referencing a precise figure/table/section, it is spelled in upper case, e.g., Figure 1 (use \Cref, not \cref)
If your figure or table is on a different page than the cross-reference: Use \pageref
The dash ('—') ('---' in LaTeX) has no spaces before or after.
Do not use " for quotes in LaTeX, but `` and ''
You can try to force a figure or table to a certain position by using 'htbp', e.g. \begin{figure}[htbp]. h = here, t = top, b = bottom, p = page. If you really try to force a position, you can also try adding the "!".

## Special Files

- `todo.tex` - Contains TODO items or notes (not included in main compilation)
- `old.tex`, `old_2.tex`, `old_3.tex` - Archived versions of previous drafts