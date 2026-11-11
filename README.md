# textwrap

Wrap, fill, indent, dedent and shorten text, measured in terminal columns - for
building prompts and formatting terminal output. Pure computation - no
capabilities.

## Install

```bash
ecko get github.com/ecko-lang/textwrap
```

```ecko
import textwrap
```

## Usage

```ecko
import textwrap

print(textwrap.wrap("a long sentence here", 12))       # [a long, sentence, here]
print(textwrap.fill("a long sentence here", 12))       # three lines: a long / sentence / here
print(textwrap.indent("a\n\nb", "> "))                 # "> a", "", "> b"
print(textwrap.dedent("    a\n      b"))               # "a", "  b"
print(textwrap.shorten("a long sentence here", 12))    # a long ...
print(textwrap.wrap("日本語 日本語", 6))                 # [日本語, 日本語] - each is 6 columns
```

## API

| function | returns |
|---|---|
| `wrap(text, width)` | a list of lines, each at most `width` columns, broken between words |
| `fill(text, width)` | the lines of `wrap` joined with newlines |
| `indent(text, prefix)` | `text` with `prefix` added to every line that is not blank |
| `dedent(text)` | `text` with the leading whitespace its non-blank lines share removed |
| `shorten(text, width)` | `text` with whitespace collapsed, cut to `width` columns and ending `...` |

## Notes

### Errors

| kind | reason | when |
|---|---|---|
| `bug` | `bad_argument` | `text` (or `indent`'s `prefix`) is not a string |
| `bug` | `bad_width` | `width` is not an Int, or is below 1 (below 4 for `shorten`) |

### Widths are terminal columns

Every width is what a terminal draws, not a character count: CJK characters,
fullwidth forms and emoji take two columns; combining marks, zero-width joiners
and variation selectors take none; an emoji ZWJ sequence such as a family, a
skin-tone emoji and a flag each count as one two-column glyph. The tables
follow Unicode's East Asian Width property, as `wcwidth` does.

### Whitespace and long words

- `wrap`, `fill` and `shorten` collapse every run of whitespace, newlines
  included, to one space, so paragraph breaks do not survive (Python's
  `textwrap` does the same). Wrap each paragraph separately to keep them.
- A word wider than `width` stays whole on a line of its own in `wrap`. In
  `shorten`, a first word that does not fit is cut and ends `...`.
- `dedent` compares the shared prefix character by character, so a tab and
  four spaces have nothing in common, and a line of only whitespace becomes
  empty. `indent` leaves lines of only whitespace unprefixed.

## Testing

```bash
ecko test
```

## License

[MIT](LICENSE)
