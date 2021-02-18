# MMM-DHT-Sensors
This an extension for the [MagicMirror](https://github.com/MichMich/MagicMirror).

The intention is to access DHT11/DHT22 sensors directly within MM without any cronjobs and submitted data via textfiles or stdout/stdin. Both temperature and humidity are displayed onscreen. 

## Requirements

The  [BCM2835](http://www.airspayce.com/mikem/bcm2835/) library is required on your raspberry pi.

[node-dht-sensor](https://github.com/momenso/node-dht-sensor) is required as well.

## Installation

Open a terminal session on your raspberry pi. No matter if you are using ssh or if you access your pi directly.

First of all you need to install the BCM2835 library, in case you don't have it. Just follow the instructions below or look at the libraries website to find the most recent version and updated installation instructions.
```bash
# download the sources
wget http://www.airspayce.com/mikem/bcm2835/bcm2835-1.50.tar.gz
# extract the archive
tar zxvf bcm2835-1.50.tar.gz
cd bcm2835-1.50
# compile and install the library
./configure
make
sudo make check
sudo make install
```

Afterwards we can install the MagicMirror Module. 
```
cd ~/MagicMirror/modules
git clone https://github.com/BrielC/MMM-DHT-Sensors.git
cd MMM-DHT-Sensors
npm install
``` 
Install dependencies. 
```
cd node_modules/node-dht-sensor
npm rebuild --runtime=electron --target=1.3.4 --disturl=https://atom.io/download/atom-shell --abi=49
```
This was done to avoid any version errors.
Last step before we can use the module is to add our user to the GPIO security group.
```
sudo adduser -g $USER gpio
```

## Config
```
{
	module: "MMM-DHT-Sensors",
	position: "top_right",
  	config: {
      		}
},
```
## Screenshot
```
![DHT jpg](https://user-images.githubusercontent.com/52597141/108412285-5b434a80-7232-11eb-8c0e-494a3624e522.jpg)
```
![DHT jpg](https://user-images.githubusercontent.com/52597141/108412958-17047a00-7233-11eb-878b-a4f6d5a29dc7.jpg)
```
