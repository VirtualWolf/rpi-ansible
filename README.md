# rpi-ansible

## Overview

This repository contains the [Ansible](https://www.ansible.com) playbooks I use to automate configuration of the various Raspberry Pis I have running at home.

* `playbooks/dashboard.yml` configures Raspberry Pi Zero Ws/Zero 2 Ws with attached [Pimoroni HyperPixel 4 TFT displays](https://shop.pimoroni.com/products/hyperpixel-4?variant=12569539706963) that display the temperature/power usage dashboard and a clock from my [pi-home-dashboard](https://github.com/VirtualWolf/pi-home-dashboard) repository.
* `playbooks/e_ink_dashboards.yml` configures the Raspberry Pi 3B+ with attached 2.7" [Pi Supply e-ink display](https://uk.pi-supply.com/products/papirus-epaper-eink-screen-hat-for-raspberry-pi) that displays the temperature and humidity from my [pi-home-dashboard](https://github.com/VirtualWolf/pi-home-dashboard) repository.
* `playbooks/server.yml` configures the Raspberry Pi 4B+ that runs everything else.

## Optional: Adding a self-contained Ansible installation

* Install and configure [pyenv](https://github.com/pyenv/pyenv)
* Install the version of Python for this project — `pyenv install`
* Add a new virtualenv for this project — `python3 -m venv .venv`
* Activate the virtualenv — `. .venv/bin/activate`
* Install Ansible — `pip3 install -r requirements.txt`

Before running any `ansible-playbook` commands, load the virtualenv with `. .venv/bin/activate`.

## Running
Run as `ansible-playbook playbooks/<playbook>.yml`.

To specify a single host, add `-l <host>`.

To run only a specific subset of a playbook, use one of the tags described below with the `-t` flag.

## Tags

To make it easier to run individual tasks that might need occasionally updating separately from running every task in an entire playbook, the following tags are available:

### `server.yml`, `dashboards.yml`, `e_ink_dashboards.yml`
* `install-packages` — Updates to packages installed with `apt install` can be applied to all the runbooks with this tag.

### `server.yml`
* `chrony`
* `nodejs`
* `mosquitto`
* `pi-home-dashboard`
* `pvoutput-uploader`
* `shairport-sync`

### `dashboards.yml`
* `browser` — Configures the web browsers and the URL they'll launch to on boot.
* `hyperpixel-brightness-control` — Pulls updates from the hyperpixel-brightness-control repository and updates configuration settings.
* `refresh-dashboard` — This won't run without explicitly setting the `--tags refresh-dashboard` flag and will do a full browser refresh, useful for picking up changes in the Pi Home Dashboard pages.

### `update_config_repository_and_bashmarks.yml`
* `update_config_only` — Only pulls the latest commits from the configuration repository and doesn't do anything else.
