textutils
Helpful utilities for formatting and manipulating strings.

Changes
New in version 1.2
slowWrite(text [, rate])	Slowly writes string text at current cursor position, character-by-character.
slowPrint(sText [, nRate])	Slowly prints string text at current cursor position, character-by-character.
formatTime(nTime [, bTwentyFourHour])	Takes input time and formats it in a more readable format such as 6:30 PM.
pagedPrint(text [, free_lines])	Prints a given string to the display.
tabulate(...)	Prints tables in a structured form.
pagedTabulate(...)	Prints tables in a structured form, stopping and prompting for input should the result not fit on the terminal.
empty_json_array	A table representing an empty JSON array, in order to distinguish it from an empty JSON object.
json_null	A table representing the JSON null value.
serialize(t, opts)	Convert a Lua object into a textual representation, suitable for saving in a file or pretty-printing.
serialise(t, opts)	Convert a Lua object into a textual representation, suitable for saving in a file or pretty-printing.
unserialize(s)	Converts a serialised string back into a reassembled Lua object.
unserialise(s)	Converts a serialised string back into a reassembled Lua object.
serializeJSON(t [, bNBTStyle])	Returns a JSON representation of the given data.
serialiseJSON(t [, bNBTStyle])	Returns a JSON representation of the given data.
unserializeJSON(s [, options])	Converts a serialised JSON string back into a reassembled Lua object.
unserialiseJSON(s [, options])	Converts a serialised JSON string back into a reassembled Lua object.
urlEncode(str)	Replaces certain characters in a string to make it safe for use in URLs or POST data.
complete(sSearchText [, tSearchTable])	Provides a list of possible completions for a partial Lua expression.
slowWrite(text [, rate])
Source
Slowly writes string text at current cursor position, character-by-character.

Like _G.write, this does not insert a newline at the end.

Parameters
text string The the text to write to the screen
rate? number The number of characters to write each second, Defaults to 20.
Usage
Run ᐅtextutils.slowWrite("Hello, world!")
Run ᐅtextutils.slowWrite("Hello, world!", 5)
Changes
New in version 1.3
slowPrint(sText [, nRate])
Source
Slowly prints string text at current cursor position, character-by-character.

Like print, this inserts a newline after printing.

Parameters
sText string The the text to write to the screen
nRate? number The number of characters to write each second, Defaults to 20.
Usage
Run ᐅtextutils.slowPrint("Hello, world!")
Run ᐅtextutils.slowPrint("Hello, world!", 5)
formatTime(nTime [, bTwentyFourHour])
Source
Takes input time and formats it in a more readable format such as 6:30 PM.

Parameters
nTime number The time to format, as provided by os.time.
bTwentyFourHour? boolean Whether to format this as a 24-hour clock (18:30) rather than a 12-hour one (6:30 AM)
Returns
string The formatted time
Usage
Print the current in-game time as a 12-hour clock.

Run ᐅtextutils.formatTime(os.time())
Print the local time as a 24-hour clock.

Run ᐅtextutils.formatTime(os.time("local"), true)
pagedPrint(text [, free_lines])
Source
Prints a given string to the display.

If the action can be completed without scrolling, it acts much the same as print; otherwise, it will throw up a "Press any key to continue" prompt at the bottom of the display. Each press will cause it to scroll down and write a single line more before prompting again, if need be.

Parameters
text string The text to print to the screen.
free_lines? number The number of lines which will be automatically scrolled before the first prompt appears (meaning free_lines + 1 lines will be printed). This can be set to the cursor's y position - 2 to always try to fill the screen. Defaults to 0, meaning only one line is displayed before prompting.
Returns
number The number of lines printed.
Usage
Generates several lines of text and then prints it, paging once the bottom of the terminal is reached.

Run ᐅlocal lines = {}
for i = 1, 30 do lines[i] = ("This is line #%d"):format(i) end
local message = table.concat(lines, "\n")

local width, height = term.getCursorPos()
textutils.pagedPrint(message, height - 2)
tabulate(...)
Source
Prints tables in a structured form.

This accepts multiple arguments, either a table or a number. When encountering a table, this will be treated as a table row, with each column width being auto-adjusted.

When encountering a number, this sets the text color of the subsequent rows to it.

Parameters
... { string... } | number The rows and text colors to display.
Usage
Run ᐅtextutils.tabulate(
  colors.orange, { "1", "2", "3" },
  colors.lightBlue, { "A", "B", "C" }
)
Changes
New in version 1.3
pagedTabulate(...)
Source
Prints tables in a structured form, stopping and prompting for input should the result not fit on the terminal.

This functions identically to textutils.tabulate, but will prompt for user input should the whole output not fit on the display.

