# Distribution policy

Normal changes to this repository are made only by the reviewed AptUtil release
workflows. Manual edits are reserved for documented recovery operations.

## Candidate and promotion rules

1. A candidate is built and signed once from a reviewed private-monorepo commit.
2. Candidate tags are unique and immutable.
3. Promotion downloads and verifies the exact candidate again.
4. The operator supplies the exact tested package SHA-256.
5. Test and stable reuse the same package, manifest, and signature.
6. The channel index changes only after the release is publicly downloadable.
7. Rollback routes a channel to a known-good published release; artifacts needed
   for audit and support are retained.

The legacy index remains untouched until the migration plan explicitly retires
the clients that depend on it.

Signing-key rotation is delivered as an explicitly signed `trust` component. It
is promoted like any other immutable candidate, but automatic rollback cannot
cross the rotation boundary; recovery must be signed by the current key.
