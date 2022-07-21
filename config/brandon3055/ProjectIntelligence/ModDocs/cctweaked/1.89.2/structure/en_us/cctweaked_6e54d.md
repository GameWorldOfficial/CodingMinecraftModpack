§img[https://tweaked.cc/logo.png]{width:180}
§n                                             §n

Link to the wiki: §link[https://tweaked.cc/]
This is a direct copy paste of the entire CC: Tweaked wiki so the formating may look weird

CC: Tweaked is a mod for Minecraft which adds programmable computers, turtles and more to the game. A fork of the much-beloved ComputerCraft, it continues its legacy with better performance, stability, and a wealth of new features.

CC: Tweaked can be installed from CurseForge or Modrinth. It requires the Minecraft Forge mod loader, but versions are available for Fabric.

Features
Controlled using the Lua programming language, CC: Tweaked's computers provides all the tools you need to start writing code and automating your Minecraft world.

§img[https://tweaked.cc/images/basic-terminal.png]{width:100,tooltip:"A ComputerCraft terminal open and ready to be programmed."} 

While computers are incredibly powerful, they're rather limited by their inability to move about. Turtles are the solution here. They can move about the world, placing and breaking blocks, swinging a sword to protect you from zombies, or whatever else you program them to!

§img[https://tweaked.cc/images/turtle.png]{width:100,tooltip:"A turtle tunneling"} 

Not all problems can be solved with a pickaxe though, and so CC: Tweaked also provides a bunch of additional peripherals for your computers. You can play a tune with speakers, display text or images on a monitor, connect all your computers together with modems, and much more.

Computers can now also interact with inventories such as chests, allowing you to build complex inventory and item management systems.

§img[https://tweaked.cc/images/peripherals.png]{width:100,tooltip:"A chest's contents being read by a computer and displayed on a monitor."} 

Getting Started
While ComputerCraft is lovely for both experienced programmers and for people who have never coded before, it can be a little daunting getting started. Thankfully, there's several fantastic tutorials out there:

Direwolf20's ComputerCraft tutorials
Sethbling's ComputerCraft series
Lyqyd's Computer Basics 1
Once you're a little more familiar with the mod, the sidebar and links below provide more detailed documentation on the various APIs and peripherals provided by the mod.

If you get stuck, do pop in to the Minecraft Computer Mod Discord guild or ComputerCraft's IRC channel.

Get Involved
CC: Tweaked lives on GitHub. If you've got any ideas, feedback or bugs please do create an issue.

Globals
_G Functions in the global environment, defined in bios.lua.
colors Constants and functions for colour values, suitable for working with term and redstone.
colours An alternative version of colors for lovers of British spelling.
commands Execute Minecraft commands and gather data from the results from a command computer.
disk Interact with disk drives.
fs Interact with the computer's files and filesystem, allowing you to manipulate files, directories and paths.
gps Use modems to locate the position of the current turtle or computers.
help Find help files on the current computer.
http Make HTTP requests, sending and receiving data to a remote web server.
io Emulates Lua's standard io library.
keys Constants for all keyboard "key codes", as queued by the key event.
multishell Multishell allows multiple programs to be run at the same time.
os The os API allows interacting with the current computer.
paintutils Utilities for drawing more complex graphics, such as pixels, lines and images.
parallel A simple way to run several functions at once.
peripheral Find and control peripherals attached to this computer.
pocket Control the current pocket computer, adding or removing upgrades.
rednet Communicate with other computers by using modems.
redstone Get and set redstone signals adjacent to this computer.
settings Read and write configuration options for CraftOS and your programs.
shell The shell API provides access to CraftOS's command line interface.
term Interact with a computer's terminal or monitors, writing text and drawing ASCII graphics.
textutils Helpful utilities for formatting and manipulating strings.
turtle Turtles are a robotic device, which can break and place blocks, attack mobs, and move about the world.
vector A basic 3D vector type and some common vector operations.
window A terminal redirect occupying a smaller area of an existing terminal.
Modules
cc.audio.dfpwm Convert between streams of DFPWM audio data and a list of amplitudes.
cc.completion A collection of helper methods for working with input completion, such as that require by _G.read.
cc.expect The cc.expect library provides helper functions for verifying that function arguments are well-formed and of the correct type.
cc.image.nft Read and draw nbt ("Nitrogen Fingers Text") images.
cc.pretty A pretty printer for rendering data structures in an aesthetically pleasing manner.
cc.require A pure Lua implementation of the builtin require function and package library.
cc.shell.completion A collection of helper methods for working with shell completion.
cc.strings Various utilities for working with strings and text.
Peripherals
command This peripheral allows you to interact with command blocks.
computer A computer or turtle wrapped as a peripheral.
drive Disk drives are a peripheral which allow you to read and write to floppy disks and other "mountable media" (such as computers or turtles).
modem Modems allow you to send messages between computers over long distances.
monitor Monitors are a block which act as a terminal, displaying information on one side.
printer The printer peripheral allows pages and books to be printed.
speaker The speaker peirpheral allow your computer to play notes and other sounds.
Generic Peripherals
energy_storage Methods for interacting with blocks using Forge's energy storage system.
fluid_storage Methods for interacting with tanks and other fluid storage blocks.
inventory Methods for interacting with inventories.
Events
alarm The timer event is fired when an alarm started with os.setAlarm completes.
char The char event is fired when a character is typed on the keyboard.
computer_command The computer_command event is fired when the /computercraft queue command is run for the current computer.
disk The disk event is fired when a disk is inserted into an adjacent or networked disk drive.
disk_eject The disk_eject event is fired when a disk is removed from an adjacent or networked disk drive.
http_check The http_check event is fired when a URL check finishes.
http_failure The http_failure event is fired when an HTTP request fails.
http_success The http_success event is fired when an HTTP request returns successfully.
key This event is fired when any key is pressed while the terminal is focused.
key_up Fired whenever a key is released (or the terminal is closed while a key was being pressed).
modem_message The modem_message event is fired when a message is received on an open channel on any modem.
monitor_resize The monitor_resize event is fired when an adjacent or networked monitor's size is changed.
monitor_touch The monitor_touch event is fired when an adjacent or networked Advanced Monitor is right-clicked.
mouse_click This event is fired when the terminal is clicked with a mouse.
mouse_drag This event is fired every time the mouse is moved while a mouse button is being held.
mouse_scroll This event is fired when a mouse wheel is scrolled in the terminal.
mouse_up This event is fired when a mouse button is released or a held mouse leaves the computer's terminal.
paste The paste event is fired when text is pasted into the computer through Ctrl-V (or ⌘V on Mac).
peripheral The peripheral event is fired when a peripheral is attached on a side or to a modem.
peripheral_detach The peripheral_detach event is fired when a peripheral is detached from a side or from a modem.
rednet_message The rednet_message event is fired when a message is sent over Rednet.
redstone The redstone event is fired whenever any redstone inputs on the computer change.
speaker_audio_empty Return Values
task_complete The task_complete event is fired when an asynchronous task completes.
term_resize The term_resize event is fired when the main terminal is resized.
terminate The terminate event is fired when Ctrl-T is held down.
timer The timer event is fired when a timer started with os.startTimer completes.
turtle_inventory The turtle_inventory event is fired when a turtle's inventory is changed.
websocket_closed The websocket_closed event is fired when an open WebSocket connection is closed.
websocket_failure The websocket_failure event is fired when a WebSocket connection request fails.
websocket_message The websocket_message event is fired when a message is received on an open WebSocket connection.
websocket_success The websocket_success event is fired when a WebSocket connection request returns successfully.
Guides
Setting up GPS The gps API allows computers and turtles to find their current position using wireless modems.
Allowing access to local IPs	By default, ComputerCraft blocks access to local IP addresses for security.
Playing audio with speakers	CC: Tweaked's speaker peripheral provides a powerful way to play any audio you like with the speaker.playAudio method.
Reusing code with require	A library is a collection of useful functions and other definitions which is stored separately to your main program.
Reference
Lua 5.2/5.3 features in CC: Tweaked	CC: Tweaked is based off of the Cobalt Lua runtime, which uses Lua 5.
Last updated on 2022-07-16