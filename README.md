# rpi-ansible

## Overview

This repository contains the [Ansible](https://www.ansible.com) playbooks I use to automate configuration of the various Raspberry Pis I have running at home.

* `playbooks/dashboard.yml` configures Raspberry Pi Zero Ws/Zero 2 Ws with attached [Pimoroni HyperPixel 4 TFT displays](https://shop.pimoroni.com/products/hyperpixel-4?variant=12569539706963) that display the temperature/power usage dashboard and a clock from my [pi-home-dashboard](https://github.com/VirtualWolf/pi-home-dashboard) repository.
* `playbooks/e_ink_dashboards.yml` configures the Raspberry Pi 3B+ with attached 2.7" [Pi Supply e-ink display](https://uk.pi-supply.com/products/papirus-epaper-eink-screen-hat-for-raspberry-pi) that displays the temperature and humidity from my [pi-home-dashboard](https://github.com/VirtualWolf/pi-home-dashboard) repository.
* `playbooks/server.yml` configures the Raspberry Pi 4B+ that runs everything else.

## Running
Run as `ansible-playbook playbooks/<playbook>.yml`.

To specify a single host, add `-l <host>`.

To run only a specific subset of a playbook, use one of the tags described below.

## Tags

To make it easier to run individual tasks that might need occasionally updating separately from running every task in an entire playbook, the following tags are available:

### `playbooks/server.yml`
* `chrony`
* `nvm_and_nodejs`
* `mosquitto`
* `pi-home-dashboard`
* `pvoutput-uploader`
* `shairport-sync`

### `playbooks/dashboards.yml`
* `browser`
