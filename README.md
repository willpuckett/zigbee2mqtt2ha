# zigbee2mqtt2ha

A quick and easy setup for [HomeAssistant](https://www.home-assistant.io) with [MQTT](https://mosquitto.org) and [Zigbee2MQTT](https://www.zigbee2mqtt.io) in [Docker](https://www.docker.com). I ran the hassio image for a while, but kept having problems. Although I was probably fighting my own ignorance as much as anything, suddenly everything got a lot easier and ran better when I switched to this Docker install.

Based on ARM images configured for a [Deconz RaspbeeII](https://phoscon.de/en/raspbee) on [Raspberry Pi](https://www.raspberrypi.org), but *easily adaptable* via `zigbee2mqtt/configuration.yaml` (it's pretty good at finding most adapters so you can try commenting out the whole "serial" section and use the web interface to configure). Also minimally tested on Apple M1 (it all loads and starts up but I don't have an adapter handy to test Zigbee with).

## Installation

Follow the steps for **RTC-Installation** [here](https://phoscon.de/en/raspbee2/install), then SKIP the "deCONZ Installation" steps on that page. Run the first step of the "Docker Installation" section (`sudo raspiconfig` > Options > Serial > "No! login shell accessible over serial" and "Yes! hardware serial port enabled"). Then run the instructions [here](https://phoenixnap.com/kb/docker-on-raspberry-pi) to get docker installed.

Clone this repo (`git clone https://github.com/willpuckett/zigbee2mqtt2ha`) and cd in, then:

  1. `docker-compose up -d`
  2. `docker exec -it mqtt /bin/sh`
  3. Run `mosquitto_passwd /mosquitto/config/password_file insert-username-here` repeatedly to create as many username/password combos as you need (I use seperate ones for zigbee2mqtt, ha, and various types of devices around the house, although if you only create one and reuse it everywhere, 🤷🏻‍♂️, but *do* jot them down as you create them...).
  4. `exit`
  5. `nano zigbee2mqtt/configuration.yaml` to fill the password you just created
  6. `docker-compose restart`
  7. And!... fill in your mqtt user/pass in the home assistant integration when it starts up.

## Configuration

zigbee2mqtt is configured to show it's web interface at `http://your-docker-machine-ip:8080`. The basic auth doesn't work in safari, so I left it disabled see [here](https://www.zigbee2mqtt.io/information/frontend.html) for more detail.

After devices are configured in zigbee2mqtt, you can `http://your-docker-machine-ip:8123` to get Home Assistant setup
