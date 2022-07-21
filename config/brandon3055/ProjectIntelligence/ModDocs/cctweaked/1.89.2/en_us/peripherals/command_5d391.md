command
This peripheral allows you to interact with command blocks.

Command blocks are only wrapped as peripherals if the enable_command_block option is true within the config.

This API is not the same as the commands API, which is exposed on command computers.

getCommand()	Get the command this command block will run.
setCommand(command)	Set the command block's command.
runCommand()	Execute the command block once.
getCommand()
Source
Get the command this command block will run.

Returns
string The current command.
setCommand(command)
Source
Set the command block's command.

Parameters
command string The new command.
runCommand()
Source
Execute the command block once.

Returns
boolean If the command completed successfully.
string | nil A failure message.
Last updated on 2022-07-16