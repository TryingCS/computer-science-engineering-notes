---
{"dg-publish":true,"permalink":"/subjects/technical-writing/la-te-x-crash-course/","dg-note-properties":{}}
---

#technicalWritng 

***

Latex is a document preparation system. You write plain text with commands, then compile it into a beautiful PDF.

Example:

```latex
\textbf{Hello}
```

produces: **Hello**

---

# 1. Installation and Editors

## Option A: Overleaf — easiest

Overleaf works in your browser.

Website: https://www.overleaf.com

Good for:

- your laptop
- your Xiaomi Redmi Note 8 browser
- no installation
- automatic compilation

Steps:

1. Create an account.
2. Click **New Project**.
3. Choose **Blank Project**.
4. Write your LaTeX code.
5. Click **Recompile**.

---

## Option B: Linux Mint + TeXstudio

Install LaTeX and TeXstudio:

```bash
sudo apt update
sudo apt install texlive-latex-base texlive-latex-recommended texlive-latex-extra texlive-fonts-recommended texlive-bibtex-extra texstudio
```

Optional full version, large download:

```bash
sudo apt install texlive-full
```

Open TeXstudio:

```bash
texstudio
```

Basic workflow:

1. Create `main.tex`.
2. Write LaTeX code.
3. Click **Build & View**.
4. PDF appears.

---

# 2. Basic LaTeX Syntax

LaTeX uses commands starting with a backslash:

```latex
\command
```

Required arguments use curly braces:

```latex
\command{argument}
```

Optional arguments use square brackets:

```latex
\command[option]{argument}
```

Environments have a beginning and an end:

```latex
\begin{environment}
content
\end{environment}
```

Comments start with `%`:

```latex
This is visible.
% This is a comment.
```

Important special characters:

| Symbol | Meaning |
|---|---|
| `\` | starts a command |
| `{ }` | groups arguments |
| `[ ]` | optional arguments |
| `%` | comment |
| `$` | math mode |
| `&` | table/tabular separator |
| `\\` | new line |
| `~` | non-breaking space |

To print special characters, escape them:

```latex
\& \% \$ \_ \{ \}
```

---

# 3. Document Construction: The Skeleton

Every LaTeX document needs this structure:

```latex
\documentclass{article}

\begin{document}

Hello, LaTeX!

\end{document}
```

Explanation:

```latex
\documentclass{article}
```

chooses the document type.

Common classes:

```latex
article
report
book
beamer
```

Everything between:

```latex
\begin{document}
...
\end{document}
```

is visible in the PDF.

---

## A more complete skeleton

```latex
\documentclass[12pt,a4paper]{article}

\usepackage[utf8]{inputenc}
\usepackage[T1]{fontenc}
\usepackage{graphicx}
\usepackage{amsmath}

\title{My First Document}
\author{Your Name}
\date{\today}

\begin{document}

\maketitle

Hello, LaTeX!

\end{document}
```

Meaning:

| Command | Purpose |
|---|---|
| `\documentclass` | document type |
| `\usepackage` | adds features |
| `\title` | document title |
| `\author` | author name |
| `\date` | date |
| `\maketitle` | prints title block |

---

# 4. Text Formatting

## Bold

```latex
\textbf{bold text}
```

## Italic

```latex
\textit{italic text}
```

## Underline

```latex
\underline{underlined text}
```

## Small caps

```latex
\textsc{small caps}
```

## Emphasis

```latex
\emph{emphasized text}
```

Example:

```latex
This is \textbf{bold}, this is \textit{italic}, and this is \emph{emphasized}.
```

---

# 5. Lists

## Bullet list

```latex
\begin{itemize}
  \item First item
  \item Second item
  \item Third item
\end{itemize}
```

## Numbered list

```latex
\begin{enumerate}
  \item First step
  \item Second step
  \item Third step
\end{enumerate}
```

## Description list

```latex
\begin{description}
  \item[LaTeX] A typesetting system
  \item[PDF] Portable Document Format
  \item[BibTeX] Reference manager
