A block based editor
===================

## Blocks
The editor is block based like a terminal based editor.
Each block is described by one unicode character and additional information all encoded as a single `long`.

- 32 bit unicode code point
- 2 bit font size
- 7 bit decoration 1 index
- 7 bit decoration 2 index
- 6 bit foreground colour index
- 6 bit background colour index
- 1 bit bold
- 1 bit italic
- 1 bit strikethrough
- 1 bit underlined

A display has a fixed amount of vertical and horizontal blocks.
One `long[]` stores the logical display. When e.g. scrolling the values in this array are changed. Another process takes care of visualising the blocks.

When a block uses multiple code points those are shown halve of the usual font size. The align controls when 2 characters appear.

## Decorations
Decorations are all kind of shapes in addition to the block character itself like
- borders
- cursor
- error markers (wave underline)
- etc...

A block refers to one out of 127 preset decorations by index. 0 index means no decoration.

## Features
- use a indexed colourset of e.g. 64 colours so that a 6 bit reference can encode a colour
- no modal or detached windows, instead display can be divided into views/areas (that are visible at the same time next to each other)
- views can have tab like sub-selection
- status bar at the bottom
- focus on keyboard navigation (that is context aware, switch views is done relative to the focused, useful keys are shown in a view)
