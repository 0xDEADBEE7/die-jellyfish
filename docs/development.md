# Developing it beside DIE

DIE's crates come from [github.com/0xDEADBEE7/die](https://github.com/0xDEADBEE7/die) at `main`
(never a `rev`, so every repository in one build has the same die-core).

## Building against a DIE checkout

To build against a DIE checkout instead, copy `dev-config.example.toml` to `.cargo/config.toml`,
which git ignores:

```sh
mkdir -p .cargo
cp dev-config.example.toml .cargo/config.toml   # for a DIE checkout beside this one
```

Its paths are relative, for a DIE checkout beside this one (`../die`), and cargo reads them from
this repository's root (change them if yours is elsewhere):

- the `[patch]` points die-core, die-vim and die-test-cap at the checkout's crates;
- `[env]` sets `DIE_FONT_DIR` to its `fonts/`.

Patch every repository in one build to the same checkout.

## Checks

With the Rust that `rust-toolchain.toml` pins (1.96.0):

```sh
cargo fmt --check
cargo clippy --all-targets
DIE_UNSEEN=1 cargo test
```

Tests run through die-core's harness and need no window; `DIE_UNSEEN=1` keeps any that start DIE
off the screen.

Tests of DIE's extensions find DIE's fonts through `DIE_FONT_DIR`, which a standalone
repository has to be given since it has no `fonts/` of its own. This crate's tests draw cells and
read no font, so they also pass without it.
