# Safe Pareto Improvements for Expected Utility Maximizers in Program Games

LaTeX source for the paper *Safe Pareto Improvements for Expected Utility
Maximizers in Program Games* and related extensions.

**Authors:** Anthony DiGiovanni, Jesse Clifton, Nicolas Macé

## Contents

- `main.tex` — main paper (AAMAS `sigconf` format).
- `gpt/main_branch_aggregate.tex` — revised CSR draft with independently chosen selectors and conditional PMP-extension; see `gpt/branch_aggregate_README.md` for details and compilation instructions.
- `spi_for_eums_prn_revision.tex` — rough draft of a revision of the CSR algorithm by GPT-5.5 Pro.
- `beliefcond.tex` — belief-conditional variant.
- `main.bib` — shared bibliography.
- `aamas.cls`, `defaults.sty`, `ACM-Reference-Format.bst` — AAMAS class,
  macros, and bibliography style.

The main drafts are standalone documents and can be compiled independently
(e.g. `pdflatex`/`bibtex`), sharing `main.bib` and the AAMAS style files.
Compile the `gpt/` draft from the repository root; its appendix file is
included by that draft, not compiled separately. `by.eps` supplies the
Creative Commons license image used by the paper template.

## License

Released under [CC BY 4.0](LICENSE).
