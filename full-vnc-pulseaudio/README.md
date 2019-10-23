How to carry audio over SSH?
----------------------------

> The easy way: Run `paprefs`, go to *Network Server* and check *Enable
> network access to local sound devices*.

You need to install it using

    sudo apt-get install paprefs

> Whenever you SSH with X11 forwarding enabled, PulseAudio programs use
> X11 to discover your sound server (use `pax11publish` or

>     xprop -root PULSE_SERVER
>
> to see for yourself). Just tell PulseAudio to listen for
> network connections (`paprefs` as described above), and all X11
> programs will be able to use it. 
> 
> (Other users will not have access to your sound server, unless you
> allow it yourself in `paprefs`. The authentication data is carried
> over in the X11 `PULSE_COOKIE` property, or you can copy
> `~/.pulse_cookie` manually.)
> 
> Note however, that the PulseAudio stream is not encrypted this way, so
> it is okay for use at home, but not over the Internet.
> 
> ---
> 
> The slightly more complicated way: Enable network access as above, but
> tunnel PulseAudio over SSH TCP forwarding. Use `pax11publish` to
> discover your PulseAudio port (usually 4713), connect with
>
>     ssh -R > 24713:localhost:4713`
>
> then run
>
>     export PULSE_SERVER="tcp:localhost:24713"
>
> This will be slightly slower due to SSH overhead, but is safe to use
> over the Internet.
