# Kubernetes Raspberry Pi 4 Cluster

This is documentation on how I have configured a kubernetes cluster in my raspberry pi homelab. this will be the IoT to run development services in my home lab such as Spark clusters, APIs, and Microservices

## Overview

This homelab consists of 4 raspberry pis one will be designated as the manager service for the kubernetes cluster will the others will be nodes 1-3.

Two things to not about the hardware choices:

One, I went with 1tb ssds, while that may be overkill in some cases some of these pis will also be used to house databases and blob storage outside of the kubernetes cluster so better safe than sorry.

Two, The PoE switch is rated for 78w of power so roughly 78w/4 = 19.5w per pi. This should be find to power pi in most cases since the standard pi power supply is 15w but with the added power draw from the ssd, poe hats and fans, this could cause issues under heavy loading in the long run. I would recommend if your conserned with underpowering to pis to try and find a 100w rated PoE switch to so you can consitantly get that sweet spot, 20w per pi with a 20% overhead.

### Hardware

- 4x Raspberry Pi 4b (8gb ram)
- 4x 32gb Micro sd (Boat loading)
- 4x 1tb SSD (usb 3 to sata connection)
- 4x Raspberry Pi PoE Hat
- Mokerlink 78w 4-port PoE switch
- 2x Cooling Fans

### Software

- Ubuntu Server 23.0.4 x64 LTS
- Docker
- Kubernetes

## Configuring Ubuntu Servers

Configuring Ubuntu Server for pis is pretty straight forward:

Download the [Raspberry Pi Imager](https://www.raspberrypi.com/software/). Select your flavor of ubuntu server under general OS
(**Go with a x32 installation if using pi 3 or low ram pi 4**). Select a micro sd to install it on. Then in advanced setting configure ssh. Repeat x4

## Installing Docker
