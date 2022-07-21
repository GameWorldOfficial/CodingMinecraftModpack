http
Make HTTP requests, sending and receiving data to a remote web server.

See also
Allowing access to local IPs To allow accessing servers running on your local network.
Changes
New in version 1.1
request(...)	Asynchronously make a HTTP request to the given url.
get(...)	Make a HTTP GET request to the given url.
post(...)	Make a HTTP POST request to the given url.
checkURLAsync(url)	Asynchronously determine whether a URL can be requested.
checkURL(url)	Determine whether a URL can be requested.
websocket(url [, headers])	Open a websocket.
websocketAsync(url [, headers])	Asynchronously open a websocket.
request(...)
Source
Asynchronously make a HTTP request to the given url.

This returns immediately, a http_success or http_failure will be queued once the request has completed.

Parameters
url string The url to request
body? string An optional string containing the body of the request. If specified, a POST request will be made instead.
headers? { [string] = string } Additional headers to send as part of this request.
binary? boolean Whether to make a binary HTTP request. If true, the body will not be UTF-8 encoded, and the received response will not be decoded.
Or
request { url = string, body? = string, headers? = { [string] = string }, binary? = boolean, method? = string, redirect? = boolean }
Options for the request.

This table form is an expanded version of the previous syntax. All arguments from above are passed in as fields instead (for instance, http.request("https://example.com") becomes http.request { url = "https://example.com" }).

This table also accepts several additional options:

method: Which HTTP method to use, for instance "PATCH" or "DELETE".
redirect: Whether to follow HTTP redirects. Defaults to true.
See also
http.get For a synchronous way to make GET requests.
http.post For a synchronous way to make POST requests.
Changes
Changed in version 1.63: Added argument for headers.
Changed in version 1.80pr1: Added argument for binary handles.
Changed in version 1.80pr1.6: Added support for table argument.
Changed in version 1.86.0: Added PATCH and TRACE methods.
get(...)
Source
Make a HTTP GET request to the given url.

Parameters
url string The url to request
headers? { [string] = string } Additional headers to send as part of this request.
binary? boolean Whether to make a binary HTTP request. If true, the body will not be UTF-8 encoded, and the received response will not be decoded.
Or
request { url = string, headers? = { [string] = string }, binary? = boolean, method? = string, redirect? = boolean } Options for the request. See http.request for details on how these options behave.
Returns
Response The resulting http response, which can be read from.
Or
nil When the http request failed, such as in the event of a 404 error or connection timeout.
string A message detailing why the request failed.
Response | nil The failing http response, if available.
Usage
Make a request to example.tweaked.cc, and print the returned page.

Run ᐅlocal request = http.get("https://example.tweaked.cc")
print(request.readAll())
-- => HTTP is working!
request.close()
Changes
Changed in version 1.63: Added argument for headers.
Changed in version 1.80pr1: Response handles are now returned on error if available.
Changed in version 1.80pr1: Added argument for binary handles.
Changed in version 1.80pr1.6: Added support for table argument.
Changed in version 1.86.0: Added PATCH and TRACE methods.
post(...)
Source
Make a HTTP POST request to the given url.

Parameters
url string The url to request
body string The body of the POST request.
headers? { [string] = string } Additional headers to send as part of this request.
binary? boolean Whether to make a binary HTTP request. If true, the body will not be UTF-8 encoded, and the received response will not be decoded.
Or
request { url = string, body? = string, headers? = { [string] = string }, binary? = boolean, method? = string, redirect? = boolean } Options for the request. See http.request for details on how these options behave.
Returns
Response The resulting http response, which can be read from.
Or
nil When the http request failed, such as in the event of a 404 error or connection timeout.
string A message detailing why the request failed.
Response | nil The failing http response, if available.
Changes
New in version 1.31
Changed in version 1.63: Added argument for headers.
Changed in version 1.80pr1: Response handles are now returned on error if available.
Changed in version 1.80pr1: Added argument for binary handles.
Changed in version 1.80pr1.6: Added support for table argument.
Changed in version 1.86.0: Added PATCH and TRACE methods.
checkURLAsync(url)
Source
Asynchronously determine whether a URL can be requested.

