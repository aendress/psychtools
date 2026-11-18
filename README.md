# psychtools — LaTeX Macros for Psychology Manuscripts

`psychtools` is a LaTeX package providing convenience macros for empirical
psychology and cognitive science manuscripts. It covers:

- **Statistical notation**: compact, italic commands for common test statistics
  and effect sizes (APA style), enabled with the `statsmacros` option
- **Supplementary-materials appendix**: `S`-prefixed page, section, figure, and
  table numbering with an optional local table of contents
- **Draft editing aids**: conditional footnotes and section headers that are
  visible (and coloured red) during writing but can be hidden entirely for
  submission with a single package option
- **Author masking**: wrap institution names and other identifying details so
  they print normally but become a neutral redaction marker in the
  anonymous-review build
- **Citation shortcuts** for `apacite` users

## Installation

### Via TeX Live / MiKTeX (after CTAN acceptance)
```
tlmgr install psychtools
```

### Manually
Copy `psychtools.sty` to your local texmf tree, e.g.:
```
~/texmf/tex/latex/psychtools/psychtools.sty
```
Then run `texhash` (TeX Live) or `initexmf --update-fndb` (MiKTeX).

## Usage

```latex
\usepackage{psychtools}
% or with options:
\usepackage[statsmacros,excludedetails,appendixtoc]{psychtools}
```

See `psychtools.pdf` for the full documentation and `howto.pdf` for a
worked example using all commands, based on a simulated serial-position-effect
experiment.

## Package options

**`includedetails` / `excludedetails`** (default: `includedetails`)  
Show or hide *draft content* — footnotes and section headers that are marked
for removal before submission (`\footnotewithdetails`, `\draftsection`, etc.).
Switch to `excludedetails` when preparing the final submission and all draft
content disappears silently.

**`appendixtoc`** (default: off)  
Generate a separate table of contents for the supplementary-materials section.
When active, supplementary sections are suppressed from the main document TOC;
instead, a local TOC is printed immediately after the supplementary-materials
header produced by `\myappendix`.

**`nocolorize`** (default: off)  
Draft content is coloured red by default so it is easy to spot during writing.
`nocolorize` suppresses this colouring while keeping the content visible.

**`nocitecommands`** (default: off)  
Disable the `apacite` citation helpers (`\citeeg`, `\cites`). Use this if you
are not using `apacite` and wish to define these command names yourself.

**`statsmacros`** (default: off)  
Enable the short statistical-notation commands (`\T`, `\F`, `\Z`, `\p`, `\M`,
`\SD`, `\SE`, `\D`, `\CI`, `\et`, `\etp`, `\U`, `\W`). These are off by
default because their single-letter names may conflict with math or font
packages. Request this option only after verifying there are no conflicts with
other packages you load.

**`maskauthor` / `nomaskauthor`** (default: `nomaskauthor`)  
Turn *author masking* on or off (see [Author masking](#author-masking-anonymous-review)).
With `maskauthor`, `\maskaffiliation` and `\maskdetail` print a fixed redaction
marker instead of their argument. Masking is also enabled automatically when the
document class is `apa6` loaded with its own `mask` option, so
`\documentclass[...,mask]{apa6}` needs no extra option; `nomaskauthor` forces it
off even then.

## Quick reference

### Statistical notation (requires `statsmacros`)
| Command | Output | Meaning |
|---------|--------|---------|
| `\T` | *t* | Student's *t* |
| `\F` | *F* | *F* ratio |
| `\Z` | *Z* | *Z* score |
| `\p` | *p* | *p* value |
| `\M` | *M* | Mean |
| `\SD` | *SD* | Standard deviation |
| `\SE` | *SE* | Standard error |
| `\D` | Cohen's *d* | Cohen's *d* |
| `\CI` | *CI*₉₅ | 95% confidence interval |
| `\et` | η² | Eta-squared |
| `\etp` | η²ₚ | Partial eta-squared |
| `\U` | *U* | Mann–Whitney *U* |
| `\W` | *W* | Wilcoxon *W* |

### Supplementary materials appendix
```latex
\renewcommand{\appendixname}{Supplementary Online Materials}
\myappendix          % reset numbering, print header
\appsection{...}     % section inside the appendix (adds page break from 2nd onwards)
```

### Draft aids
```latex
\draftsection{...}          % red section header; hidden with excludedetails
\draftsubsection{...}       % same for subsections
\draftsubsubsection{...}    % same for subsubsections
\footnotewithdetails{...}   % red footnote; hidden with excludedetails
\colorize{...}              % mark revised text red (reviewer responses); pass-through with nocolorize
\begin{colorizeblock} ... \end{colorizeblock}  % same for longer passages (whole sections, figures)
```

### Author masking (anonymous review)
```latex
\maskaffiliation{City St George's, University of London}  % institution name
\maskdetail{ETH2223-1027}                                 % approval/grant number, project code
```
Used inline at each mention (like apa6's `\maskcite`). Both print their argument
verbatim, or `[affiliation removed for masked review]` /
`[identifying detail removed for masked review]` when masking is active
(`maskauthor` option, or `apa6` with `mask`).

### Citation helpers (apacite)
```latex
\citeeg{key}   % (e.g., Author Year)
\cites{key}    % Author's Year
```

### Miscellaneous
```latex
\includesubgraphics{A}{filename}   % subfigure with bold panel label, no sub-caption
\protectedemail{user@example.org}  % email in a TikZ node (deters scrapers)
```

## License

LPPL 1.3c — see `LICENSE`.

## Author

Ansgar Endress  
<ansgar.endress@m4x.org>
