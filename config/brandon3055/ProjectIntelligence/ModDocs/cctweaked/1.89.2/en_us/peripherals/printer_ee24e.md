printer
The printer peripheral allows pages and books to be printed.

Recipe
§recipe[computercraft:peripheral,1,3]{spacing:4}
write(...)	Writes text to the current page.
getCursorPos()	Returns the current position of the cursor on the page.
setCursorPos(x, y)	Sets the position of the cursor on the page.
getPageSize()	Returns the size of the current page.
newPage()	Starts printing a new page.
endPage()	Finalizes printing of the current page and outputs it to the tray.
setPageTitle([title])	Sets the title of the current page.
getInkLevel()	Returns the amount of ink left in the printer.
getPaperLevel()	Returns the amount of paper left in the printer.
write(...)
Source
Writes text to the current page.

Parameters
... string | number The values to write to the page.
Throws
If any values couldn't be converted to a string, or if no page is started.

getCursorPos()
Source
Returns the current position of the cursor on the page.

Returns
number The X position of the cursor.
number The Y position of the cursor.
Throws
If a page isn't being printed.

setCursorPos(x, y)
Source
Sets the position of the cursor on the page.

Parameters
x number The X coordinate to set the cursor at.
y number The Y coordinate to set the cursor at.
Throws
If a page isn't being printed.

getPageSize()
Source
Returns the size of the current page.

Returns
number The width of the page.
number The height of the page.
Throws
If a page isn't being printed.

newPage()
Source
Starts printing a new page.

Returns
boolean Whether a new page could be started.
endPage()
Source
Finalizes printing of the current page and outputs it to the tray.

Returns
boolean Whether the page could be successfully finished.
Throws
If a page isn't being printed.

setPageTitle([title])
Source
Sets the title of the current page.

Parameters
title? string The title to set for the page.
Throws
If a page isn't being printed.

getInkLevel()
Source
Returns the amount of ink left in the printer.

Returns
number The amount of ink available to print with.
getPaperLevel()
Source
Returns the amount of paper left in the printer.

Returns
number The amount of paper available to print with.
Last updated on 2022-07-16