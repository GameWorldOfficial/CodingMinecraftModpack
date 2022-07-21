speaker
The speaker peirpheral allow your computer to play notes and other sounds.

The speaker can play three kinds of sound, in increasing orders of complexity:

playNote allows you to play noteblock note.
playSound plays any built-in Minecraft sound, such as block sounds or mob noises.
playAudio can play arbitrary audio.
Recipe
§recipe[computercraft:peripheral,1,5]{spacing:4}
Changes
New in version 1.80pr1
playNote(instrument [, volume [, pitch]])	Plays a note block note through the speaker.
playSound(name [, volume [, pitch]])	Plays a Minecraft sound through the speaker.
playAudio(audio [, volume])	Attempt to stream some audio data to the speaker.
stop()	Stop all audio being played by this speaker.
playNote(instrument [, volume [, pitch]])
Source
Plays a note block note through the speaker.

This takes the name of a note to play, as well as optionally the volume and pitch to play the note at.

The pitch argument uses semitones as the unit. This directly maps to the number of clicks on a note block. For reference, 0, 12, and 24 map to F#, and 6 and 18 map to C.

A maximum of 8 notes can be played in a single tick. If this limit is hit, this function will return false.

Valid instruments
The speaker supports all of Minecraft's noteblock instruments. These are:

"harp", "basedrum", "snare", "hat", "bass", @code "flute"}, "bell", "guitar", "chime", "xylophone", "iron_xylophone", "cow_bell", "didgeridoo", "bit", "banjo" and "pling".

Parameters
instrument string The instrument to use to play this note.
volume? number The volume to play the note at, from 0.0 to 3.0. Defaults to 1.0.
pitch? number The pitch to play the note at in semitones, from 0 to 24. Defaults to 12.
Returns
boolean Whether the note could be played as the limit was reached.
Throws
If the instrument doesn't exist.

playSound(name [, volume [, pitch]])
Source
Plays a Minecraft sound through the speaker.

This takes the name of a Minecraft sound, such as "minecraft:block.note_block.harp", as well as an optional volume and pitch.

Only one sound can be played at once. This function will return false if another sound was started this tick, or if some audio is still playing.

Parameters
name string The name of the sound to play.
volume? number The volume to play the sound at, from 0.0 to 3.0. Defaults to 1.0.
pitch? number The speed to play the sound at, from 0.5 to 2.0. Defaults to 1.0.
Returns
boolean Whether the sound could be played.
Throws
If the sound name was invalid.

Usage
Play a creeper hiss with the speaker.

Run ᐅlocal speaker = peripheral.find("speaker")
speaker.playSound("entity.creeper.primed")
playAudio(audio [, volume])
Source
Attempt to stream some audio data to the speaker.

This accepts a list of audio samples as amplitudes between -128 and 127. These are stored in an internal buffer and played back at 48kHz. If this buffer is full, this function will return false. You should wait for a speaker_audio_empty event before trying again.

🛈 NOTE
The speaker only buffers a single call to playAudio at once. This means if you try to play a small number of samples, you'll have a lot of stutter. You should try to play as many samples in one call as possible (up to 128×1024), as this reduces the chances of audio stuttering or halting, especially when the server or computer is lagging.

Playing audio with speakers provides a more complete guide to using speakers

Parameters
audio { number... } A list of amplitudes.
volume? number The volume to play this audio at. If not given, defaults to the previous volume given to playAudio.
Returns
boolean If there was room to accept this audio data.
Throws
If the audio data is malformed.

Usage
Read an audio file, decode it using cc.audio.dfpwm, and play it using the speaker.

Run ᐅlocal dfpwm = require("cc.audio.dfpwm")
local speaker = peripheral.find("speaker")

local decoder = dfpwm.make_decoder()
for chunk in io.lines("data/example.dfpwm", 16 * 1024) do
    local buffer = decoder(chunk)

    while not speaker.playAudio(buffer) do
        os.pullEvent("speaker_audio_empty")
    end
end
See also
cc.audio.dfpwm Provides utilities for decoding DFPWM audio files into a format which can be played by the speaker.
Playing audio with speakers For a more complete introduction to the playAudio function.
Changes
New in version 1.100
stop()
Source
Stop all audio being played by this speaker.

This clears any audio that playAudio had queued and stops the latest sound played by playSound.

Changes
New in version 1.100
Last updated on 2022-07-16