\end{description}
```

---

# 6. Structuring Long Documents

Use sections to organize your document.

```latex
\section{Introduction}
Some text.

\section{Method}
More text.

\subsection{Data Collection}
Details here.

\subsection{Analysis}
More details.
```

Available hierarchy commands:

```latex
\part{...}
\chapter{...}
\section{...}
\subsection{...}
\subsubsection{...}
\paragraph{...}
\subparagraph{...}
```

Note:

`article` does not usually use `\chapter`.

`report` and `book` support `\chapter`.

---

# 7. Table of Contents

Add this where you want the table of contents:

```latex
\tableofcontents
```

Full example:

```latex
\documentclass{article}

\begin{document}

\tableofcontents
\newpage

\section{Introduction}
Text.

\section{Method}
Text.

\subsection{Step One}
Text.

\end{document}
```

Important:

You may need to compile twice for the table of contents to update.

---

# 8. Cross-Referencing with `\label` and `\ref`

You can refer dynamically to sections, figures, tables, and equations.

## Section reference

```latex
\section{Introduction}
\label{sec:intro}

See Section~\ref{sec:intro}.
```

The `~` prevents a line break between “Section” and the number.

---

## Figure reference

```latex
\begin{figure}
  \centering
  \includegraphics[width=0.5\textwidth]{image.png}
  \caption{My image}
  \label{fig:myimage}
\end{figure}

See Figure~\ref{fig:myimage}.
```

---

## Table reference

```latex
\begin{table}
  \centering
  \caption{My table}
  \label{tab:mytable}
  \begin{tabular}{cc}
    A & B \\
    1 & 2
  \end{tabular}
\end{table}

See Table~\ref{tab:mytable}.
```

---

## Equation reference

Use `\label` inside the equation environment.

```latex
\begin{equation}
E = mc^2
\label{eq:einstein}
\end{equation}

See Equation~\eqref{eq:einstein}.
```

`\eqref` automatically adds parentheses around the equation number.

---

# 9. Tables

## Basic `tabular` environment

```latex
\begin{tabular}{lcr}
Name & Age & City \\
Ali & 20 & Paris \\
Sara & 22 & Lyon
\end{tabular}
```

Column alignment:

| Symbol | Meaning |
|---|---|
| `l` | left aligned |
| `c` | centered |
| `r` | right aligned |
| `p{3cm}` | paragraph column with fixed width |

Rows end with:

```latex
\\
```

Cells are separated by:

```latex
&
```

---

## Lines inside tables

Horizontal line:

```latex
\hline
```

Example:

```latex
\begin{tabular}{|l|c|}
\hline
Name & Age \\
\hline
Ali & 20 \\
Sara & 22 \\
\hline
\end{tabular}
```

Better style: use `booktabs`.

```latex
\usepackage{booktabs}
```

Then use:

```latex
\toprule
\midrule
\bottomrule
```

instead of many `\hline`.

---

## Full table with caption

Tables usually go inside a floating `table` environment.

```latex
\begin{table}[htbp]
  \centering
  \caption{Student information}
  \label{tab:students}
  \begin{tabular}{lcc}
    \toprule
    Name & Age & City \\
    \midrule
    Ali & 20 & Paris \\
    Sara & 22 & Lyon \\
    \bottomrule
  \end{tabular}
\end{table}
```

Important:

Put `\label` after `\caption`.

---

## Table positioning options

```latex
[htbp]
```

Meaning:

| Letter | Meaning |
|---|---|
| `h` | here |
| `t` | top of page |
| `b` | bottom of page |
| `p` | separate float page |
| `!` | override LaTeX restrictions |

Example:

```latex
\begin{table}[!htbp]
```

---

# 10. Images

You need:

```latex
\usepackage{graphicx}
```

## Insert an image

```latex
\includegraphics{image.png}
```

With width:

```latex
\includegraphics[width=0.5\textwidth]{image.png}
```

Common image formats:

```text
.png
.jpg
.pdf
```

---

## Figure environment

Use `figure` to make the image float and add a caption.

```latex
\begin{figure}[htbp]
  \centering
  \includegraphics[width=0.6\textwidth]{image.png}
  \caption{My figure caption}
  \label{fig:myfigure}
