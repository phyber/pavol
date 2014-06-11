# pavol

`pavol` is a simple command line interface for setting PulseAudio volume.

## Usage

`pavol` can be called in a few different ways. The simplest way is to call it
with a single argument, for example:

~~~ shell
$ pavol +10%
~~~

This command would set the volume relative to your current volume on the
default sink. So if you were at 50% volume before, you would now be at
60% volume.

You may also specify which sink you wish to set the volume on.

~~~ shell
$ pavol analog-stereo -5%
~~~

Toggling the mute status is also possible by passing the word `toggle` instead
of a volume level.

~~~ shell
$ pavol analog-stereo toggle
~~~

The volume argument (unless it is set to `toggle`) is passed as-is through to
`pactl`. To see more information about the volume argument, you should check
the `set-sink-volume` section of the `pactl(1)` man page.

## Debugging

If you believe that `pavol` isn't behaving itself for some reason, you can try
to get a better look at what it's doing by setting the `PAVOL_DEBUG`
environment variable. You may set it to any value, pavol only checks for its
existance, not its content.

~~~ shell
$ PAVOL_DEBUG=1 pavol analog-stereo +1%
C: set-sink-volume. S: alsa_output.pci-0000_00_1b.0.analog-stereo. V: +1%.
~~~

The C, S and V values here are the Command, Sink and Volume that are going to
be passed to `pactl`.
