A block based editor
===================

- use a indexed colourset of e.g. 64 colours so that a 6 bit reference can encode a colour

## Blocks
The editor is block based like a terminal based editor.
Each block is described by one unicode character and additional information all encoded as a single long.

- 32 bit unicode code point
- 6 bit foreground colour
- 6 bit background colour
- 6 bit border colour
- 4 bit border flags (top, right, bottom, left)
- 1 bit content flag (block represents editable content)
- 1 bit cursor flag (block is the cursor/focus position)
- 1 bit action flag (block is an input element)
