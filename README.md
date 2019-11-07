# UV4L Webrtc on Raspberry Pi 
Here's the link to UV4L Project [https://www.linux-projects.org/uv4l/](https://www.linux-projects.org/uv4l/)

This guide is intended for Raspbian 10 Buster and was tested on a raspberry PI 3B+

### Setting up the RPI
Run `sudo raspi-config` and go into 
```diff
- 5 Interfacing Options
```
and make sure to enable the camera. A reboot is recommended right after.

### Installation
Execute the following commands
```bash
curl http://www.linux-projects.org/listing/uv4l_repo/lpkey.asc | sudo apt-key add -
```
add this line to /etc/apt/sources.list 
```bash
deb http://www.linux-projects.org/listing/uv4l_repo/raspbian/stretch stretch main
```
and then
```bash
sudo apt update
sudo apt upgrade
sudo apt-get install uv4l uv4l-raspicam uv4l-server uv4l-webrtc uv4l-raspicam-sextras
```

reboot the PI.

### Configuration
Edit the file /uv4l/uv4l-raspicam.conf as follows (only relevant lines are reported)
```bash
video_nr = 0
encoding = h264
width = 1640
height = 922
framerate = 40
profile = baseline
custom-sensor-config = 5
server-option = --enable-webrtc-audio = no
server-option = --webrtc-receive-audio = no
```

To remove the watermark from the video it is necessary to obtain a license from the project owner.
The license should be placed in the configuration file

### STUN server
There are several STUN server open source implementation available.
We succesfully tested and used [Stuntman](http://www.stunprotocol.org/) on Windows.

### Usage
On the RPI:
```bash
sudo rm /dev/video0
sudo pkill uv4l
sudo uv4l --driver raspicam --driver-config-file /etc/uv4l/uv4l-raspicam.conf --video_nr 0 --sched-rr 0
```

to kill the process

```bash
sudo pkill uv4l
sudo rm /dev/vide0
```

On the receive, download the webrtc-client.html from this folder
