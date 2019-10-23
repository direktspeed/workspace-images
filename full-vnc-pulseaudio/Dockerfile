FROM full-vnc
### Server (Your Client) The Machine Your Sitting at
# apt-get install pulseaudio pulseaudio-module-zeroconf avahi-daemon dbus-x11
# /etc/pulse/system.pa
# load-module module-native-protocol-tcp auth-ip-acl=127.0.0.1;192.168.0.0/24
# load-module module-zeroconf-publish
### Client (your Workspace)
## Method 1 graphical
# apt-get install paprefs
# pulseaudio -k && pulseaudio --start
## Method 2 console
# apt-get install pulseaudio dbus-x11
# /etc/pulse/default.pa
# load-module module-tunnel-sink-new server=192.168.0.1 sink_name=Remote channels=2 rate=44100
# We need a way to start pulse audio
