# ADR-0001: Tile Size 4x4 (16 tiles)

## Status

Accepted (2026-06-01); measured rationale updated 2026-10-03 for issue #1.

## Context

The original plan considered 8x2 (16 tiles) and 8x4 (32 tiles). The implemented
design uses 4x4 on GF180MCU. [Empirical fit] Same-source GF180MCU synthesis and
independent DRC/precheck receipts now establish fit of the full ROM/decoder
design; see [Phase A report](../phase_a/README.md) for values and source links.
The prior 480-520 cells/tile and 2.1x density estimates were not measurements
and are removed from the decision rationale.

## Decision

Retain the implemented 4x4 (16 tiles). [Empirical fit] The measured design has
1,356 technology-mapped cells, 27,980.0192 um^2 synthesis cell area and
1,045,266.432 um^2 core area. All twelve prechecks pass and four independent
KLayout reports contain zero violation items. There is no measured 8x2-vs-4x4
routing comparison; do not infer that 4x4 is optimal or square in physical units.

## Consequences

- The full implemented design supersedes the preliminary Phase A stub trial.
- 1,356 / 16 = 84.75 mapped cells allocated per tile, not maximum tile capacity.
- Every RTL/config change invalidates this pinned evidence until remeasured.
- [Risk] Setup/slew/capacitance warnings remain; area and DRC success do not
  establish timing signoff. No new submission or silicon expectation is created.
- FL-002 remains [Open conjecture].
