cc.strings
Various utilities for working with strings and text.

See also
textutils For additional string related utilities.
Changes
New in version 1.95.0
wrap(text [, width])	Wraps a block of text, so that each line fits within the given width.
ensure_width(line [, width])	Makes the input string a fixed width.
wrap(text [, width])
Source
Wraps a block of text, so that each line fits within the given width.

This may be useful if you want to wrap text before displaying it to a monitor or printer without using print.

Parameters
text string The string to wrap.
width? number The width to constrain to, defaults to the width of the terminal.
Returns
{ string... } The wrapped input string as a list of lines.
Usage
Wrap a string and write it to the terminal.

Run ᐅterm.clear()
local lines = require "cc.strings".wrap("This is a long piece of text", 10)
for i = 1, #lines do
  term.setCursorPos(1, i)
  term.write(lines[i])
end
ensure_width(line [, width])
Source
Makes the input string a fixed width. This either truncates it, or pads it with spaces.

Parameters
line string The string to normalise.
width? number The width to constrain to, defaults to the width of the terminal.
Returns
string The string with a specific width.
Usage
Run ᐅrequire "cc.strings".ensure_width("a short string", 20)
Run ᐅrequire "cc.strings".ensure_width("a rather long string which is truncated", 20)
Last updated on 2022-07-16
