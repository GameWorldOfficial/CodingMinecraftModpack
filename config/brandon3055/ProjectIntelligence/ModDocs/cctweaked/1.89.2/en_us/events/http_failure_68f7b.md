http_failure
The http_failure event is fired when an HTTP request fails.

This event is normally handled inside http.get and http.post, but it can still be seen when using http.request.

Return Values
string: The event name.
string: The URL of the site requested.
string: An error describing the failure.
nil: A response handle if the connection succeeded, but the server's response indicated failure.
Example
Prints an error why the website cannot be contacted:

Run ᐅlocal myURL = "https://does.not.exist.tweaked.cc"
http.request(myURL)
local event, url, err
repeat
    event, url, err = os.pullEvent("http_failure")
until url == myURL
print("The URL " .. url .. " could not be reached: " .. err)
Prints the contents of a webpage that does not exist:

Run ᐅlocal myURL = "https://tweaked.cc/this/does/not/exist"
http.request(myURL)
local event, url, err, handle
repeat
    event, url, err, handle = os.pullEvent("http_failure")
until url == myURL
print("The URL " .. url .. " could not be reached: " .. err)
print(handle.getResponseCode())
handle.close()
See also
http.request To send an HTTP request.
Last updated on 2022-07-16