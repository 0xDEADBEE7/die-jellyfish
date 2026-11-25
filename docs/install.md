# Installing it in a config

A DIE config, such as [die-config](https://github.com/0xDEADBEE7/die-config), is a binary crate
on top of die-dev that lists the extensions it installs. Installing this one is a dependency line
in its `Cargo.toml`:

```toml
die-jellyfish = { git = "https://github.com/0xDEADBEE7/die-jellyfish", branch = "main" }
```

and its entry in the list of extensions:

```rust
Box::new(die_jellyfish::Jellyfish::default()),
// or with options of your own:
Box::new(die_jellyfish::Jellyfish::new(die_jellyfish::Options {
    shoal: true,
    ..die_jellyfish::Options::default()
})),
```

The options are listed in [usage.md](usage.md#options).

## Opening on it at launch

Registering it shows nothing. To open on it at a launch, the config's greeting runs the
`jellyfish` command when:

- no file was named,
- at most one window exists, and
- the launch is a fresh one (or nothing has the focus).

It then sets the buffer named `die_jellyfish::NAME` to the directory DIE started in.
die-config's greeting does this.

## Removing it

Delete the dependency, the entry and the greeting.
