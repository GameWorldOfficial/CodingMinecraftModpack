websocket_closed
The websocket_closed event is fired when an open WebSocket connection is closed.

Return Values
string: The event name.
string: The URL of the WebSocket that was closed.
Example
Prints a message when a WebSocket is closed (this may take a minute):

Run ᐅlocal myURL = "wss://example.tweaked.cc/echo"
local ws = http.websocket(myURL)
local event, url
repeat
    event, url = os.pullEvent("websocket_closed")
until url == myURL
print("The WebSocket at " .. url .. " was closed.")
Last updated on 2022-07-16