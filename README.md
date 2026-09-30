# Lattice Decision Fabric

An open research implementation of a 96-logical-tile lattice decision and attestation fabric.

The original engineering package used the internal identity OMEGA 96 and the external working name A10 Ultra Omega. This repository intentionally uses a neutral project name to avoid product-brand confusion.

## Status

- Release line: OMEGA 96 V0.3
- State: SHADOW_ACCELERATED_INGRESS
- Production cutover: denied
- Target/database/transport/storage/game/agent mutation authority: zero

This is a software architecture and research prototype, not a physical CPU, GPU, or commercial hardware product. The 96 tiles are logical governance identities, not 96 physical CPU cores.

## Architecture

The fabric contains 96 logical roles: 64 WORKER, 8 LOCAL_RAGE, 8 LOCAL_VAULT, 4 GLOBAL_RAGE, 4 ORACLE, 4 GLOBAL_VAULT, and 4 GUARDIAN tiles. V0.3 adds a native Host Forge for homogeneous raw-signal batches. The ingress path constructs a 32-byte Aggregate Frame, 2-byte Decision Tokens, and per-shard commitments in one call.

Shared provenance is committed once in the batch header; decision-affecting semantics remain committed through the Frame Tree. Non-homogeneous input falls back to the fully attested raw signal forge.

## V0.3 benchmark context

The included benchmark evidence was collected in a 5-CPU environment:

| Path | Result |
| --- | ---: |
| Raw-object release recheck | 3,326,359 decisions/s median over 11 runs |
| Raw-object / contextual A9 ratio | 5.58x |
| Frame-hot release recheck | 43,174,124 decisions/s median over 5 runs |
| Contextual A9 V2.2 baseline | 596,146 decisions/s |

The frame-hot result is not an end-to-end raw-object speedup claim. The A9 comparison is contextual because the two ingress contracts are not byte-identical.

## Package layout

- 00_CORE/ — Python reference, native fast path, and release guard
- 01_TOPOLOGY/ — logical tile topology
- 02_CONTRACT/ — ABI and release contracts
- 03_TESTS/ — differential, adversarial, determinism, and governance tests
- 04_BENCHMARK/ — benchmark scripts and recorded evidence
- 05_EXAMPLES/ — shadow execution example
- 06_REVIEW/ — known limitations and next tasks
- 07_VENDOR/ — cross-project adapter contracts
- 08_ROLLBACK/ — rollback payload
- 09_ARCHIVE/ — previous release evidence

## Safety boundary

This package is designed for shadow evaluation and attestation experiments. It does not grant authority to write canonical data, mutate targets, control transport or storage, modify games, or control agents. Do not treat benchmark numbers as proof of production readiness.

## License

Released under the MIT License. See LICENSE.