Parameters
... { string... } | number The rows and text colors to display.
Usage
Generates a long table, tabulates it, and prints it to the screen.

Run ᐅlocal rows = {}
for i = 1, 30 do rows[i] = {("Row #%d"):format(i), math.random(1, 400)} end

textutils.tabulate(colors.orange, {"Column", "Value"}, colors.lightBlue, table.unpack(rows))
See also
textutils.tabulate
textutils.pagedPrint
Changes
New in version 1.3
empty_json_array
Source
A table representing an empty JSON array, in order to distinguish it from an empty JSON object.

The contents of this table should not be modified.

Usage
Run ᐅtextutils.serialiseJSON(textutils.empty_json_array)
See also
textutils.serialiseJSON
textutils.unserialiseJSON
json_null
Source
A table representing the JSON null value.

The contents of this table should not be modified.

Usage
Run ᐅtextutils.serialiseJSON(textutils.json_null)
See also
textutils.serialiseJSON
textutils.unserialiseJSON
serialize(t, opts)
Source
Convert a Lua object into a textual representation, suitable for saving in a file or pretty-printing.

Parameters
t The object to serialise
opts { compact? = boolean, allow_repetitions? = boolean }
Options for serialisation.

compact: Do not emit indentation and other whitespace between terms.
allow_repetitions: Relax the check for recursive tables, allowing them to appear multiple times (as long as tables do not appear inside themselves).
Returns
string The serialised representation
Throws
If the object contains a value which cannot be serialised. This includes functions and tables which appear multiple times.

Usage
Serialise a basic table.

Run ᐅtextutils.serialise({ 1, 2, 3, a = 1, ["another key"] = { true } })
Demonstrates some of the other options

Run ᐅlocal tbl = { 1, 2, 3 }
print(textutils.serialize({ tbl, tbl }, { allow_repetitions = true }))

print(textutils.serialize(tbl, { compact = true }))
See also
cc.pretty.pretty_print An alternative way to display a table, often more suitable for pretty printing.
Changes
New in version 1.3
Changed in version 1.97.0: Added opts argument.
serialise(t, opts)
Source
Convert a Lua object into a textual representation, suitable for saving in a file or pretty-printing.

Parameters
t The object to serialise
opts { compact? = boolean, allow_repetitions? = boolean }
Options for serialisation.

compact: Do not emit indentation and other whitespace between terms.
allow_repetitions: Relax the check for recursive tables, allowing them to appear multiple times (as long as tables do not appear inside themselves).
Returns
string The serialised representation
Throws
If the object contains a value which cannot be serialised. This includes functions and tables which appear multiple times.

Usage
Serialise a basic table.

Run ᐅtextutils.serialise({ 1, 2, 3, a = 1, ["another key"] = { true } })
Demonstrates some of the other options

Run ᐅlocal tbl = { 1, 2, 3 }
print(textutils.serialize({ tbl, tbl }, { allow_repetitions = true }))

print(textutils.serialize(tbl, { compact = true }))
See also
cc.pretty.pretty_print An alternative way to display a table, often more suitable for pretty printing.
Changes
New in version 1.3
Changed in version 1.97.0: Added opts argument.
unserialize(s)
Source
Converts a serialised string back into a reassembled Lua object.

This is mainly used together with textutils.serialize.

Parameters
s string The serialised string to deserialise.
Returns
The deserialised object
Or
nil If the object could not be deserialised.
Changes
New in version 1.3
unserialise(s)
Source
Converts a serialised string back into a reassembled Lua object.

This is mainly used together with textutils.serialize.

Parameters
s string The serialised string to deserialise.
Returns
The deserialised object
Or
nil If the object could not be deserialised.
Changes
New in version 1.3
serializeJSON(t [, bNBTStyle])
Source
Returns a JSON representation of the given data.

This function attempts to guess whether a table is a JSON array or object. However, empty tables are assumed to be empty objects - use textutils.empty_json_array to mark an empty array.

This is largely intended for interacting with various functions from the commands API, though may also be used in making http requests.

Parameters
t The value to serialise. Like textutils.serialise, this should not contain recursive tables or functions.
bNBTStyle? boolean Whether to produce NBT-style JSON (non-quoted keys) instead of standard JSON.
Returns
string The JSON representation of the input.
Throws
If the object contains a value which cannot be serialised. This includes functions and tables which appear multiple times.

Usage
Run ᐅtextutils.serializeJSON({ values = { 1, "2", true } })
See also
textutils.json_null Use to serialize a JSON null value.
textutils.empty_json_array Use to serialize a JSON empty array.
Changes
New in version 1.7
serialiseJSON(t [, bNBTStyle])
Source
Returns a JSON representation of the given data.

