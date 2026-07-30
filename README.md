# Textwrap - Ecko Std Lib Package

Wrap, fill, indent, dedent, and shorten text for [Ecko](https://ecko.sh),
written in Ecko - handy for building prompts and formatting terminal output.

## Install

```bash
ecko get github.com/ecko-lang/textwrap
```

## Usage

```ecko
import textwrap

textwrap.wrap("a long sentence here", 12)   # ["a long", "sentence", "here"]
textwrap.fill("a long sentence here", 12)   # "a long\nsentence\nhere"
textwrap.indent("a\nb", "> ")               # "> a\n> b"
textwrap.dedent("    a\n    b")             # "a\nb"
textwrap.shorten("a long sentence here", 12) # "a long ..."
```

## API

| Function | Description |
|---|---|
| `wrap(text, width)` | Word-wrap into a list of lines, each ≤ `width` |
| `fill(text, width)` | `wrap` joined with newlines |
| `indent(text, prefix)` | Prefix every non-blank line |
| `dedent(text)` | Remove the common leading whitespace from all lines |
| `shorten(text, width)` | Collapse whitespace and truncate with an `"..."` ellipsis at a word boundary |

## Notes

- Runs of whitespace (spaces, tabs, newlines) are collapsed to single spaces.
- A word longer than `width` is kept whole on its own line rather than broken.

## Testing

```bash
ecko test tests/
```

## License

MIT - see [LICENSE](LICENSE).