\end{figure}
```

Then refer to it:

```latex
See Figure~\ref{fig:myfigure}.
```

---

## If you do not have an image yet

You can use a placeholder image by adding:

```latex
\usepackage{mwe}
```

Then use:

```latex
\includegraphics[width=0.6\textwidth]{example-image}
```

Later replace it with your own image.

---

# 11. Mathematical Equations

You need:

```latex
\usepackage{amsmath}
```

For extra symbols:

```latex
\usepackage{amssymb}
```

---

## Inline math

Inline math appears inside text.

```latex
The equation $E = mc^2$ is famous.
```

Use one dollar sign:

```latex
$...$
```

---

## Display math without numbering

```latex
\[
E = mc^2
\]
```

---

## Numbered equation

```latex
\begin{equation}
E = mc^2
\end{equation}
```

With label:

```latex
\begin{equation}
E = mc^2
\label{eq:energy}
\end{equation}

Equation~\eqref{eq:energy} is famous.
```

---

## Multiple aligned equations

```latex
\begin{align}
a &= b + c \\
d &= e + f
\end{align}
```

Without numbers:

```latex
\begin{align*}
a &= b + c \\
d &= e + f
\end{align*}
```

---

## Fractions

```latex
\[
\frac{a}{b}
\]
```

Example:

```latex
\[
\frac{1}{2}
\]
```

---

## Indices and exponents

Index:

```latex
x_i
```

Exponent:

```latex
x^2
```

Both:

```latex
x_i^2
```

Example:

```latex
\[
a_i^2 + b_i^2 = c_i^2
\]
```

---

## Square roots

```latex
\[
\sqrt{x}
\]
```

With index:

```latex
\[
\sqrt[3]{x}
\]
```

---

## Greek letters

```latex
\[
\alpha, \beta, \gamma, \Delta, \lambda, \pi
\]
```

---

## Sums and integrals

Sum:

```latex
\[
\sum_{i=1}^{n} x_i
\]
```

Integral:

```latex
\[
\int_0^1 x^2 \, dx
\]
```

---

## Matrices

Plain matrix:

```latex
\[
\begin{matrix}
a & b \\
c & d
\end{matrix}
\]
```

Matrix with parentheses:

```latex
\[
\begin{pmatrix}
a & b \\
c & d
\end{pmatrix}
\]
```

Matrix with square brackets:

```latex
\[
\begin{bmatrix}
a & b \\
c & d
\end{bmatrix}
\]
```

Example:

```latex
\[
A =
\begin{bmatrix}
1 & 2 \\
3 & 4
\end{bmatrix}
\]
```

---

# 12. Bibliography with BibTeX

BibTeX helps you manage references.

You need two files:

```text
main.tex
refs.bib
```

Both should be in the same folder/project.

---

## Step 1: Create `refs.bib`

Example:

```bibtex
@book{knuth1984,
  author    = {Donald E. Knuth},
  title     = {The TeXbook},
  publisher = {Addison-Wesley},
  year      = {1984}
}

@book{lamport1994,
  author    = {Leslie Lamport},
  title     = {LaTeX: A Document Preparation System},
  publisher = {Addison-Wesley},
  year      = {1994}
}

