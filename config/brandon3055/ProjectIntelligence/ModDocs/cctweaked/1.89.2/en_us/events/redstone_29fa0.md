redstone
The redstone event is fired whenever any redstone inputs on the computer change.

Example
Prints a message when a redstone input changes:

Run ᐅwhile true do
  os.pullEvent("redstone")
  print("A redstone input has changed!")
end
Last updated on 2022-07-16