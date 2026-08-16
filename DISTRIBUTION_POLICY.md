# Distribution policy

Normal changes to this repository are made only by reviewed workflows in
`PharmUtilities/AptUtil`. GitHub Actions are disabled here: this repository is a
generated distribution surface, not an independent build or development system.
Manual edits are reserved for documented recovery or repository migration.

## Candidate and promotion rules

1. A candidate is built once from a reviewed private-monorepo commit and signed
   by the release-signing environment.
2. Candidate tags are unique and immutable.
3. Promotion downloads and verifies the exact candidate again.
4. The operator supplies the exact tested package SHA-256.
5. Test and stable reuse the same package, manifest, and signature.
6. The separately signed channel index changes only after the release is publicly
   downloadable.
7. Rollback routes a channel to a known-good published release; artifacts needed
   for audit and support are retained.

The unsigned `update-index.json` is historical and is not an active AptUtil v6
channel. Current clients use only `update-index-v6.json` and its detached
signature.

Release and index signing keys are separate, repository-environment secrets.
Offline root keys never enter GitHub. Trust rotation is delivered as an explicitly
signed `trust` component and automatic rollback cannot cross that boundary.
