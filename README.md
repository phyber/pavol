# pavol

`pavol` is a simple command line interface for setting PulseAudio volume.

## Usage

`pavol` can be called in a few different ways. The simplest way is to call it
with a single argument, for example:

~~~ shell
pavol +10%
~~~

This command would set the volume relative to your current volume on the
default sink. So if you were at 50% volume before, you would now be at
60% volume.

You may also specify which sink you wish to set the volume on.

~~~ shell
pavol analog-stereo -5%
~~~

Toggling the mute status is also possible by passing the word `toggle` instead
of a volume level.

~~~ shell
pavol analog-stereo toggle
~~~