@article{einstein1905,
  author  = {Albert Einstein},
  title   = {On the Electrodynamics of Moving Bodies},
  journal = {Annalen der Physik},
  volume  = {17},
  pages   = {891--921},
  year    = {1905}
}
```

Each entry has a citation key:

```text
knuth1984
lamport1994
einstein1905
```

You will use these keys in `\cite`.

---

## Step 2: Cite in your LaTeX document

```latex
LaTeX was described by Lamport~\cite{lamport1994}.
Knuth created TeX~\cite{knuth1984}.
```

Multiple citations:

```latex
\cite{knuth1984,lamport1994}
```

---

## Step 3: Print the bibliography

At the end of your document:

```latex
\bibliographystyle{plain}
\bibliography{refs}
```

If your file is called `refs.bib`, write:

```latex
\bibliography{refs}
```

Do not write `.bib`.

---

## Compilation sequence

For BibTeX, compile in this order:

```bash
pdflatex main
bibtex main
pdflatex main
pdflatex main
```

In Overleaf, this is usually automatic.

In TeXstudio, use **Build & View**. If references do not appear, run BibTeX once, then build again.

---

# 13. Complete Tiny Example

Create `main.tex`:

```latex
\documentclass{article}

\usepackage[utf8]{inputenc}
\usepackage[T1]{fontenc}
\usepackage{graphicx}
\usepackage{amsmath}
\usepackage{amssymb}
\usepackage{booktabs}
\usepackage{mwe}

\title{Tiny Example}
\author{Student}
\date{\today}

\begin{document}

\maketitle

\tableofcontents
\newpage

\section{Introduction}
This is a simple LaTeX document.

\section{Mathematics}
An equation:
\begin{equation}
E = mc^2
\label{eq:energy}
\end{equation}

See Equation~\eqref{eq:energy}.

\section{Table}
See Table~\ref{tab:data}.

\begin{table}[htbp]
  \centering
  \caption{Data}
  \label{tab:data}
  \begin{tabular}{lcc}
    \toprule
    Item & Length (cm) & Mass (g) \\
    \midrule
    A & 10.0 & 5.0 \\
    B & 7.5 & 3.2 \\
    \bottomrule
  \end{tabular}
\end{table}

\section{Figure}
See Figure~\ref{fig:sample}.

\begin{figure}[htbp]
  \centering
  \includegraphics[width=0.5\textwidth]{example-image}
  \caption{Sample figure}
  \label{fig:sample}
\end{figure}

\bibliographystyle{plain}
\bibliography{refs}

\end{document}
```

Create `refs.bib`:

```bibtex
@book{knuth1984,
  author    = {Donald E. Knuth},
  title     = {The TeXbook},
  publisher = {Addison-Wesley},
  year      = {1984}
}

@book{lamport1994,
  author    = {Leslie Lamport},
  title     = {LaTeX: A Document Preparation System},
  publisher = {Addison-Wesley},
  year      = {1994}
}
```

Then compile.

---

# 14. Exercise 5: 2-Page Mini-Document

Now we build a mini scientific report.

It includes:

- introduction
- sections
- table of contents
- formatted text
- list
- table
- figure
- equation
- bibliography
- cross-references

---

## File 1: `main.tex`

```latex
\documentclass[12pt,a4paper]{article}

% Basic packages
\usepackage[utf8]{inputenc}
\usepackage[T1]{fontenc}

% Packages for images, math, and tables
\usepackage{graphicx}
\usepackage{amsmath}
\usepackage{amssymb}
\usepackage{booktabs}

% This package provides example-image.
% Remove it later if you use your own image.
\usepackage{mwe}

\title{Mini Scientific Report}
\author{Your Name}
\date{\today}

\begin{document}

\maketitle

\begin{abstract}
This mini-report shows the basic use of LaTeX. It includes text structure,
a table, a figure, mathematical equations, and a bibliography.
\end{abstract}

\tableofcontents
\newpage

\section{Introduction}
\label{sec:introduction}

LaTeX is a powerful system for writing scientific documents.
It is especially useful for \textbf{mathematics}, \textit{tables},
and consistent document structure.

The main goals of this mini-report are:

\begin{itemize}
  \item Show basic text formatting.
  \item Create a structured document.
  \item Insert a table and a figure.
  \item Write mathematical equations.
  \item Add references using BibTeX.
