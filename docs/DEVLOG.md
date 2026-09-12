# Metal Slug X development log

## 2026-09-03 — setup package mod catalog

The Wave 1 wrapper audit found that this title did not pass the built `mods`
directory to the shared packager. Bloody Roar II reproduced the same source
shape in CI run `33743305573`: all four packages had no mod catalog and the
workflow rejected them.

The wrapper now passes `--runtime-dir mods`. The package gate remains active.
It still rejects a missing catalog, machine state, and developer-only packages.

Consulted leads:

- `_runs/knowledge/FINDING_CANDIDATES.md`, `PSX-PUB-001` and `PSX-PUB-016`
- `_runs/knowledge/regressions/REGRESSION_LEDGER.md`, `PSX-PUB-016`
- GitHub searches for the exact error and wrapper option; no matching result
  was indexed

This correction does not authorize a release.

## 2026-09-04 v0.1.2 POSIX setup-copy candidate

This candidate pins PSXRecomp 40ce47896026be52bcaae7de03b69766e0bd03e4 and recomp-ui be8ac1d03ee19d55394b5a5f2d9d1506edd56659.
Linux and macOS packages use native CMake, Ninja, Python, C, and C++ tools.
Windows keeps the portable toolchain route. This change does not change game
code or the graduation state. Build-only CI and every exact-package release
gate must pass before publication.

## 2026-09-13 - Reconcile published source into main

The default branch now includes the published v0.1.2 source. The release workflow uses the existing PSX-PUB-031 indentation repair. Later catalog identities and the current recomp-ui repository URL are preserved. The pinned runtime and UI commits match v0.1.2. No new package, release, gameplay test, or source-pin promotion is claimed.

Corpus consulted: PSX-PUB-031 and FAIL-142. The existing audit_release_workflow.py parser and regression supply the repair. Primary reference: https://github.com/softprops/action-gh-release documents overwrite_files under with. Source checks cover YAML structure, Actionlint, title executable-name tests when present, manifest versions, and exact release gitlinks.
