piui
==============

Add a UI to your standalone Raspberry Pi project using your Android or iOS phone

Modified version of the [original project](https://github.com/dps/piui).
Here, the goal is to control the raspberry pi camera module.

Demo
====

[Watch Demo Video](http://youtu.be/2ay0vuW6aNY)

[![Demo Video Screengrab](http://blog.davidsingleton.org/static/ytpiui.png)](http://youtu.be/2ay0vuW6aNY)


Install PiUi
============


The do-it-yourself way
----------------------

Start with the latest release of [Raspbian](http://www.raspberrypi.org/downloads).

Install `nginx` - nginx is an HTTP server and reverse proxy, we use it to multiplex requests to your app and the `piui-supervisor`.

```
sudo apt-get install nginx
```

Configure nginx using the [config file](https://github.com/dps/piui/blob/master/nginx-conf/nginx.conf) in the PiUi github repo - copy this to `/etc/nginx/nginx.conf` and restart nginx.
```
sudo /etc/init.d/nginx restart
```

Get the piui source code from github
```
cd /home/pi
git clone https://github.com/dps/piui.git
```

Arrange for the `piui-supervisor` to run on boot.
```
sudo cp /home/pi/piui/supervisor/piui-supervisor /etc/init.d
sudo update-rc.d piui-supervisor defaults
```

Done!  Run the demo app:
```
cd piui
python piui_demo.py
```

or my personal app:
```
cd piui
python piui.py
```

Connect your phone to the wifi AP and navigate to 'http://<raspberry pi IP>/'.


Known limitations / work in progress
====================================

- only works for one concurrently connected phone right now
- upon reconnection, all historical updates to page elements are made in sequence - should collapse updates to the same element


Copyright and License (BSD 2-clause)
====================================

Copyright (c) 2013, David Singleton
All rights reserved.

Redistribution and use in source and binary forms, with or without modification, are permitted provided that the following conditions are met:

Redistributions of source code must retain the above copyright notice, this list of conditions and the following disclaimer.
Redistributions in binary form must reproduce the above copyright notice, this list of conditions and the following disclaimer in the documentation and/or other materials provided with the distribution.

THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS "AS IS" AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT HOLDER OR CONTRIBUTORS BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.
