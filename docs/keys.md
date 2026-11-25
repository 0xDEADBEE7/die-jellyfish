# Keys

In normal state, the only state it has. The first three rows are in the jellyfish's own keymap,
so `\hk` describes them.

| Key | What it does |
|---|---|
| `q` | Let it go (`jellyfish-close`): the buffer is killed, and the window the launch or `:jellyfish` put it in shows the buffer it covered there, whatever was made behind it meanwhile. If that window has left it and come back by another way (`C-^`, `\]`), or `q` is pressed in another window on it, each window that showed it shows the buffer you used last, as when any buffer is killed, or an empty `*scratch*`. |
| `:`, `C-w …` | die-vim's command line and window keys, bound here as on a die-whiteboard board, since a jellyfish has no text for die-vim's keys to come through. |
| `ZZ` `ZQ` `C-^` `C-o` | Evil's reflexes, bound here for the same reason. `ZZ` and `ZQ` close its window (both as `:q`, since there's nothing to write, so in the last window they quit DIE). `C-^` and `C-o` flip to the buffer used before, the jellyfish staying behind it (`C-o` is `C-^` here, since die-vim's jump list starts from a text cursor, which a jellyfish hasn't, and that buffer is where the first `C-o` from here would go). With nothing behind it they say `No other buffer`. |
| `Esc`, `Ctrl-[` | Nothing, as in normal state anywhere; after `C-w` or `Z` it drops the key begun, and says nothing. |
| Any other key | `i is undefined`, as on any buffer that isn't text. Typing doesn't lift it. |

Your leader's keys and DIE's own work as anywhere, so `\f`, `\p`, `\]`, `\e` or `:e file` put
what you asked for in its window, with the jellyfish a buffer behind it (`\]`, `C-^`). It takes
no leader key.
