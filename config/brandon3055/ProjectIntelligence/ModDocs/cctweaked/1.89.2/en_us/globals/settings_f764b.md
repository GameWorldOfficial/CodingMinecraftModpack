settings
Read and write configuration options for CraftOS and your programs.

By default, the settings API will load its configuration from the /.settings file. One can then use settings.save to update the file.

Changes
New in version 1.78
define(name [, options])	Define a new setting, optional specifying various properties about it.
undefine(name)	Remove a definition of a setting.
set(name, value)	Set the value of a setting.
get(name [, default])	Get the value of a setting.
getDetails(name)	Get details about a specific setting.
unset(name)	Remove the value of a setting, setting it to the default.
clear()	Resets the value of all settings.
getNames()	Get the names of all currently defined settings.
load([sPath])	Load settings from the given file.
save([sPath])	Save settings to the given file.
define(name [, options])
Source
Define a new setting, optional specifying various properties about it.

While settings do not have to be added before being used, doing so allows you to provide defaults and additional metadata.

Parameters
name string The name of this option
options? { description? = string, default? = any, type? = string }
Options for this setting. This table accepts the following fields:

description: A description which may be printed when running the set program.
default: A default value, which is returned by settings.get if the setting has not been changed.
type: Require values to be of this type. Setting the value to another type will error.
Changes
New in version 1.87.0
undefine(name)
Source
Remove a definition of a setting.

If a setting has been changed, this does not remove its value. Use settings.unset for that.

Parameters
name string The name of this option
Changes
New in version 1.87.0
set(name, value)
Source
Set the value of a setting.

Parameters
name string The name of the setting to set
value The setting's value. This cannot be nil, and must be serialisable by textutils.serialize.
Throws
If this value cannot be serialised

See also
settings.unset
get(name [, default])
Source
Get the value of a setting.

Parameters
name string The name of the setting to get.
default? The value to use should there be pre-existing value for this setting. If not given, it will use the setting's default value if given, or nil otherwise.
Returns
The setting's, or the default if the setting has not been changed.
Changes
Changed in version 1.87.0: Now respects default value if pre-defined and default is unset.
getDetails(name)
Source
Get details about a specific setting.

Parameters
name string The name of the setting to get.
Returns
{ description? = string, default? = any, type? = string, value? = any } Information about this setting. This includes all information from settings.define, as well as this setting's value.
Changes
New in version 1.87.0
unset(name)
Source
Remove the value of a setting, setting it to the default.

settings.get will return the default value until the setting's value is set, or the computer is rebooted.

Parameters
name string The name of the setting to unset.
See also
settings.set
settings.clear
clear()
Source
Resets the value of all settings. Equivalent to calling settings.unset

on every setting.
@see settings.unset

getNames()
Source
Get the names of all currently defined settings.

Returns
{ string } An alphabetically sorted list of all currently-defined settings.
load([sPath])
Source
Load settings from the given file.

Existing settings will be merged with any pre-existing ones. Conflicting entries will be overwritten, but any others will be preserved.

Parameters
sPath? string The file to load from, defaulting to .settings.
Returns
boolean Whether settings were successfully read from this file. Reasons for failure may include the file not existing or being corrupted.
See also
settings.save
Changes
Changed in version 1.87.0: sPath is now optional.
save([sPath])
Source
Save settings to the given file.

This will entirely overwrite the pre-existing file. Settings defined in the file, but not currently loaded will be removed.

Parameters
sPath? string The path to save settings to, defaulting to .settings.
Returns
boolean If the settings were successfully saved.
See also
settings.load
Changes
Changed in version 1.87.0: sPath is now optional.
Last updated on 2022-07-16