If this returns true, one should also listen for http_check which will container further information about whether the URL is allowed or not.

Parameters
url string The URL to check.
Returns
true When this url is not invalid. This does not imply that it is allowed - see the comment above.
Or
false When this url is invalid.
string A reason why this URL is not valid (for instance, if it is malformed, or blocked).
See also
http.checkURL For a synchronous version.
checkURL(url)
Source
Determine whether a URL can be requested.

If this returns true, one should also listen for http_check which will container further information about whether the URL is allowed or not.

Parameters
url string The URL to check.
Returns
true When this url is valid and can be requested via http.request.
Or
false When this url is invalid.
string A reason why this URL is not valid (for instance, if it is malformed, or blocked).
Usage
Run ᐅprint(http.checkURL("https://example.tweaked.cc/"))
-- => true
print(http.checkURL("http://localhost/"))
-- => false Domain not permitted
print(http.checkURL("not a url"))
-- => false URL malformed
See also
http.checkURLAsync For an asynchronous version.
websocket(url [, headers])
Source
Open a websocket.

Parameters
url string The websocket url to connect to. This should have the ws:// or wss:// protocol.
headers? { [string] = string } Additional headers to send as part of the initial websocket connection.
Returns
Websocket The websocket connection.
Or
false If the websocket connection failed.
string An error message describing why the connection failed.
Changes
New in version 1.80pr1.1
Changed in version 1.80pr1.3: No longer asynchronous.
Changed in version 1.95.3: Added User-Agent to default headers.
websocketAsync(url [, headers])
Source
Asynchronously open a websocket.

This returns immediately, a websocket_success or websocket_failure will be queued once the request has completed.

Parameters
url string The websocket url to connect to. This should have the ws:// or wss:// protocol.
headers? { [string] = string } Additional headers to send as part of the initial websocket connection.
Changes
New in version 1.80pr1.3
Changed in version 1.95.3: Added User-Agent to default headers.
Types
 Websocket
A websocket, which can be used to send an receive messages with a web server.

See also
http.websocket On how to open a websocket.
Websocket.receive([timeout])
Source
Wait for a message from the server.

Parameters
timeout? number The number of seconds to wait if no message is received.
Returns
string The received message.
boolean If this was a binary message.
Or
nil If the websocket was closed while waiting, or if we timed out.
Throws
If the websocket has been closed.

Changes
Changed in version 1.80pr1.13: Added return value indicating whether the message was binary.
Changed in version 1.87.0: Added timeout argument.
Websocket.send(message [, binary])
Source
Send a websocket message to the connected server.

Parameters
message any The message to send.
binary? boolean Whether this message should be treated as a
Throws
If the message is too large.

If the websocket has been closed.

Changes
Changed in version 1.81.0: Added argument for binary mode.
Websocket.close()
Source
Close this websocket. This will terminate the connection, meaning messages can no longer be sent or received along it.

 Response
A http response. This provides the same methods as a file (or binary file if the request used binary mode), though provides several request specific methods.

See also
http.request On how to make a http request.
Response.getResponseCode()
Source
Returns the response code and response message returned by the server.

Returns
number The response code (i.e. 200)
string The response message (i.e. "OK")
Changes
Changed in version 1.80pr1.13: Added response message return value.
Response.getResponseHeaders()
Source
Get a table containing the response's headers, in a format similar to that required by http.request. If multiple headers are sent with the same name, they will be combined with a comma.

Returns
{ [string] = string } The response's headers.
Usage
Make a request to example.tweaked.cc, and print the returned headers.

Run ᐅlocal request = http.get("https://example.tweaked.cc")
print(textutils.serialize(request.getResponseHeaders()))
-- => {
--  [ "Content-Type" ] = "text/plain; charset=utf8",
--  [ "content-length" ] = 17,
--  ...
-- }
request.close()
Last updated on 2022-07-16