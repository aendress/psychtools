# psychtools — LaTeX Macros for Psychology Manuscripts

`psychtools` is a LaTeX package providing convenience macros for empirical
psychology and cognitive science manuscripts. It covers statistical notation,
supplementary-materials appendix management, citation helpers (for apacite),
and draft editing aids.

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
```

See `psychtools.pdf` for the full documentation.

## Package options

| Option | Default | Effect |
|--------|---------|--------|
| `includedetails` | on | Show draft footnotes and draft section headers |
| `excludedetails` | — | Hide all draft content |
| `appendixtoc` | off | Include a table of contents for the supplementary materials |
| `nocolorize` | — | Suppress red coloring of draft content |
| `nocitecommands` | — | Disable the apacite citation helpers |

## Quick reference

### Statistical notation
`\T` `\F` `\Z` `\p` `\M` `\SD` `\SE` `\D` `\CI` `\et` `\etp` `\U` `\W`

> **Compatibility note**: these short command names may conflict with math or
> font packages. Load `psychtools` before any math-heavy packages.

### Supplementary materials appendix
```latex
\renewcommand{\appendixname}{Supplementary Online Materials}
\myappendix        % resets numbering, prints header
\appsection{...}   % sections inside the appendix
```

### Draft aids
```latex
\draftsection{...}         % red section header, removed when excludedetails
\footnotewithdetails{...}  % footnote removed when excludedetails
```

### Citation helpers (apacite)
```latex
\citeeg{key}   % (e.g., Author Year)
\cites{key}    % Author's Year
```

## Backward compatibility

`ansgar.sty` is provided as a one-line shim (`\RequirePackage{psychtools}`)
so that existing documents using `\usepackage{ansgar}` continue to work
without modification.

## License

LPPL 1.3c — see `LICENSE`.

## Author

Ansgar Endress <ansgar.endress@gmx.net>
