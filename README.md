# Home Assistant Configurations 🏡✨

Welcome to my Home Assistant Configs repository! Here, you will find all the configurations I use to automate my home. This project focuses on integrating various smart devices, enhancing home automation, and creating a seamless user experience.

[![Download Releases](https://img.shields.io/badge/Download%20Releases-blue.svg)](https://github.com/YHONCARLOSCHOQUEHUANCA/Home-Assistant/releases)

## Table of Contents

- [Introduction](#introduction)
- [Features](#features)
- [Getting Started](#getting-started)
- [Configuration Overview](#configuration-overview)
- [Supported Devices](#supported-devices)
- [Automation Examples](#automation-examples)
- [Using Zigbee2MQTT](#using-zigbee2mqtt)
- [Contributing](#contributing)
- [License](#license)
- [Contact](#contact)

## Introduction

Home Assistant is an open-source platform for smart home automation. It allows you to control and automate devices from different manufacturers through a single interface. This repository contains my personal configurations for Home Assistant, including integrations for various devices and automation scripts.

## Features

- **Voice Control**: Integrate with Alexa for voice commands.
- **Climate Control**: Manage heating and cooling systems efficiently.
- **Doorbell Notifications**: Get alerts when someone rings your doorbell.
- **Lighting Automation**: Control lights based on time or events.
- **Zigbee Support**: Connect Zigbee devices easily with Zigbee2MQTT.
- **YAML Configuration**: All configurations are written in YAML for easy readability.

## Getting Started

To get started with Home Assistant, follow these steps:

1. **Install Home Assistant**: You can install it on various platforms, including Raspberry Pi, Docker, or a virtual machine.
2. **Clone the Repository**: Use the following command to clone the repository:
   ```bash
   git clone https://github.com/YHONCARLOSCHOQUEHUANCA/Home-Assistant.git
   ```
3. **Navigate to the Directory**: Change to the repository directory:
   ```bash
   cd Home-Assistant
   ```
4. **Download Releases**: Visit the [Releases](https://github.com/YHONCARLOSCHOQUEHUANCA/Home-Assistant/releases) section to download the latest configurations. Make sure to execute the necessary files to apply the configurations.

## Configuration Overview

The configuration files are organized into several directories:

- **automations**: Contains automation scripts that define how devices interact.
- **scenes**: Stores scenes that set multiple devices to specific states.
- **scripts**: Includes scripts for more complex actions and interactions.
- **configuration.yaml**: The main configuration file for Home Assistant.

### Example Configuration

Here’s a simple example of how to configure a light automation in `automations.yaml`:

```yaml
- alias: Turn on lights at sunset
  trigger:
    platform: sun
    event: sunset
  action:
    service: light.turn_on
    entity_id: light.living_room
```

## Supported Devices

This repository supports a wide range of devices, including:

- **Smart Lights**: Philips Hue, LIFX, and others.
- **Smart Thermostats**: Nest, Ecobee, and similar.
- **Smart Doorbells**: Ring, Nest Hello, etc.
- **Zigbee Devices**: Various sensors and switches that work with Zigbee2MQTT.

## Automation Examples

### Voice-Controlled Lighting

Integrate your lights with Alexa to control them using voice commands. Here’s how to set it up:

1. **Enable the Alexa Integration**: Follow the documentation to enable the Alexa integration in Home Assistant.
2. **Create a Voice Command**: Use the following YAML to create a command for turning on the living room lights:

```yaml
- alias: Alexa Turn On Living Room Lights
  trigger:
    platform: event
    event_type: alexa_smart_home
    event_data:
      request:
        namespace: Alexa.PowerController
        name: TurnOn
  action:
    service: light.turn_on
    entity_id: light.living_room
```

### Doorbell Notifications

Get notified when someone rings your doorbell. Here’s a simple automation:

```yaml
- alias: Doorbell Notification
  trigger:
    platform: state
    entity_id: binary_sensor.doorbell
    to: 'on'
  action:
    service: notify.notify
    data:
      message: "Someone is at the door!"
```

## Using Zigbee2MQTT

Zigbee2MQTT allows you to connect Zigbee devices to Home Assistant easily. Here’s how to set it up:

1. **Install Zigbee2MQTT**: Follow the installation guide on the [Zigbee2MQTT documentation](https://www.zigbee2mqtt.io/).
2. **Configure Zigbee2MQTT**: Update the `configuration.yaml` in the Zigbee2MQTT directory to include your devices.
3. **Connect to Home Assistant**: Add the MQTT integration in Home Assistant to start receiving data from your Zigbee devices.

### Example Zigbee Configuration

Here’s an example configuration for a Zigbee light:

```yaml
devices:
  '0x00124b0018d1a5e0':
    friendly_name: 'Zigbee Light'
    retain: true
```

## Contributing

Contributions are welcome! If you want to add new features or improve existing ones, feel free to fork the repository and submit a pull request. Please follow the contribution guidelines outlined in the `CONTRIBUTING.md` file.

## License

This project is licensed under the MIT License. See the `LICENSE` file for more details.

## Contact

For questions or feedback, please reach out via GitHub or contact me directly at my email. Your input is valuable, and I appreciate your interest in my Home Assistant configurations.

[![Download Releases](https://img.shields.io/badge/Download%20Releases-blue.svg)](https://github.com/YHONCARLOSCHOQUEHUANCA/Home-Assistant/releases)

Thank you for visiting my repository! I hope you find my Home Assistant configurations helpful for your smart home setup.