\end{itemize}

The rest of this report is organized as follows.
Section~\ref{sec:method} describes the method.
Section~\ref{sec:results} presents the results.

\section{Method}
\label{sec:method}

We use a simple mathematical model.
The quadratic formula is given in Equation~\eqref{eq:quadratic}.

\begin{equation}
x = \frac{-b \pm \sqrt{b^2 - 4ac}}{2a}
\label{eq:quadratic}
\end{equation}

We can also write matrices. For example:

\[
A =
\begin{bmatrix}
1 & 2 \\
3 & 4
\end{bmatrix}
\]

A matrix with parentheses:

\[
B =
\begin{pmatrix}
x_1 & x_2 \\
y_1 & y_2
\end{pmatrix}
\]

An aligned system of equations:

\begin{align}
a &= b + c \\
d &= e + f \\
g &= h + i
\end{align}

\section{Results}
\label{sec:results}

Table~\ref{tab:samples} shows some fake experimental results.

\begin{table}[htbp]
  \centering
  \caption{Sample measurements}
  \label{tab:samples}
  \begin{tabular}{lccc}
    \toprule
    Sample & Length (cm) & Mass (g) & Temperature (°C) \\
    \midrule
    A & 10.2 & 5.0 & 20.5 \\
    B & 7.5 & 3.2 & 21.0 \\
    C & 12.8 & 8.1 & 19.8 \\
    \bottomrule
  \end{tabular}
\end{table}

Figure~\ref{fig:sample-figure} shows a placeholder image.

\begin{figure}[htbp]
  \centering
  \includegraphics[width=0.6\textwidth]{example-image}
  \caption{Placeholder figure}
  \label{fig:sample-figure}
\end{figure}

As shown in Table~\ref{tab:samples}, sample C has the largest length.
This is only an example.

\section{Conclusion}
\label{sec:conclusion}

This document demonstrated the basics of LaTeX:
sections, lists, tables, figures, equations, and bibliography.
For more details, see Knuth~\cite{knuth1984}
and Lamport~\cite{lamport1994}.

\newpage

\bibliographystyle{plain}
\bibliography{refs}

\end{document}
```

---

## File 2: `refs.bib`

```bibtex
@book{knuth1984,
  author    = {Donald E. Knuth},
  title     = {The TeXbook},
  publisher = {Addison-Wesley},
  year      = {1984},
  address   = {Reading, Massachusetts}
}

@book{lamport1994,
  author    = {Leslie Lamport},
  title     = {LaTeX: A Document Preparation System},
  publisher = {Addison-Wesley},
  year      = {1994},
  edition   = {2nd},
  address   = {Reading, Massachusetts}
}

