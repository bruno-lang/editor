A block based editor
===================

## Blocks
The editor is block based like a terminal based editor.
Each block is described by one unicode character and additional information all encoded as a single `long`.

- 32 bit unicode code point
- 2 bit multi-code (0-3 encodes the number of additional code points that are also stored in the unicode (those of course need to be 1 or 2 byte code encodable points)
- 2 bit multi-align (0-3 align multiple smaller characters top, right, bottom or left)
- 6 bit foreground colour
- 6 bit background colour
- 6 bit border colour
- 4 bit border flags (top, right, bottom, left)
- 1 bit content flag (block represents editable content)
- 1 bit action flag (block is an input element)

A display has a fixed amount of vertical and horizontal blocks.
One `long[]` stores the logical display. When e.g. scrolling the values in this array are changed. Another process takes care of visualising the blocks.

When a block uses multiple code points those are shown halve of the usual font size. The align controls when 2 characters appear.

## Features
- use a indexed colourset of e.g. 64 colours so that a 6 bit reference can encode a colour
- no modal or detached windows, instead display can be divided into views/areas (that are visible at the same time next to each other)
- views can have tab like sub-selection
- status bar at the bottom
- focus on keyboard navigation (that is context aware, switch views is done relative to the focused, useful keys are shown in a view)
