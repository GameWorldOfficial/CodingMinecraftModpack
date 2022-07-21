cc.image.nft
Read and draw nbt ("Nitrogen Fingers Text") images.

nft ("Nitrogen Fingers Text") is a file format for drawing basic images. Unlike the images that paintutils.parseImage uses, nft supports coloured text as well as simple coloured pixels.

Usage
Load an image from example.nft and draw it.

Run ᐅlocal nft = require "cc.image.nft"
local image = assert(nft.load("data/example.nft"))
nft.draw(image, term.getCursorPos())
Changes
New in version 1.90.0
parse(image)	Parse an nft image from a string.
load(path)	Load an nft image from a file.
draw(image, xPos, xPos [, target])	Draw an nft image to the screen.
parse(image)
Source
Parse an nft image from a string.

Parameters
image string The image contents.
Returns
table The parsed image.
load(path)
Source
Load an nft image from a file.

Parameters
path string The file to load.
Returns
table The parsed image.
Or
nil If the file does not exist or could not be loaded.
string An error message explaining why the file could not be loaded.
draw(image, xPos, xPos [, target])
Source
Draw an nft image to the screen.

Parameters
image table An image, as returned from load or draw.
xPos number The x position to start drawing at.
xPos number The y position to start drawing at.
target? term.Redirect The terminal redirect to draw to. Defaults to the current terminal.
Last updated on 2022-07-16