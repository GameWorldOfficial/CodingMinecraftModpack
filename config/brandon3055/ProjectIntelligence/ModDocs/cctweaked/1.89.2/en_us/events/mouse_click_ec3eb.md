mouse_click
This event is fired when the terminal is clicked with a mouse. This event is only fired on advanced computers (including advanced turtles and pocket computers).

Return values
string: The event name.
number: The mouse button that was clicked.
number: The X-coordinate of the click.
number: The Y-coordinate of the click.
Mouse buttons
Several mouse events (mouse_click, mouse_up, mouse_scroll) contain a "mouse button" code. This takes a numerical value depending on which button on your mouse was last pressed when this event occurred.

Button Code	Mouse Button
1	Left button
2	Right button
3	Middle button
Example
Print the button and the coordinates whenever the mouse is clicked.

Run ᐅwhile true do
  local event, button, x, y = os.pullEvent("mouse_click")
  print(("The mouse button %s was pressed at %d, %d"):format(button, x, y))
end
Last updated on 2022-07-16