timer
The timer event is fired when a timer started with os.startTimer completes.

Return Values
string: The event name.
number: The ID of the timer that finished.
Example
Starts a timer and then prints its ID:

Run ᐅlocal timerID = os.startTimer(2)
local event, id
repeat
    event, id = os.pullEvent("timer")
until id == timerID
print("Timer with ID " .. id .. " was fired")
See also
os.startTimer To start a timer.
Last updated on 2022-07-16