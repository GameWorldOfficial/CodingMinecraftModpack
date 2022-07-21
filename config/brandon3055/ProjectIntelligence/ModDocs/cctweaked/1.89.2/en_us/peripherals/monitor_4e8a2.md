monitor
Monitors are a block which act as a terminal, displaying information on one side. This allows them to be read and interacted with in-world without opening a GUI.

Monitors act as terminal redirects and so expose the same methods, as well as several additional ones, which are documented below.

Like computers, monitors come in both normal (no colour) and advanced (colour) varieties.

Recipes
§recipe[computercraft:peripheral,1,2]{spacing:4}
§recipe[computercraft:peripheral,1,4]{spacing:4}
Usage
Write "Hello, world!" to an adjacent monitor:

Run ᐅlocal monitor = peripheral.find("monitor")
monitor.setCursorPos(1, 1)
monitor.write("Hello, world!")
setTextScale(scale)	Set the scale of this monitor.
getTextScale()	Get the monitor's current text scale.
write(text)	Write text at the current cursor position, moving the cursor to the end of the text.
scroll(y)	Move all positions up (or down) by y pixels.
getCursorPos()	Get the position of the cursor.
setCursorPos(x, y)	Set the position of the cursor.
getCursorBlink()	Checks if the cursor is currently blinking.
setCursorBlink(blink)	Sets whether the cursor should be visible (and blinking) at the current cursor position.
getSize()	Get the size of the terminal.
clear()	Clears the terminal, filling it with the current background colour.
clearLine()	Clears the line the cursor is currently on, filling it with the current background colour.
getTextColour()	Return the colour that new text will be written as.
getTextColor()	Return the colour that new text will be written as.
setTextColour(colour)	Set the colour that new text will be written as.
setTextColor(colour)	Set the colour that new text will be written as.
getBackgroundColour()	Return the current background colour.
getBackgroundColor()	Return the current background colour.
setBackgroundColour(colour)	Set the current background colour.
setBackgroundColor(colour)	Set the current background colour.
isColour()	Determine if this terminal supports colour.
isColor()	Determine if this terminal supports colour.
blit(text, textColour, backgroundColour)	Writes text to the terminal with the specific foreground and background characters.
setPaletteColour(...)	Set the palette for a specific colour.
setPaletteColor(...)	Set the palette for a specific colour.
getPaletteColour(colour)	Get the current palette for a specific colour.
getPaletteColor(colour)	Get the current palette for a specific colour.
setTextScale(scale)
Source
Set the scale of this monitor. A larger scale will result in the monitor having a lower resolution, but display text much larger.

Parameters
scale number The monitor's scale. This must be a multiple of 0.5 between 0.5 and 5.
Throws
If the scale is out of range.

See also
getTextScale
getTextScale()
Source
Get the monitor's current text scale.

Returns
number The monitor's current scale.
Throws
If the monitor cannot be found.

Changes
New in version 1.81.0
write(text)
Source
Write text at the current cursor position, moving the cursor to the end of the text.

Unlike functions like write and print, this does not wrap the text - it simply copies the text to the current terminal line.

Parameters
text The text to write.
scroll(y)
Source
Move all positions up (or down) by y pixels.

Every pixel in the terminal will be replaced by the line y pixels below it. If y is negative, it will copy pixels from above instead.

Parameters
y number The number of lines to move up by. This may be a negative number.
getCursorPos()
Source
Get the position of the cursor.

Returns
number The x position of the cursor.
number The y position of the cursor.
setCursorPos(x, y)
Source
Set the position of the cursor. terminal writes will begin from this position.

Parameters
x number The new x position of the cursor.
y number The new y position of the cursor.
getCursorBlink()
Source
Checks if the cursor is currently blinking.

Returns
boolean If the cursor is blinking.
Changes
New in version 1.80pr1.9
setCursorBlink(blink)
Source
Sets whether the cursor should be visible (and blinking) at the current cursor position.

Parameters
blink boolean Whether the cursor should blink.
getSize()
Source
Get the size of the terminal.

Returns
number The terminal's width.
number The terminal's height.
clear()
Source
Clears the terminal, filling it with the current background colour.

clearLine()
Source
Clears the line the cursor is currently on, filling it with the current background colour.

getTextColour()
Source
Return the colour that new text will be written as.

Returns
number The current text colour.
See also
colors For a list of colour constants, returned by this function.
Changes
New in version 1.74
getTextColor()
Source
Return the colour that new text will be written as.

Returns
number The current text colour.
See also
colors For a list of colour constants, returned by this function.
Changes
New in version 1.74
setTextColour(colour)
Source
Set the colour that new text will be written as.

Parameters
colour number The new text colour.
See also
colors For a list of colour constants.
Changes
New in version 1.45
Changed in version 1.80pr1: Standard computers can now use all 16 colors, being changed to grayscale on screen.
setTextColor(colour)
Source
Set the colour that new text will be written as.

Parameters
colour number The new text colour.
See also
colors For a list of colour constants.
Changes
New in version 1.45
Changed in version 1.80pr1: Standard computers can now use all 16 colors, being changed to grayscale on screen.
getBackgroundColour()
Source
Return the current background colour. This is used when writing text and clearing the terminal.

Returns
number The current background colour.
See also
colors For a list of colour constants, returned by this function.
Changes
New in version 1.74
getBackgroundColor()
Source
Return the current background colour. This is used when writing text and clearing the terminal.

