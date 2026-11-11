# Changelog

## 0.38.0

### Fixed

- Widths are measured in terminal columns: CJK characters and emoji count as
  two, combining marks as none. `wrap`, `fill` and `shorten` used to count
  characters, so wide text overflowed its width.
- `dedent` removes only a prefix every line shares character for character.
  `dedent("\ta\n    b")` used to strip unequal amounts and give `"a\n   b"`; it
  now leaves both lines alone. Lines holding only whitespace become empty.
- A `width` below 1 (below 4 for `shorten`), or one that is not an Int, throws
  a `bug` error naming the function, instead of returning one word per line,
  `""` or `".."`.
- `shorten` keeps the start of a first word too wide to fit:
  `shorten("supercalifragilistic word", 10)` is `"superca..."`, not `"..."`.
- `indent` no longer prefixes lines that hold only whitespace, as documented.
- A non-string `text` or `prefix` throws a `bug` error naming the function.
