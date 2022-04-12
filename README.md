

Concept behind Live-Tracker is simple, just like we host phishing pages to get credentials why not host a fake page that requests your location like many popular location based websites. Read more on <a href="https://scaninfoga.in"> scaninfoga's Blog </a>.Live-Tracker Hosts a fake website which asks for Location Permission and if the target allows it, we can get :

* Longitude
* Latitude
* Accuracy
* Altitude - Not always available
* Direction - Only available if user is moving
* Speed - Only available if user is moving

Along with Location Information we also get **Device Information** without any permissions :

* Unique ID using Canvas Fingerprinting
* Device Model - Not always available
* Operating System
* Platform
* Number of CPU Cores - Approximate Results
* Amount of RAM - Approximate Results
* Screen Resolution
* GPU information
* Browser Name and Version
* Public IP Address
* Local IP Address
* Local Port

**Automatic IP Address Reconnaissance** is performed after the above information is received.

**This tool is a Proof of Concept and is for Educational Purposes Only, Live-Tracker shows what data a malicious website can gather about you and your devices and why you should not click on random links and allow critical permissions such as Location etc.**

## How is this Different from IP GeoLocation

* Other tools and services offer IP Geolocation which is NOT accurate at all and does not give location of the target instead it is the approximate location of the ISP.

* Live-Tracker uses HTML API and gets Location Permission and then grabs Longitude and Latitude using GPS Hardware which is present in the device, so Live-Tracker works best with Smartphones, if the GPS Hardware is not present, such as on a Laptop, Live-Tracker fallbacks to IP Geolocation or it will look for Cached Coordinates.  

* Generally if a user accepts location permsission, Accuracy of the information recieved is **accurate to approximately 30 meters**

* Accuracy depends on multiple factors which you may or may not control such as :
  * Device - Won't work on laptops or phones which have broken GPS
  * Browser - Some browsers block javascripts
  * GPS Calibration - If GPS is not calibrated you may get inaccurate results and this is very common

## Templates

Available Templates : 

* NearYou
* Google Drive (Suggested by @Rohan Nahak)
* WhatsApp (Suggested by @scaninfoga)
* Telegram
* Zoom (Made by @R-Security)

## Tested On :

* Kali Linux
* BlackArch Linux
* Ubuntu
* Kali Nethunter
* Termux
* Parrot OS
* OSX - Monterey v.12.0.1

## Installation

### Kali Linux / Arch Linux / Ubuntu / Parrot OS / Termux

```bash
git clone https://github.com/scaninfoga/Live-Tracker.git
cd Live-Tracker/
chmod +x install.sh
./install.sh
```

### BlackArch Linux

```bash
sudo pacman -S Live-Tracker
```

### Docker

```bash
docker pull scaninfoga/Live-Tracker
```

### OSX
```bash
git clone https://github.com/scaninfoga/Live-Tracker.py
cd Live-Tracker/
python3 Live-Tracker.py
````

In order to run in tunnel mode, install ngrok by running this command in the terminal:
```bash
brew install ngrok/ngrok/ngrok

ngrok http 8080
````

## Usage

```bash
python3 Live-Tracker.py -h

usage: Live-Tracker.py [-h] [-k KML] [-p PORT] [-u] [-v]

options:
  -h, --help            show this help message and exit
  -k KML, --kml KML     KML filename
  -p PORT, --port PORT  Web server port [ Default : 8080 ]
  -u, --update          Check for updates
  -v, --version         Prints version

##################
# Usage Examples #
##################

# Step 1 : In first terminal
$ python3 Live-Tracker.py

# Step 2 : In second terminal start a tunnel service such as ngrok
$ ./ngrok http 8080

###########
# Options #
###########

# Ouput KML File for Google Earth
$ python3 Live-Tracker.py -k <filename>

# Use Port
$ python3 Live-Tracker.py -p 8080
$ ./ngrok http 8080

################
# Docker Usage #
################

# Step 1
$ docker network create ngroknet

# Step 2
$ docker run --rm -it --net ngroknet --name Live-Tracker scaninfoga/Live-Tracker

# Step 3
$ docker run --rm -it --net ngroknet --name ngrok wernight/ngrok ngrok http Live-Tracker:8080
```

## Local Tunnels
Use
```
ssh -R 80:localhost:8080 nokey@localhost.run
```
as an alterntive to ngrok

## Demo

**YouTube**

<a href="https://www.youtube.com/channel/UCl9W4KnQ0Yk8HQdxlcFP7Zg/videos">
  <img src="http://scaninfoga.in/wp-content/uploads/2022/04/scaninfoga12.png">
</a>
