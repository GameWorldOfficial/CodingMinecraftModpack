help
Find help files on the current computer.

Changes
New in version 1.2
path()	Returns a colon-separated list of directories where help files are searched for.
setPath(newPath)	Sets the colon-seperated list of directories where help files are searched for to newPath
lookup(topic)	Returns the location of the help file for the given topic.
topics()	Returns a list of topics that can be looked up and/or displayed.
completeTopic(prefix)	Returns a list of topic endings that match the prefix.
path()
Source
Returns a colon-separated list of directories where help files are searched for. All directories are absolute.

Returns
string The current help search path, separated by colons.
See also
help.setPath
setPath(newPath)
Source
Sets the colon-seperated list of directories where help files are searched for to newPath

Parameters
newPath string The new path to use.
Usage
Run ᐅhelp.setPath( "/disk/help/" )
Run ᐅhelp.setPath( help.path() .. ":/myfolder/help/" )
See also
help.path
lookup(topic)
Source
Returns the location of the help file for the given topic.

Parameters
topic string The topic to find
Returns
string | nil The path to the given topic's help file, or nil if it cannot be found.
Usage
Run ᐅhelp.lookup("disk")
Changes
Changed in version 1.80pr1: Now supports finding .txt files.
Changed in version 1.97.0: Now supports finding Markdown files.
topics()
Source
Returns a list of topics that can be looked up and/or displayed.

Returns
table A list of topics in alphabetical order.
Usage
Run ᐅhelp.topics()
completeTopic(prefix)
Source
Returns a list of topic endings that match the prefix. Can be used with read to allow input of a help topic.

Parameters
prefix string The prefix to match
Returns
table A list of matching topics.
Changes
New in version 1.74
Last updated on 2022-07-16