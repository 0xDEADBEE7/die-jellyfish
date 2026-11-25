# die-jellyfish

An ASCII jellyfish swimming in a [DIE](https://github.com/0xDEADBEE7/die) buffer, on the theme's
background: the animal and its effects from the owner's jellyfish program, worked out from the
clock alone. It's a DIE extension in a repository of its own, outside DIE, which your config
installs. It depends on die-core only, so it's platform-neutral.

## Using it

`M-x jellyfish`, or `:jellyfish`, shows it in a buffer, `*jellyfish*`. It's the program's animal
and its effects, drawn on your theme's background: the bell and its lip, the arms, the
tentacles, the coats and the flash between them, the swirl it forms from, the halos, the sparks,
and the glint where it's about to be. The source listing, the readouts and the command line are
gone. The five rows the readouts kept clear are two, one above and one below, with the animal
centred between them.

**When it shows.** With [die-config](https://github.com/0xDEADBEE7/die-config)'s greeting
(die-dev's before the split), DIE started with no file opens on it, where the empty `*scratch*`
was: from the Dock, Finder or `open`, or a bare `die` that finds no DIE running. Over a session
that brought back one window it takes that window, with every buffer back behind it, and `q`
uncovers the one that was there. It stays away from a session's splits, from a start with a file
named (`die foo.rs` opens on the file, and no jellyfish is made), from `:rebuild` and `:restart`,
which bring back what was on screen, and from `die --check`. A restart that brings nothing back
gets it where `*scratch*` would have been. A file that arrives after the launch takes its window,
with the jellyfish still there behind it: a Finder double-click or `open -a DIE file` that starts
DIE, and `die --wait` with no DIE running, which starts one and then sends its file, so those show
a frame of jellyfish first. `:jellyfish` shows it in this window at any time: the one already
swimming, or a new one from its first spark. Without the greeting, `:jellyfish` is the only way it
shows.

**Keys**, in normal state, the only state it has. The first three rows are in the jellyfish's
own keymap, so `\hk` describes them:

| Key | What it does |
|---|---|
| `q` | Let it go (`jellyfish-close`): the buffer is killed, and the window the launch or `:jellyfish` put it in shows the buffer it covered there, whatever was made behind it meanwhile. If that window has left it and come back by another way (`C-^`, `\]`), or `q` is pressed in another window on it, each window that showed it shows the buffer you used last, as when any buffer is killed, or an empty `*scratch*`. |
| `:`, `C-w …` | die-vim's command line and window keys, bound here as on a die-whiteboard board, since a jellyfish has no text for die-vim's keys to come through. |
| `ZZ` `ZQ` `C-^` `C-o` | Evil's reflexes, bound here for the same reason: close its window (both, as `:q`, since there's nothing to write, so in the last window they quit DIE), and flip to the buffer used before, the jellyfish staying behind it (both: `C-o` is `C-^` here, since die-vim's jump list starts from a text cursor, which a jellyfish hasn't, and that buffer is where the first `C-o` from here would go). With nothing behind it they say `No other buffer`. |
| `Esc`, `Ctrl-[` | Nothing, as in normal state anywhere; after `C-w` or `Z` it drops the key begun, and says nothing. |
| Any other key | `i is undefined`, as on any buffer that isn't text. Typing doesn't lift it. |

Your leader's keys and DIE's own work as anywhere, so `\f`, `\p`, `\]`, `\e` or `:e file` put
what you asked for in its window, with the jellyfish a buffer behind it (`\]`, `C-^`). It takes
no leader key.

**When it swims.** While a window shows it and you've touched DIE in the last five minutes. With
no window on it, it stops, and shown again it goes on from where it stopped: the opening plays
once for a buffer, and again only after `q` and `:jellyfish`. After five minutes without a key
(`rest_after`) it rests, a still picture, and the next key's command wakes it where it stopped;
so do a click anywhere in DIE, a key or the pointer on it, and DIE's window taking the keyboard
while the jellyfish's split has the focus (with the focus in another split, coming back to DIE
leaves it still until your first key's command). Typing into a terminal in another split doesn't
wake one at rest, as those keys run no command. It swims whether or not DIE has the keyboard,
since DIE's window opens without it. A pause never jumps it ahead: each frame adds the time since
the last one, a quarter second at most, as the program's `clock += dt.min(0.25)` did, and a new
one's first frame a thirtieth at most, so the opening starts at its start however long DIE's
window took to open.

**On screen.** Every cell's background is the theme's, and the colours fade into it where the
program's faded to black, so a halo or a spark's tail ends at the paper rather than as a dark
speck on it. On a dark background nothing else about the inks changes. On a light one, white
would be the paper, so the brightest ink is the theme's foreground and the pigments are deepened
(to 0.62 of themselves, toward black): that's measured for contrast and not yet seen, since
mono-dark is the only theme. A theme set while it swims re-tones it at the next frame. It's the
window's whole width (`full_width`), so the water's glitter and the sparks don't stop at an
invisible wall, and `\z` narrows it to a file's width and widens it again. The animal grows with
the window between about 49 columns by 30 rows and 132 by 77 (for cells twice as tall as wide),
and in a smaller window it's cut at the edges rather than drawn smaller, as in a small terminal.
The status line shows the directory, as on any buffer, and no cursor is drawn.

**Not kept.** It isn't in the session: a restart doesn't bring it back, and a window that showed
it shows the buffer you used last, which is the one it covered unless you've shown or made
another since, your cursor where it was, though that window's jump list is gone, as after a
restart with a terminal in it. Nothing of it is written anywhere.

**Options** (`die_jellyfish::Options`): `water` (true: the dust and the four-point twinkles in
the water around it), `shoal` (false: the far-off little jellyfish), `full_width` (true, where a
board's is false), `rest_after` (five minutes; `None` never rests). **What it costs:** nothing
until it's shown. While it swims, one timer at 30 a second, a covered or minimized DIE's too,
until the five minutes are up. At rest or with no window on it, nothing: no timer runs.

**What isn't there yet.** Nobody has seen it on screen: it was checked as cells, inks and
timers, and the first look is the owner's: `:jellyfish` after a `:rebuild`, which as a restart
comes back on what was on screen, or the next launch with no file named, unless the session
brings back splits. A light theme's inks are measured, not seen. It doesn't come back after a
restart (M1's surface restorer), and it has no key of its own. A start that gets its file after
the launch (Finder, `open -a`, `die --wait` with no DIE running) shows a frame of it before the
file. In a window under about 49 columns or 30 rows the animal is cut rather than drawn smaller.

## Installing it in die-config

die-config is the owner's DIE: a binary crate on top of die-dev that lists the extensions it
installs. Installing this one is a dependency line in its `Cargo.toml`:

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

Registering it shows nothing. To open on it at a launch, die-config's greeting runs the
`jellyfish` command when no file was named, at most one window exists and the launch is a fresh
one (or nothing has the focus), and sets the buffer named `die_jellyfish::NAME` to the directory
DIE started in. Removing it is deleting the dependency, the entry and the greeting.

## Developing it beside DIE

DIE's crates come from [github.com/0xDEADBEE7/die](https://github.com/0xDEADBEE7/die) at `main`
(never a `rev`, so every repository in one build has the same die-core). To build against a DIE
checkout instead, copy `dev-config.example.toml` to `.cargo/config.toml`, which git ignores, and
replace each `/abs/path/to/...` placeholder with an absolute path (cargo doesn't expand `~`): the
`[patch]` points die-core, die-vim and die-test-cap at the checkout's crates, and `[env]` sets
`DIE_FONT_DIR` to its `fonts/`. Patch every repository in one build to the same checkout.

```sh
mkdir -p .cargo
cp dev-config.example.toml .cargo/config.toml   # then write out the paths
```

Then, with the Rust that `rust-toolchain.toml` pins (1.96.0):

```sh
cargo fmt --check
cargo clippy --all-targets
DIE_UNSEEN=1 cargo test
```

Tests run through die-core's harness and need no window; `DIE_UNSEEN=1` keeps any that start
DIE off the screen. Tests of DIE's extensions find DIE's fonts through `DIE_FONT_DIR`, which a
standalone repository has to be given since it has no `fonts/` of its own; this crate's tests
draw cells and read no font, so they also pass without it.

## Licence

MIT or Apache-2.0, at your option: `LICENSE-MIT`, `LICENSE-APACHE`.
