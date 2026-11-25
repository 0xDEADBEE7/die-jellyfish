# Using die-jellyfish

`M-x jellyfish`, or `:jellyfish`, shows it in a buffer, `*jellyfish*`. It's an ASCII jellyfish
and its effects, drawn on your theme's background and worked out from the clock alone: the bell
and its lip, the arms, the tentacles, the coats and the flash between them, the swirl it forms
from, the halos, the sparks, and the glint where it's about to be. Two rows stay clear, one above
and one below, with the animal centred between them.

For its keys, see [keys.md](keys.md).

## When it shows

With a config whose greeting runs it (see [install.md](install.md)), DIE started with no file
opens on it, where the empty `*scratch*` was: from the Dock, Finder or `open`, or a bare `die`
that finds no DIE running. Over a session that brought back one window it takes that window,
with every buffer back behind it, and `q` uncovers the one that was there.

It stays away from:

- a session's splits;
- a start with a file named (`die foo.rs` opens on the file, and no jellyfish is made);
- `:rebuild` and `:restart`, which bring back what was on screen;
- `die --check`.

A restart that brings nothing back gets it where `*scratch*` would have been. A file that
arrives after the launch takes its window, with the jellyfish still there behind it: a Finder
double-click or `open -a DIE file` that starts DIE, and `die --wait` with no DIE running, which
starts one and then sends its file, so those show a frame of jellyfish first.

`:jellyfish` shows it in this window at any time: the one already swimming, or a new one from
its first spark. Without the greeting, `:jellyfish` is the only way it shows.

## When it swims

While a window shows it and you've touched DIE in the last five minutes.

- With no window on it, it stops, and shown again it goes on from where it stopped. The opening
  plays once for a buffer, and again only after `q` and `:jellyfish`.
- After five minutes without a key (`rest_after`) it rests, a still picture. The next key's
  command wakes it where it stopped; so do a click anywhere in DIE, a key or the pointer on it,
  and DIE's window taking the keyboard while the jellyfish's split has the focus. With the focus
  in another split, coming back to DIE leaves it still until your first key's command.
- Typing into a terminal in another split doesn't wake one at rest, as those keys run no
  command.
- It swims whether or not DIE has the keyboard, since DIE's window opens without it.
- A pause never jumps it ahead: each frame adds the time since the last one, a quarter second at
  most, and a new one's first frame a thirtieth at most, so the opening starts at its start
  however long DIE's window took to open.

## On screen

Every cell's background is the theme's, and the colours fade into it, so a halo or a spark's
tail ends at the paper rather than as a dark speck on it.

- On a dark background nothing else about the inks changes.
- On a light one, white would be the paper, so the brightest ink is the theme's foreground and
  the pigments are deepened (to 0.62 of themselves, toward black). That's measured for contrast
  but not yet seen on screen.
- A theme set while it swims re-tones it at the next frame.

It's the window's whole width (`full_width`), so the water's glitter and the sparks don't stop
at an invisible wall, and `\z` narrows it to a file's width and widens it again. The animal grows
with the window between about 49 columns by 30 rows and 132 by 77 (for cells twice as tall as
wide). In a smaller window it's cut at the edges rather than drawn smaller, as in a small
terminal. The status line shows the directory, as on any buffer, and no cursor is drawn.

## Not kept

It isn't in the session: a restart doesn't bring it back. A window that showed it shows the
buffer you used last, which is the one it covered unless you've shown or made another since,
with your cursor where it was, though that window's jump list is gone, as after a restart with a
terminal in it. Nothing of it is written anywhere.

## Options

`die_jellyfish::Options`:

| Option | Default | What it does |
|---|---|---|
| `water` | `true` | The dust and the four-point twinkles in the water around it. |
| `shoal` | `false` | The far-off little jellyfish. |
| `full_width` | `true` | Fill the window's whole width (a board's is false). |
| `rest_after` | five minutes | Rest after this long without a key; `None` never rests. |

## What it costs

Nothing until it's shown. While it swims, one timer at 30 a second (a covered or minimized DIE's
too) until the five minutes are up. At rest or with no window on it, nothing: no timer runs.

## What isn't there yet

- It hasn't been checked by eye on screen: its tests check cells, inks and timers. To see it,
  run `:jellyfish` after a `:rebuild`, or launch DIE with no file named (unless the session
  brings back splits).
- A light theme's inks are measured, not seen.
- It doesn't come back after a restart, and it has no key of its own.
- A start that gets its file after the launch (Finder, `open -a`, `die --wait` with no DIE
  running) shows a frame of it before the file.
- In a window under about 49 columns or 30 rows the animal is cut rather than drawn smaller.
