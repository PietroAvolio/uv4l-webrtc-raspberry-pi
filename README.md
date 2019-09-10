# UV4L Webrtc on Raspberry Pi 
Here's the link to UV4L Project [https://www.linux-projects.org/uv4l/](https://www.linux-projects.org/uv4l/)



### Setting up the RPI
Please run `sudo raspi-config` and go into 
```diff
- 5 Interfacing Options
```
and make sure to enable the camera. A reboot is recommended right after.

### SRT 
The project can be found here: [SRT Project from GitHub](https://github.com/Haivision/srt).
```bash
sudo apt-get install tclsh pkg-config cmake libssl-dev build-essential
git clone https://github.com/Haivision/srt
cd srt
./configure
make
sudo make install
```
