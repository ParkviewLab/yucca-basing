<!--
SPDX-FileCopyrightText: 2026 Gary Frattarola <garyf@parkviewlab.ai>
SPDX-License-Identifier: CC-BY-4.0
-->

# In-flight ideas

*Candidates under consideration. Each is a question, not a commitment: to
research, weigh against the northstar, and either promote to a plan or drop.
Nothing here is acted on silently.*

## Release packaging for a Rust desktop app

How per-OS installers get built and attached to the GitHub Release. The
candidates are `cargo-dist` (which generates the dmg, msi, and AppImage
targets and can drive the release itself) and a bespoke `release-rust.yml` in
the handbook's shape (gate, a three-OS build matrix, the changelog job) with
`cargo-packager` for the bundles and `apple-codesign` for macOS signing and
notarization from any CI runner. Whichever is chosen must slot into the tag →
CI → GitHub Release flow the handbook establishes for desktop apps. Also open:
whether Windows signing is wanted for the first releases.

## The dev-tools version helpers do not read `Cargo.toml`

`_sot.sh` in [dev-tools](https://github.com/ParkviewLab/dev-tools) detects only
`pyproject.toml`, `package.json`, and `VERSION.txt`, so `git bump` and
`git release` cannot drive this repo yet. A Cargo kind is needed: detect
`Cargo.toml`, read and write the workspace's package version. That is a
dev-tools change and its own PR; the handbook's rule against hand-typing a
version argues against a one-off manual exception for the first release.

## A Rust profile in the handbook

This is the family's first Rust repo. The conventions it settles (the rustfmt
and clippy gates, the `rust-toolchain.toml` pin, the `test-rust.yml` shape,
the version guard's Cargo branch, the workspace layout) are recorded only here
for now. Once proven, propose a `rust-tooling.md` in the handbook, analogous
to `node-tooling.md`, so the next Rust repo starts from the same shape.
