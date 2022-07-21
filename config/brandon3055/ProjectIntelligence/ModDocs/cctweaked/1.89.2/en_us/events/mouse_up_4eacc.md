mouse_up
This event is fired when a mouse button is released or a held mouse leaves the computer's terminal.

Return values
string: The event name.
number: The mouse button that was released.
number: The X-coordinate of the mouse.
number: The Y-coordinate of the mouse.
Example
Prints the coordinates and button number whenever the mouse is released.

Run ᐅwhile true do
  local event, button, x, y = os.pullEvent("mouse_up")
  print(("The mouse button %s was released at %d, %d"):format(button, x, y))
end
Last updated on 2022-07-16