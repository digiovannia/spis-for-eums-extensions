# CSR with independently chosen selection functions

The draft in [main_branch_aggregate.tex](main_branch_aggregate.tex) studies
how players can individually benefit from adopting programs that guarantee
safe Pareto improvements, without coordinating on a particular improvement
or a common selection function.

## Motivation

Conditional set-valued renegotiation (CSR) lets each player specify a set
of acceptable improvements on a default outcome. These sets can depend
on the other player's renegotiation function. Their intersection is the
agreement set.

Choosing an outcome from this intersection creates another coordination
problem: players may prefer different selection functions. The draft
allows each player to choose their own, while retaining a common procedure
for combining the results.

## The procedure

Each program stores a default program, a renegotiation function, and a
transitive selection function. Algorithm 2 computes the common default
outcome, then evaluates renegotiation under each player's selector:

1. Evaluate both renegotiation functions using that selector as an input.
2. Apply the selector to their intersection, or use the default outcome
   if the intersection is empty.
3. After both computations, implement a common outcome giving each player
   their lower payoff from the two selected outcomes.

For example, selected payoffs of (3, 2) and (2, 3) produce final payoffs
of (2, 2). The minimum is taken over payoffs, not actions. In a two-player
game with a convex feasible payoff set, this payoff is feasible because
both selected outcomes weakly improve on the same default. The programs
agree on its realization, potentially using correlated randomization.

## Conditional PMP-extension

The Pareto meet minimum (PMM) gives each player their lowest payoff on
the game's Pareto frontier. A player's Pareto meet projection (PMP) of
an outcome consists of feasible improvements that give both players at
least their PMM payoffs, while increasing the other player's payoff only
as far as necessary to reach that bound.

PMP-extension modifies the renegotiation function, leaving the program's
default and chosen selector unchanged. For each selector being evaluated:

- If the counterpart's function is also PMP-extended, recover both
  original functions and compute their default renegotiation outcome
  under that selector. Each extended function returns its original
  offers against the counterpart's original function, together with
  its player's PMP of this outcome.
- Otherwise, return the original function's output against the actual
  counterpart, without adding PMP offers.

Reciprocity matters because adding offers unconditionally can change the
selected outcome to a player's disadvantage. When both functions extend,
the new offers instead weakly improve on a common reference outcome.
Transitivity requires a selector not to worsen the selected payoff when
only such improvements are added.

## What the result establishes (NOT yet verified by Anthony)

Under the stated non-punishment and feasibility assumptions, a
subjectively optimal program remains optimal after PMP-extension.
The comparison holds against each counterpart in the player's belief
support, under each selector, so taking the payoff minimum preserves it.
When both players use extended programs, their actual final payoffs
are at least the PMM.

The non-punishment assumption is substantive: relevant non-extended
functions must respond identically to a counterpart's extension and its
original function. This includes the focal player's original function;
conditional extension alone does not establish the incentive result.
Players still share the interaction protocol, but need not share a
selector or beliefs about one another.

The theorem concerns the full two-player programs. Appendix B verifies
feasibility of the payoff minimum, and Appendix C gives the full proof.
The separate iterated-renegotiation tightness analysis concerns a
shared-selector protocol.

## Compilation

From the repository root:

```sh
latexmk -pdf -interaction=nonstopmode -halt-on-error \
  -outdir=build gpt/main_branch_aggregate.tex
```
