## Evidence Chain Properties

Run analyzed: `37645199282` (commit `5e9e101c4e349d08664dff5d677aad5e6dcbf6faa45a8b27ff486e30e821007b`), vault `s3://cgep-lab-grc-evidence-vault-35f9ee54/runs/37645199282/`

| Property | Artifact that proves it | How to verify |
|---|---|---|
| **Integrity**: the evidence hasn't changed since it was produced | `evidence-37645199282-f8b7a03c2b45b4d390a1bc85abbcc56b0e8968aa.tar.gz.sha256`, plus the `5e9e101c4e349d08664dff5d677aad5e6dcbf6faa45a8b27ff486e30e821007b` field in `receipt.json` | Re-hash the bundle and compare. In the tamper test, flipping one byte changed the hash and verification failed. |
| **Authenticity**: the evidence came from this pipeline, not a person | `runs/37645199282/evidence-37645199282-f8b7a03c2b45b4d390a1bc85abbcc56b0e8968aa.tar.gz` (Cosign keyless signature, logged in the Rekor transparency log) | `cosign verify-blob` checks that the signer was the `grc-gate` workflow in this repo through GitHub OIDC. No long-lived signing key exists. |
| **Immutability**: stored evidence can't be silently replaced | S3 bucket versioning (and Object Lock, if enabled), plus the `LIvNZgJwUnARMq80R8RHO3CV__Lw2FK6` in `receipt.json` | Overwriting the bundle created a new version. The original version the receipt points to was still there. |
| **Traceability**: evidence links to the exact run and code change | `receipt.json` (`3764519928`, `f8b7a03c2b45b4d390a1bc85abbcc56b0e8968aa`, `runs/37645199282/evidence-37645199282-f8b7a03c2b45b4d390a1bc85abbcc56b0e8968aa.tar.gz`, `LIvNZgJwUnARMq80R8RHO3CV__Lw2FK6`) | The run ID matches the Actions run, the commit matches the PR, and the key and version ID identify exactly one object in the vault. |

### Tamper test result
- Original bundle: `verify-evidence.sh` reported verified OK, chain intact.
- After uploading a one-byte-modified bundle to the same key: `FAIL: SHA mismatch` 