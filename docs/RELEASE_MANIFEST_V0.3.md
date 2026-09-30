# OMEGA 96 V0.3 Release Manifest

Repository identity: Lattice Decision Fabric
Engineering identity: OMEGA 96
Release state: SHADOW_ACCELERATED_INGRESS

## Source packages

The release was assembled from these two source packages:

1. A10_Ultra_Ω_OMEGA96_V0.3_SHADOW_ACCELERATED_INGRESS(1).zip
2. A10_Ultra_Ω_OMEGA96_跨项目对接_SKILL_V0.3(2).zip

The repository name is intentionally neutral. The original names are retained here only as historical engineering identifiers for traceability.

## Included release areas

- Core Python and native fast-path implementation
- Logical topology and tile-role contracts
- Aggregate Frame and Decision Token ABIs
- Native Host ingress contracts
- Differential, adversarial, determinism, and governance tests
- Benchmark scripts and recorded benchmark evidence
- Shadow execution example
- Cross-project handoff verifier and manifest
- Rollback payload and archived V0.2 evidence

## V0.3 evidence summary

- Raw-object release recheck: 3,326,359 decisions/s median over 11 runs
- Raw-object comparison: 5.58x contextual A9 V2.2 baseline
- Frame-hot release recheck: 43,174,124 decisions/s median over 5 runs
- Test environment: 5 CPUs

The frame-hot value is not an end-to-end raw-object speedup claim. The A9 comparison is contextual because the ingress contracts are not byte-identical.

## Authority and safety

- Production cutover: DENY
- Canonical write authority: 0
- Target write authority: 0
- Transport mutation authority: 0
- Storage mutation authority: 0
- Game mutation authority: 0
- Agent mutation authority: 0

This repository describes a shadow research implementation. It must not be represented as a commercial hardware chip or as proof of production readiness.
