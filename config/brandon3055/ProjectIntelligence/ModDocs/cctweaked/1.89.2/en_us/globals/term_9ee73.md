term
Interact with a computer's terminal or monitors, writing text and drawing ASCII graphics.

nativePaletteColour(colour)	Get the default palette value for a colour.
nativePaletteColor(colour)	Get the default palette value for a colour.
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
redirect(target)	Redirects terminal output to a monitor, a window, or any other custom terminal object.
current()	Returns the current terminal object of the computer.
native()	Get the native terminal object of the current computer.
nativePaletteColour(colour)
Source
Get the default palette value for a colour.

Parameters
colour number The colour whose palette should be fetched.
Returns
number The red channel, will be between 0 and 1.
number The green channel, will be between 0 and 1.
number The blue channel, will be between 0 and 1.
Throws
When given an invalid colour.

See also
term.Redirect.setPaletteColour To change the palette colour.
Changes
New in version 1.81.0
nativePaletteColor(colour)
Source
Get the default palette value for a colour.

Parameters
colour number The colour whose palette should be fetched.
Returns
number The red channel, will be between 0 and 1.
number The green channel, will be between 0 and 1.
number The blue channel, will be between 0 and 1.
Throws
When given an invalid colour.

See also
term.Redirect.setPaletteColour To change the palette colour.
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
redirect(target)
Source
Redirects terminal output to a monitor, a window, or any other custom terminal object. Once the redirect is performed, any calls to a "term" function - or to a function that makes use of a term function, as print - will instead operate with the new terminal object.

A "terminal object" is simply a table that contains functions with the same names - and general features - as those found in the term table. For example, a wrapped monitor is suitable.

The redirect can be undone by pointing back to the previous terminal object (which this function returns whenever you switch).

Parameters
target Redirect The terminal redirect the term API will draw to.
Returns
Redirect The previous redirect object, as returned by term.current.
Usage
Redirect to a monitor on the right of the computer. term.redirect(peripheral.wrap("right"))

Changes
New in version 1.31
current()
Source
Returns the current terminal object of the computer.

Returns
Redirect The current terminal redirect
Usage
Create a new window which draws to the current redirect target.

Run ᐅwindow.create(term.current(), 1, 1, 10, 10)
Changes
New in version 1.6
native()
Source
Get the native terminal object of the current computer.

It is recommended you do not use this function unless you absolutely have to. In a multitasked environment, term.native will not be the current terminal object, and so drawing may interfere with other programs.

Returns
Redirect The native terminal redirect.
Changes
New in version 1.6
Types
 Redirect
A base class for all objects which interact with a terminal. Namely the term and monitors.

Redirect.write(text)
Source
Write text at the current cursor position, moving the cursor to the end of the text.

Unlike functions like write and print, this does not wrap the text - it simply copies the text to the current terminal line.

Parameters
text The text to write.
Redirect.scroll(y)
Source
Move all positions up (or down) by y pixels.

Every pixel in the terminal will be replaced by the line y pixels below it. If y is negative, it will copy pixels from above instead.

Parameters
y number The number of lines to move up by. This may be a negative number.
Redirect.getCursorPos()
Source
Get the position of the cursor.

Returns
number The x position of the cursor.
number The y position of the cursor.
Redirect.setCursorPos(x, y)
Source
Set the position of the cursor. terminal writes will begin from this position.

Parameters
x number The new x position of the cursor.
y number The new y position of the cursor.
Redirect.getCursorBlink()
Source
Checks if the cursor is currently blinking.

Returns
boolean If the cursor is blinking.
Changes
New in version 1.80pr1.9
Redirect.setCursorBlink(blink)
Source
Sets whether the cursor should be visible (and blinking) at the current cursor position.

Parameters
blink boolean Whether the cursor should blink.
Redirect.getSize()
Source
Get the size of the terminal.

Returns
number The terminal's width.
number The terminal's height.
Redirect.clear()
Source
Clears the terminal, filling it with the current background colour.

Redirect.clearLine()
Source
Clears the line the cursor is currently on, filling it with the current background colour.

Redirect.getTextColour()
Source
Return the colour that new text will be written as.

Returns
number The current text colour.
See also
colors For a list of colour constants, returned by this function.
Changes
New in version 1.74
Redirect.getTextColor()
Source
Return the colour that new text will be written as.

Returns
number The current text colour.
See also
colors For a list of colour constants, returned by this function.
Changes
New in version 1.74
Redirect.setTextColour(colour)
Source
Set the colour that new text will be written as.

Parameters
colour number The new text colour.
See also
colors For a list of colour constants.
Changes
New in version 1.45
Changed in version 1.80pr1: Standard computers can now use all 16 colors, being changed to grayscale on screen.
Redirect.setTextColor(colour)
Source
Set the colour that new text will be written as.

Parameters
colour number The new text colour.
See also
colors For a list of colour constants.
Changes
New in version 1.45
Changed in version 1.80pr1: Standard computers can now use all 16 colors, being changed to grayscale on screen.
Redirect.getBackgroundColour()
Source
Return the current background colour. This is used when writing text and clearing the terminal.

Returns
number The current background colour.
See also
colors For a list of colour constants, returned by this function.
Changes
New in version 1.74
Redirect.getBackgroundColor()
Source
Return the current background colour. This is used when writing text and clearing the terminal.

Returns
number The current background colour.
See also
colors For a list of colour constants, returned by this function.
Changes
New in version 1.74
Redirect.setBackgroundColour(colour)
Source
Set the current background colour. This is used when writing text and clearing the terminal.

Parameters
colour number The new background colour.
See also
colors For a list of colour constants.
Changes
New in version 1.45
Changed in version 1.80pr1: Standard computers can now use all 16 colors, being changed to grayscale on screen.
Redirect.setBackgroundColor(colour)
Source
Set the current background colour. This is used when writing text and clearing the terminal.

Parameters
colour number The new background colour.
See also
colors For a list of colour constants.
Changes
New in version 1.45
Changed in version 1.80pr1: Standard computers can now use all 16 colors, being changed to grayscale on screen.
Redirect.isColour()
Source
Determine if this terminal supports colour.

Terminals which do not support colour will still allow writing coloured text/backgrounds, but it will be displayed in greyscale.

Returns
boolean Whether this terminal supports colour.
Changes
New in version 1.45
Redirect.isColor()
Source
Determine if this terminal supports colour.

Terminals which do not support colour will still allow writing coloured text/backgrounds, but it will be displayed in greyscale.

Returns
boolean Whether this terminal supports colour.
Changes
New in version 1.45
Redirect.blit(text, textColour, backgroundColour)
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
Redirect.setPaletteColour(...)
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
Redirect.setPaletteColor(...)
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
Redirect.getPaletteColour(colour)
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
Redirect.getPaletteColor(colour)
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