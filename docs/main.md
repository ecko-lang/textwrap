# textwrap

## `wrap(text, width)`

wrap(text, width) -> [lines], greedily filling each line up to `width`.
Words longer than `width` are kept whole (not broken) on their own line.

## `fill(text, width)`

fill(text, width) -> the wrapped text as one string.

## `indent(text, prefix)`

indent(text, prefix) -> every non-blank line prefixed.

## `dedent(text)`

dedent(text) -> the common leading whitespace removed from every line.

## `shorten(text, width)`

shorten(text, width) -> whitespace collapsed and truncated to fit `width`,
with an "..." ellipsis, broken at a word boundary.
