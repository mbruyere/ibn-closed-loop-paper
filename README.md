# Paper — HLD-as-Intent IBN Closed Loop

ACM `acmtog` template (journal, single-column, no page limit). Build locally:

```
latexmk -pdf main.tex
```

`acmart.cls` (the ACM class file) is not vendored here. Install via
TeXLive (`texlive-publishers` package) or drop the class file alongside
`main.tex`.

## Status

- [x] Skeleton + metadata
- [x] Abstract (expanded)
- [x] §1 Introduction — HLD--production gap, RFC 9315 context, 5 contributions (C1--C5)
- [x] §2 The Closed Loop — RFC mapping table, 3 architectural commitments (AC1--AC3), 12-stage pipeline with code listings, timing, 3 invariants (I1--I3)
- [x] §3 SSoT: Nine-Layer Ontology — table with writer agents, 6 cross-layer relationships, 5 model states with transition graph, profiles, "why nine" rationale
- [x] §4 The Ten Agents — summary table (lines/inputs/outputs), dispatch-table architecture, per-agent design decisions
- [x] §5 Three-Tier Memory — architecture overview, IBN Lifecycle Ontology (14 entities, 8 relationships, extraction hints), consolidation pipeline (trigger/consolidate/push/query), LLM backend config
- [x] §6 Implementation — testbed (16 containers), 6 slices table, failure modes (5 bugs + fixes), timing measurements table
- [x] §7 Discussion — vendor IBN comparison, MALT relationship, GitOps for networks, YANG/gNMI, 5 lessons learned
- [x] §8 Conclusion + future work
- [x] Bibliography (9 entries)
- [ ] Figures: pipeline diagram, ontology layers, model-state transitions
- [ ] Final proofreading pass
