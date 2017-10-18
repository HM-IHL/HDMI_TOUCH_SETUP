# 10.1-Raspberry-Pi-HDMI
Project to allow HDMI output to drive LVDS displays
The Aim for this project was to enable a Raspberry Pi to drive a 10.1" display (to begin with) via the HDMI output.
A HDMI to LVDS converter board which plugs into the HDMI Port of the Raspberry Pi was designed, the aim for this tutorial is to show how to setup the software for the Touch and the HDMI.

Some versions of the HDMI to LVDS board don't have any EDID data and rely on the Raspberry Pi to force an HDMI output.
To enable the HDMI to force data, the following lines are added to the config.txt file located in the /boot/ directory of the Raspberry Pi.
Lines of code to add to config.txt:

hdmi_force_hotplug=1

hdmi_group=2

hdmi_mode=27

or you can use the config.txt file attached to this repository.

Use the following commands to backup the current config.txt file and replace it with the one provided.
1. git clone https://github.com/HM-IHL/10.1-Raspberry-Pi-HDMI.git
2. cd 10.1-Raspberry-Pi-HDMI
3. mv /boot/config.txt /boot/config.txt.backup
4. sudo cp config.txt /boot/config.txt

Once you reboot the Raspberry Pi you should get an image on the display.
*Note that currently the config.txt is setup to allow a resolution of 1280 x 800 to be output via the HDMI port.

To setup the touch you will need to add another line of code into the config.txt file.

If you have copied the config.txt file provided you can miss this step.

1. Add the following line into config.txt:

dtoverlay=pitft28-capacitive

This will enable the Dtoverlay for the Raspberry Pi.

Now we have to change the resolution settings of the touchscreen.
1. sudo nano /usr/shar/X11/xorg.conf.d/10-evdev.conf
2. Add the following line before the last EndSection line:
Option " Calibration" " 0 1280 0 800"

once you reboot the Raspberry Pi, Assuming You have connected the touch screen and the display as per the assembly instructions, you will now have a working 10.1" dispaly with touch screen.

If you want to enable the right click function Please see the other repository https://github.com/HM-IHL/10.1-Touch-RPI