Returns
number The current background colour.
See also
colors For a list of colour constants, returned by this function.
Changes
New in version 1.74
setBackgroundColour(colour)
Source
Set the current background colour. This is used when writing text and clearing the terminal.

Parameters
colour number The new background colour.
See also
colors For a list of colour constants.
Changes
New in version 1.45
Changed in version 1.80pr1: Standard computers can now use all 16 colors, being changed to grayscale on screen.
setBackgroundColor(colour)
Source
Set the current background colour. This is used when writing text and clearing the terminal.

Parameters
colour number The new background colour.
See also
colors For a list of colour constants.
Changes
New in version 1.45
Changed in version 1.80pr1: Standard computers can now use all 16 colors, being changed to grayscale on screen.
isColour()
Source
Determine if this terminal supports colour.

Terminals which do not support colour will still allow writing coloured text/backgrounds, but it will be displayed in greyscale.

Returns
boolean Whether this terminal supports colour.
Changes
New in version 1.45
isColor()
Source
Determine if this terminal supports colour.

Terminals which do not support colour will still allow writing coloured text/backgrounds, but it will be displayed in greyscale.

Returns
boolean Whether this terminal supports colour.
Changes
New in version 1.45
blit(text, textColour, backgroundColour)
Source
Writes text to the terminal with the specific foreground and background characters.

As with write, the text will be written at the current cursor location, with the cursor moving to the end of the text.

textColour and backgroundColour must both be strings the same length as text. All characters represent a single hexadecimal digit, which is converted to one of CC's colours. For instance, "a" corresponds to purple.

Parameters
text string The text to write.
textColour string The corresponding text colours.
backgroundColour string The corresponding background colours.
Throws
If the three inputs are not the same length.

Usage
Prints "Hello, world!" in rainbow text.

Run ᐅterm.blit("Hello, world!","01234456789ab","0000000000000")
See also
colors For a list of colour constants, and their hexadecimal values.
Changes
New in version 1.74
Changed in version 1.80pr1: Standard computers can now use all 16 colors, being changed to grayscale on screen.
setPaletteColour(...)
Source
Set the palette for a specific colour.

ComputerCraft's palette system allows you to change how a specific colour should be displayed. For instance, you can make colors.red more red by setting its palette to #FF0000. This does now allow you to draw more colours - you are still limited to 16 on the screen at one time - but you can change which colours are used.

Parameters
index number The colour whose palette should be changed.
colour number A 24-bit integer representing the RGB value of the colour. For instance the integer 0xFF0000 corresponds to the colour #FF0000.
Or
index number The colour whose palette should be changed.
r number The intensity of the red channel, between 0 and 1.
g number The intensity of the green channel, between 0 and 1.
b number The intensity of the blue channel, between 0 and 1.
Usage
Change the red colour from the default #CC4C4C to #FF0000.

Run ᐅterm.setPaletteColour(colors.red, 0xFF0000)
term.setTextColour(colors.red)
print("Hello, world!")
As above, but specifying each colour channel separately.

Run ᐅterm.setPaletteColour(colors.red, 1, 0, 0)
term.setTextColour(colors.red)
print("Hello, world!")
See also
colors.unpackRGB To convert from the 24-bit format to three separate channels.
colors.packRGB To convert from three separate channels to the 24-bit format.
Changes
New in version 1.80pr1
setPaletteColor(...)
Source
Set the palette for a specific colour.

ComputerCraft's palette system allows you to change how a specific colour should be displayed. For instance, you can make colors.red more red by setting its palette to #FF0000. This does now allow you to draw more colours - you are still limited to 16 on the screen at one time - but you can change which colours are used.

Parameters
index number The colour whose palette should be changed.
colour number A 24-bit integer representing the RGB value of the colour. For instance the integer 0xFF0000 corresponds to the colour #FF0000.
Or
index number The colour whose palette should be changed.
r number The intensity of the red channel, between 0 and 1.
g number The intensity of the green channel, between 0 and 1.
b number The intensity of the blue channel, between 0 and 1.
Usage
Change the red colour from the default #CC4C4C to #FF0000.

Run ᐅterm.setPaletteColour(colors.red, 0xFF0000)
term.setTextColour(colors.red)
print("Hello, world!")
As above, but specifying each colour channel separately.

Run ᐅterm.setPaletteColour(colors.red, 1, 0, 0)
term.setTextColour(colors.red)
print("Hello, world!")
See also
colors.unpackRGB To convert from the 24-bit format to three separate channels.
colors.packRGB To convert from three separate channels to the 24-bit format.
Changes
New in version 1.80pr1
getPaletteColour(colour)
Source
Get the current palette for a specific colour.

Parameters
colour number The colour whose palette should be fetched.
Returns
number The red channel, will be between 0 and 1.
number The green channel, will be between 0 and 1.
number The blue channel, will be between 0 and 1.
Changes
New in version 1.80pr1
getPaletteColor(colour)
Source
Get the current palette for a specific colour.

Parameters
colour number The colour whose palette should be fetched.
Returns
number The red channel, will be between 0 and 1.
number The green channel, will be between 0 and 1.
number The blue channel, will be between 0 and 1.
Changes
New in version 1.80pr1
Last updated on 2022-07-16