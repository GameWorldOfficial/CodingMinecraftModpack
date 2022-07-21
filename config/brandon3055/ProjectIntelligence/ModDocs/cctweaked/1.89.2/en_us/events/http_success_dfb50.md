http_success
The http_success event is fired when an HTTP request returns successfully.

This event is normally handled inside http.get and http.post, but it can still be seen when using http.request.

Return Values
string: The event name.
string: The URL of the site requested.
http.Response: The handle for the response text.
Example
Prints the content of a website (this may fail if the request fails):

Run ᐅlocal myURL = "https://tweaked.cc/"
http.request(myURL)
local event, url, handle
repeat
    event, url, handle = os.pullEvent("http_success")
until url == myURL
print("Contents of " .. url .. ":")
print(handle.readAll())
handle.close()
See also
http.request To make an HTTP request.
Last updated on 2022-07-16