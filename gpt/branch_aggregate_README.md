# Algorithm 2 with independently chosen selectors

Compile **`gpt/main_branch_aggregate.tex`** in Overleaf.

Algorithm 2 now directly stores each program's own selector, computes
the RN intersection and selected outcome under each player's selector,
and implements the coordinatewise minimum of the resulting payoffs.
There is no separate meta-program.

The RN function takes the selector being evaluated as its third input.
PMP-extension uses that input to compute the branch's reference outcome
from the two original RN functions. Following `main.tex`'s "PMP redo",
it adds the player's PMP only against a recognized counterpart extension;
otherwise it returns the original RN output. Algorithm 2 is unchanged.
The program-space definition, overview, assumption,
notation table, and Appendix B use the same formulation; the statement
that a common selector is given to the players has been removed.

The copy otherwise stays close to `main.tex`. The main-text definition,
response assumption, Theorem 3, and proof sketch directly concern the
full two-selector programs and their implemented minimum payoffs.
There is no separate shared-selector theorem to extend: Appendix B
only checks feasibility, and Appendix C supplies the full proof of
the main theorem. The algorithm explanation is now inline in the main
copy; the former `branch_aggregate_core.tex` include is unused.
The response assumption covers both the focal original
RN function and non-extended counterparts; conditionality alone does not
prove it. The original tightness and many-player discussion is not a
new result about the two-branch protocol.

Local compilation from the project root:

```sh
latexmk -pdf -interaction=nonstopmode -halt-on-error \
  -outdir=/private/tmp/spi-branch-aggregate-direct-results \
  gpt/main_branch_aggregate.tex
```
