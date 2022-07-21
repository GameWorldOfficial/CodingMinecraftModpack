parallel
A simple way to run several functions at once.

Functions are not actually executed simultaniously, but rather this API will automatically switch between them whenever they yield (e.g. whenever they call coroutine.yield, or functions that call that - such as os.pullEvent - or functions that call that, etc - basically, anything that causes the function to "pause").

Each function executed in "parallel" gets its own copy of the event queue, and so "event consuming" functions (again, mostly anything that causes the script to pause - eg os.sleep, rednet.receive, most of the turtle API, etc) can safely be used in one without affecting the event queue accessed by the other.

⚠ CAUTION
When using this API, be careful to pass the functions you want to run in parallel, and not the result of calling those functions.

For instance, the following is correct:

Run ᐅlocal function do_sleep() sleep(1) end
parallel.waitForAny(do_sleep, rednet.receive)
but the following is NOT:

Run ᐅlocal function do_sleep() sleep(1) end
parallel.waitForAny(do_sleep(), rednet.receive)
Changes
New in version 1.2
waitForAny(...)	Switches between execution of the functions, until any of them finishes.
waitForAll(...)	Switches between execution of the functions, until all of them are finished.
waitForAny(...)
Source
Switches between execution of the functions, until any of them finishes. If any of the functions errors, the message is propagated upwards from the parallel.waitForAny call.

Parameters
... function The functions this task will run
Usage
Print a message every second until the q key is pressed.

Run ᐅlocal function tick()
    while true do
        os.sleep(1)
        print("Tick")
    end
end
local function wait_for_q()
    repeat
        local _, key = os.pullEvent("key")
    until key == keys.q
    print("Q was pressed!")
end

parallel.waitForAny(tick, wait_for_q)
print("Everything done!")
waitForAll(...)
Source
Switches between execution of the functions, until all of them are finished. If any of the functions errors, the message is propagated upwards from the parallel.waitForAll call.

Parameters
... function The functions this task will run
Usage
Start off two timers and wait for them both to run.

Run ᐅlocal function a()
    os.sleep(1)
    print("A is done")
end
local function b()
    os.sleep(3)
    print("B is done")
end

parallel.waitForAll(a, b)
print("Everything done!")
Last updated on 2022-07-16