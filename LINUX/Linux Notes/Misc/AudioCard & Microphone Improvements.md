### AudioCard

GUI-tool:
sudo apt install pavucontrol

Check SoundCard:
pulseaudio --dump-resample-methods

Cahnge options:
sudo nano /etc/pulse/daemon.conf

default-sample-format = s24le
default-sample-rate = 192000
alternate-sample-rate = 192000

REBOOT

___

### Microphone

GUI-tool:
sudo apt install pavucontrol

--------------------------------------------------------------------------------

### Misc

Шумоподавление микрофона:
sudo nano /etc/pulse/default.pa

Add to end of the file:
load-module module-echo-cancel source_name=noechosource sink_name=noechosink
set-default-source noechosource

REBOOT