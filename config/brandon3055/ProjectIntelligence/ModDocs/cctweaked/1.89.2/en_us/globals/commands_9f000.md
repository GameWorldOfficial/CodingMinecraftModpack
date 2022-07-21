commands
Execute Minecraft commands and gather data from the results from a command computer.

🛈 NOTE
This API is only available on Command computers. It is not accessible to normal players.

While one may use commands.exec directly to execute a command, the commands API also provides helper methods to execute every command. For instance, commands.say("Hi!") is equivalent to commands.exec("say Hi!").

commands.async provides a similar interface to execute asynchronous commands. commands.async.say("Hi!") is equivalent to commands.execAsync("say Hi!").

Usage
Set the block above this computer to stone:

Run ᐅcommands.setblock("~", "~1", "~", "minecraft:stone")
Changes
New in version 1.7
native	The builtin commands API, without any generated command helper functions
async	A table containing asynchronous wrappers for all commands.
exec(command)	Execute a specific command.
execAsync(command)	Asynchronously execute a command.
list(...)	List all available commands which the computer has permission to execute.
getBlockPosition()	Get the position of the current command computer.
getBlockInfos(minX, minY, minZ, maxX, maxY, maxZ [, dimension])	Get information about a range of blocks.
getBlockInfo(x, y, z [, dimension])	Get some basic information about a block.
native
Source
The builtin commands API, without any generated command helper functions

This may be useful if a built-in function (such as commands.list) has been overwritten by a command.

async
Source
A table containing asynchronous wrappers for all commands.

As with commands.execAsync, this returns the "task id" of the enqueued command.

Usage
Asynchronously sets the block above the computer to stone.

Run ᐅcommands.async.setblock("~", "~1", "~", "minecraft:stone")
See also
execAsync
exec(command)
Source
Execute a specific command.

Parameters
command string The command to execute.
Returns
boolean Whether the command executed successfully.
{ string... } The output of this command, as a list of lines.
number | nil The number of "affected" objects, or nil if the command failed. The definition of this varies from command to command.
Usage
Set the block above the command computer to stone.

Run ᐅcommands.exec("setblock ~ ~1 ~ minecraft:stone")
Changes
Changed in version 1.71: Added return value with command output.
Changed in version 1.85.0: Added return value with the number of affected objects.
execAsync(command)
Source
Asynchronously execute a command.

Unlike exec, this will immediately return, instead of waiting for the command to execute. This allows you to run multiple commands at the same time.

When this command has finished executing, it will queue a task_complete event containing the result of executing this command (what exec would return).

Parameters
command string The command to execute.
Returns
number The "task id". When this command has been executed, it will queue a task_complete event with a matching id.
Usage
Asynchronously sets the block above the computer to stone.

Run ᐅcommands.execAsync("setblock ~ ~1 ~ minecraft:stone")
See also
parallel One may also use the parallel API to run multiple commands at once.
list(...)
Source
List all available commands which the computer has permission to execute.

Parameters
... string The sub-command to complete.
Returns
{ string... } A list of all available commands
getBlockPosition()
Source
Get the position of the current command computer.

Returns
number This computer's x position.
number This computer's y position.
number This computer's z position.
See also
gps.locate To get the position of a non-command computer.
getBlockInfos(minX, minY, minZ, maxX, maxY, maxZ [, dimension])
Source
Get information about a range of blocks.

This returns the same information as getBlockInfo, just for multiple blocks at once.

Blocks are traversed by ascending y level, followed by z and x - the returned table may be indexed using x + z*width + y*depth*depth.

Parameters
minX number The start x coordinate of the range to query.
minY number The start y coordinate of the range to query.
minZ number The start z coordinate of the range to query.
maxX number The end x coordinate of the range to query.
maxY number The end y coordinate of the range to query.
maxZ number The end z coordinate of the range to query.
dimension? string The dimension to query (e.g. "minecraft:overworld"). Defaults to the current dimension.
Returns
{ table... } A list of information about each block.
Throws
If the coordinates are not within the world.

If trying to get information about more than 4096 blocks.

Changes
New in version 1.76
Changed in version 1.99: Added dimension argument.
getBlockInfo(x, y, z [, dimension])
Source
Get some basic information about a block.

The returned table contains the current name, metadata and block state (as with turtle.inspect). If there is a tile entity for that block, its NBT will also be returned.

Parameters
x number The x position of the block to query.
y number The y position of the block to query.
z number The z position of the block to query.
dimension? string The dimension to query (e.g. "minecraft:overworld"). Defaults to the current dimension.
Returns
table The given block's information.
Throws
If the coordinates are not within the world, or are not currently loaded.

Changes
Changed in version 1.76: Added block state info to return value
Changed in version 1.99: Added dimension argument.
Last updated on 2022-07-16