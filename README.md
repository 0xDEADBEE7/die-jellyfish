# die-jellyfish

An ASCII jellyfish swimming in a [DIE](https://github.com/0xDEADBEE7/die) buffer.

```text
          .    /----------\                .
            /-/#$%%$$uu}}x{\-\
           /##a0[#QQ&&aaavv[]]\\
 .        /%BBB<{{88uoouuttvzz=1|       .
         /e%%n8888{{{ouutjjcct==|
        |eB@<<&{8[##[<<{cvvvvt.1;|.
        |o@/\///\\__//\\_/_\ux_t1|
       |/-/:!};|;%/||!>\t!;\\-/\\\
.      //|.;..:|+/#||;1//c;+|111\\\
       .||-/\_//|j]||x//|_+||\|/||  . ..
        ||\ |\/ |//|u////\||/.//||.     .
        | \\|\  ||//u/j+  || //|||    .
        |. \\\\ a//x|%/|| ||// //
        |   \|\\|/|[|//|| /|  //   .:
        ||  .\\\|||e|///|//|//      +
         \   |\||/u||/  ||/|/
         \\./|//\\t/|  /|// |
           \///||\u|\\//// /|
          ///\/||   /\\//\//
        /// // || //  \\//\\
      ///  //|/|||/ ////\  \\
     */|  */ |||*| ////||   |
```

- `:jellyfish` (or `M-x jellyfish`) opens it in a `*jellyfish*` buffer.
- It can greet you when DIE starts with no file, where `*scratch*` would be.
- It's drawn on your theme's background and fills the window.
- It rests after five minutes without a key, and costs nothing at rest.
- `q` lets it go and brings back the buffer it covered.
- An extension of its own: it depends on die-core only.

## Install

Add it to your config's `Cargo.toml`:

```toml
die-jellyfish = { git = "https://github.com/0xDEADBEE7/die-jellyfish", branch = "main" }
```

and to its list of extensions:

```rust
Box::new(die_jellyfish::Jellyfish::default()),
```

## Docs

- [Usage](docs/usage.md): when it shows, when it swims, how it looks, options
- [Keys](docs/keys.md)
- [Installing](docs/install.md): options and the launch greeting
- [Development](docs/development.md): building beside a DIE checkout, tests

## Licence

MIT or Apache-2.0, at your option: `LICENSE-MIT`, `LICENSE-APACHE`.
