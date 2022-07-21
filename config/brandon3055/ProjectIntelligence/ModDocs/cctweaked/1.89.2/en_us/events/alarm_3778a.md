alarm
The timer event is fired when an alarm started with os.setAlarm completes.

Return Values
string: The event name.
number: The ID of the alarm that finished.
Example
Starts a timer and then prints its ID:

Run ᐅlocal alarmID = os.setAlarm(os.time() + 0.05)
local event, id
repeat
    event, id = os.pullEvent("alarm")
until id == alarmID
print("Alarm with ID " .. id .. " was fired")
See also
os.setAlarm To start an alarm.
Last updated on 2022-07-16