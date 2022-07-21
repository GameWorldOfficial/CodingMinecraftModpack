turtle_inventory
The turtle_inventory event is fired when a turtle's inventory is changed.

Example
Prints a message when the inventory is changed:

Run ᐅwhile true do
  os.pullEvent("turtle_inventory")
  print("The inventory was changed.")
end
Last updated on 2022-07-16