@article{einstein1905,
  author  = {Albert Einstein},
  title   = {Zur Elektrodynamik bewegter Körper},
  journal = {Annalen der Physik},
  volume  = {322},
  number  = {10},
  pages   = {891--921},
  year    = {1905}
}
```

---

# 15. How to Make It 2 Pages

The code above can become around two pages depending on spacing.

If you need exactly two pages, you can add:

```latex
\newpage
```

before a major section.

Example:

```latex
\newpage
\section{Results}
```

Or add more text.

Do not worry too much about exact page count at first. Focus on correct structure.

---

# 16. Final Mini Scientific Report Checklist

Use this checklist for your project.

## Structure

- [ ] `\documentclass{article}`
- [ ] `\begin{document}`
- [ ] `\end{document}`
- [ ] `\title`
- [ ] `\author`
- [ ] `\date`
- [ ] `\maketitle`

## Sections

- [ ] `\section`
- [ ] `\subsection`
- [ ] `\tableofcontents`

## Formatting

- [ ] `\textbf`
- [ ] `\textit`
- [ ] `itemize` or `enumerate`

## Table

- [ ] `table` environment
- [ ] `tabular` environment
- [ ] `\caption`
- [ ] `\label`
- [ ] `\ref`

## Figure

- [ ] `figure` environment
- [ ] `\includegraphics`
- [ ] `\caption`
- [ ] `\label`
- [ ] `\ref`

## Math

- [ ] inline math: `$...$`
- [ ] display math: `\[...\]`
- [ ] numbered equation: `equation`
- [ ] fraction: `\frac{}{}`
- [ ] index: `x_i`
- [ ] exponent: `x^2`
- [ ] matrix: `bmatrix` or `pmatrix`

## Bibliography

- [ ] `refs.bib`
- [ ] `\cite{...}`
- [ ] `\bibliographystyle{plain}`
- [ ] `\bibliography{refs}`

---

# 17. Common Beginner Mistakes

## Missing `$` in math

Wrong:

```latex
E = mc^2
```

Correct:

```latex
$E = mc^2$
```

---

## Missing closing brace

Wrong:

```latex
\textbf{bold
```

Correct:

```latex
\textbf{bold}
```

---

## Missing `\end{...}`

Wrong:

```latex
\begin{itemize}
\item One
```

Correct:

```latex
\begin{itemize}
\item One
\end{itemize}
```

---

## Label before caption

Wrong:

```latex
\label{tab:mytable}
\caption{My caption}
```

Correct:

```latex
\caption{My caption}
\label{tab:mytable}
```

---

## Forgetting to compile twice

If references show as `??`, compile again.

For bibliography:

```bash
pdflatex main
bibtex main
pdflatex main
pdflatex main
```

---

## Wrong file path for image

If your image is:

```text
images/photo.png
```

then use:

```latex
\includegraphics{images/photo.png}
```

---

# 18. Very Simple Learning Path

Do this in order:

1. Make a title and one paragraph.
2. Add sections.
3. Add a list.
4. Add `\tableofcontents`.
5. Add one table.
6. Add one figure.
7. Add one equation.
8. Add `refs.bib`.
9. Use `\cite`.
10. Compile until bibliography appears.

---

# 19. Minimal Template You Can Reuse

```latex
\documentclass[12pt,a4paper]{article}

\usepackage[utf8]{inputenc}
\usepackage[T1]{fontenc}
\usepackage{graphicx}
\usepackage{amsmath}
\usepackage{amssymb}
\usepackage{booktabs}

\title{Report Title}
\author{Your Name}
\date{\today}

\begin{document}

\maketitle
\tableofcontents
\newpage

\section{Introduction}
Your text here.

\section{Method}
Your text here.

\section{Results}
Your text here.

\section{Conclusion}
Your text here.

\bibliographystyle{plain}
\bibliography{refs}

\end{document}
```

Then create `refs.bib`:

```bibtex
@book{example2026,
  author    = {Author Name},
  title     = {Book Title},
  publisher = {Publisher},
  year      = {2026}
}
```

Cite it:

```latex
See \cite{example2026}.
```

---

# 20. LaTeX Command Cheat Sheet

| Task | Command |
|---|---|
| Bold | `\textbf{...}` |
| Italic | `\textit{...}` |
| Section | `\section{...}` |
| Subsection | `\subsection{...}` |
| New page | `\newpage` |
| Table of contents | `\tableofcontents` |
| Label | `\label{...}` |
| Reference | `\ref{...}` |
| Equation reference | `\eqref{...}` |
| Inline math | `$...$` |
| Display math | `\[...\]` |
| Numbered equation | `\begin{equation} ... \end{equation}` |
| Fraction | `\frac{a}{b}` |
| Subscript | `x_i` |
| Superscript | `x^2` |
| Square root | `\sqrt{x}` |
| Sum | `\sum_{i=1}^{n}` |
| Integral | `\int_a^b` |
| Matrix | `\begin{bmatrix} ... \end{bmatrix}` |
| Citation | `\cite{key}` |
| Bibliography | `\bibliography{refs}` |
