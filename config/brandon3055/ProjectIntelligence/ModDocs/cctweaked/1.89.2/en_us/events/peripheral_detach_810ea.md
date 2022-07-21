peripheral_detach
The peripheral_detach event is fired when a peripheral is detached from a side or from a modem.

Return Values
string: The event name.
string: The side the peripheral was detached from.
Example
Prints a message when a peripheral is detached:

Run ᐅwhile true do
  local event, side = os.pullEvent("peripheral_detach")
  print("A peripheral was detached on side " .. side)
end
See also
peripheral For the event fired when a peripheral is attached.
Last updated on 2022-07-16