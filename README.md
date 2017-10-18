# 10.1-Raspberry-Pi-HDMI
Project to allow HDMI output to drive LVDS displays
The Aim for this project was to enable a Raspberry Pi to drive a 10.1" display (to begin with) via the HDMI output.
A HDMI to LVDS converter board which plugs into the HDMI Port of the Raspberry Pi was designed, the aim for this tutorial is to show how to setup the software for the Touch and the HDMI.

Some versions of the HDMI to LVDS board don't have any EDID data and rely on the Raspberry Pi to force an HDMI output.
To enable the HDMI to force data, the following lines are added to the config.txt file located in the /boot/ directory of the Raspberry Pi.
Line to add to config.txt:
hdmi_force_hotplug=1
hdmi_group=2
hdmi_mode=27

or you can use the config.txt file attached to this repository.

Use the follwoing commands to backup the current config.txt file and replace it with the one provided.
1. git clone https://github.com/HM-IHL/10.1-Raspberry-Pi-HDMI.git
2. cd 10.1-Raspberry-Pi-HDMI
3. mv /boot/config.txt /boot/config.txt.backup
4. sudo cp config.txt /boot/config.txt
