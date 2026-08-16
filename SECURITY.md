# Security and privacy

Do not open a public issue containing credentials, private keys, pharmacy data,
or exploitable update details. Report those privately to the
`PharmUtilities/AptUtil` repository owner.

Supported clients require both the v6 index signature and release-manifest
signature, followed by package and per-file verification. Offline root keys are
not stored in either GitHub repository. Report data is processed locally and
must never be uploaded here.

The historical unsigned `update-index.json` is retained only as migration
evidence and must not be used by current clients.
