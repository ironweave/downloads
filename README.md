<div align="center">

# IronWeave · downloads

**Public distribution mirror for IronWeave's pre-compiled SDK artifacts.**

[Download from code.ironweave.io](https://code.ironweave.io/#downloads) ·
[All releases](https://github.com/ironweave/downloads/releases) ·
[Getting started](https://github.com/ironweave/getting-started)

</div>

---

This repository holds the **compiled binaries** for the IronWeave SDK libraries — nothing else.
There is no source code here. Each build is published as a
[GitHub Release](https://github.com/ironweave/downloads/releases), which gives every artifact a
permanent, anonymous, CDN-backed download URL. The developer portal at
[**code.ironweave.io**](https://code.ironweave.io) links to these releases through stable
`/dl/...` paths.

Builds are produced by CI in the (private) source repositories and mirrored here automatically on
every tagged release. **Don't create or edit releases here by hand** — they'll be overwritten.

## What's published

| Library | What it is | Package |
|---------|-----------|---------|
| **iwcrypto** | Confidential-value primitives — Pedersen commitments, Bulletproof range proofs, Schnorr equality proofs, Ed25519 signing, ECDH encryption. | [`IronWeave.Crypto`](https://www.nuget.org/packages/IronWeave.Crypto) (NuGet) |
| **iwblobs** | Chunked AES-256-GCM streaming for large payloads, multi-party key sharing, on-chain integrity anchoring. Builds on iwcrypto. | [`IronWeave.Blobs`](https://www.nuget.org/packages/IronWeave.Blobs) (NuGet) |

Each release for a library ships native libraries (`.so` / `.dylib` / `.dll` / `.a`) for:

| Platform | Architectures | Asset |
|----------|---------------|-------|
| Linux | x86_64, aarch64 | `<lib>-linux-x86_64.zip`, `<lib>-linux-aarch64.zip` |
| macOS | arm64, x86_64 | `<lib>-macos-aarch64.zip`, `<lib>-macos-x86_64.zip` |
| Windows | x64, arm64 | `<lib>-windows-x86_64.zip`, `<lib>-windows-aarch64.zip` |
| iOS | device + simulator | `<lib>-ios.zip` (xcframework) |
| Android | arm64-v8a, armeabi-v7a, x86_64 | `<lib>-android.zip` |
| NuGet runtimes | all of the above | `<lib>-nuget-runtimes.zip` |

Every release also includes a **`SHA256SUMS`** file covering all of its assets.

> `.NET` users generally don't need these zips — install the NuGet package instead; it bundles the
> native runtimes for every platform.

## Release & asset naming

- **Tag:** `<lib>-v<version>` — e.g. `iwcrypto-v0.3.0`, `iwblobs-v0.3.0`.
  Each library is versioned and released independently.
- **Assets:** `<lib>-<platform>-<arch>.zip` as listed above, plus `SHA256SUMS`.

## Downloading

**Recommended — branded, stable links via the portal:**

```bash
# a specific version (permanent, content-addressed)
curl -fsSL https://code.ironweave.io/dl/download/iwcrypto-v0.3.0/iwcrypto-linux-x86_64.zip -o iwcrypto.zip

# the newest release, whatever it is
curl -fsSL https://code.ironweave.io/dl/latest/iwcrypto-linux-x86_64.zip -o iwcrypto.zip
```

Those `/dl/...` paths redirect here, so you can also fetch straight from GitHub:

```bash
curl -fsSL https://github.com/ironweave/downloads/releases/download/iwcrypto-v0.3.0/iwcrypto-linux-x86_64.zip -o iwcrypto.zip
```

## Verifying a download

Always check the artifact against the release's `SHA256SUMS`:

```bash
# from the same release you downloaded the zip from
curl -fsSL https://code.ironweave.io/dl/download/iwcrypto-v0.3.0/SHA256SUMS -o SHA256SUMS
sha256sum -c SHA256SUMS 2>/dev/null | grep iwcrypto-linux-x86_64.zip
# iwcrypto-linux-x86_64.zip: OK
```

On macOS, use `shasum -a 256 -c SHA256SUMS`.

## License

The libraries distributed here are licensed under the [Apache License 2.0](LICENSE).