This function attempts to guess whether a table is a JSON array or object. However, empty tables are assumed to be empty objects - use textutils.empty_json_array to mark an empty array.

This is largely intended for interacting with various functions from the commands API, though may also be used in making http requests.

Parameters
t The value to serialise. Like textutils.serialise, this should not contain recursive tables or functions.
bNBTStyle? boolean Whether to produce NBT-style JSON (non-quoted keys) instead of standard JSON.
Returns
string The JSON representation of the input.
Throws
If the object contains a value which cannot be serialised. This includes functions and tables which appear multiple times.

Usage
Run ᐅtextutils.serializeJSON({ values = { 1, "2", true } })
See also
textutils.json_null Use to serialize a JSON null value.
textutils.empty_json_array Use to serialize a JSON empty array.
Changes
New in version 1.7
unserializeJSON(s [, options])
Source
Converts a serialised JSON string back into a reassembled Lua object.

This may be used with textutils.serializeJSON, or when communicating with command blocks or web APIs.

If a null value is encountered, it is converted into nil. It can be converted into textutils.json_null with the parse_null option.

If an empty array is encountered, it is converted into textutils.empty_json_array. It can be converted into a new empty table with the parse_empty_array option.

Parameters
s string The serialised string to deserialise.
options? { nbt_style? = boolean, parse_null? = boolean, parse_empty_array? = boolean }
Options which control how this JSON object is parsed.

nbt_style: When true, this will accept stringified NBT strings, as produced by many commands.
parse_null: When true, null will be parsed as json_null, rather than nil.
parse_empty_array: When false, empty arrays will be parsed as a new table. By default (or when this value is true), they are parsed as empty_json_array.
Returns
The deserialised object
Or
nil If the object could not be deserialised.
string A message describing why the JSON string is invalid.
Usage
Unserialise a basic JSON object

Run ᐅtextutils.unserialiseJSON('{"name": "Steve", "age": null}')
Unserialise a basic JSON object, returning null values as json_null.

Run ᐅtextutils.unserialiseJSON('{"name": "Steve", "age": null}', { parse_null = true })
See also
textutils.json_null Use to serialize a JSON null value.
textutils.empty_json_array Use to serialize a JSON empty array.
Changes
New in version 1.87.0
unserialiseJSON(s [, options])
Source
Converts a serialised JSON string back into a reassembled Lua object.

This may be used with textutils.serializeJSON, or when communicating with command blocks or web APIs.

If a null value is encountered, it is converted into nil. It can be converted into textutils.json_null with the parse_null option.

If an empty array is encountered, it is converted into textutils.empty_json_array. It can be converted into a new empty table with the parse_empty_array option.

Parameters
s string The serialised string to deserialise.
options? { nbt_style? = boolean, parse_null? = boolean, parse_empty_array? = boolean }
Options which control how this JSON object is parsed.

nbt_style: When true, this will accept stringified NBT strings, as produced by many commands.
parse_null: When true, null will be parsed as json_null, rather than nil.
parse_empty_array: When false, empty arrays will be parsed as a new table. By default (or when this value is true), they are parsed as empty_json_array.
Returns
The deserialised object
Or
nil If the object could not be deserialised.
string A message describing why the JSON string is invalid.
Usage
Unserialise a basic JSON object

Run ᐅtextutils.unserialiseJSON('{"name": "Steve", "age": null}')
Unserialise a basic JSON object, returning null values as json_null.

Run ᐅtextutils.unserialiseJSON('{"name": "Steve", "age": null}', { parse_null = true })
See also
textutils.json_null Use to serialize a JSON null value.
textutils.empty_json_array Use to serialize a JSON empty array.
Changes
New in version 1.87.0
urlEncode(str)
Source
Replaces certain characters in a string to make it safe for use in URLs or POST data.

Parameters
str string The string to encode
Returns
string The encoded string.
Usage
Run ᐅprint("https://example.com/?view=" .. textutils.urlEncode("some text&things"))
Changes
New in version 1.31
complete(sSearchText [, tSearchTable])
Source
Provides a list of possible completions for a partial Lua expression.

If the completed element is a table, suggestions will have . appended to them. Similarly, functions have ( appended to them.

Parameters
sSearchText string The partial expression to complete, such as a variable name or table index.
tSearchTable? table The table to find variables in, defaulting to the global environment (_G). The function also searches the "parent" environment via the __index metatable field.
Returns
{ string... } The (possibly empty) list of completions.
Usage
Run ᐅtextutils.complete( "pa", _ENV )
See also
shell.setCompletionFunction
_G.read
Changes
New in version 1.74
Last updated on 2022-07-16