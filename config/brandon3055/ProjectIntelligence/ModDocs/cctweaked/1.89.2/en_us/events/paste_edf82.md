paste
The paste event is fired when text is pasted into the computer through Ctrl-V (or ⌘V on Mac).

Return values
string: The event name.
string The text that was pasted.
Example
Prints pasted text:

Run ᐅwhile true do
  local event, text = os.pullEvent("paste")
  print('"' .. text .. '" was pasted')
end
Last updated on 2022-07-16