---
title: "TL;DR - Advanced Joystick Configs for Star Citizen "
date: "2022-07-21"
author: "ventorvar"
cover: "https://cdn.discordapp.com/attachments/652921814321725454/652994492961652747/joystick-sc-tldr-cover.jpg"
toc: true
tags:
  - Star Citizen
  - Joystick Gremlin
  - HOTAS
  - HOSAS
description: >
  TL;DR - just get your running as fast as possible with advanced joystick controls for Star Citizen.
---

# Star Citizen Advanced Controls Configuration

These configurations are based off my personal setup for **Star Citizen** and are outlined in a
two part guide on this site. That being said there are a few requirements, and you can use my
configurations as a starting point whether or not you have the same joystick setup.

> **Note:** This was last updated for Star Citizen 3.17.2-PTU.8143480 and may or may not work with the current build

## Requirements

- vJoy, Joystick Gremlin and HidHide must be installed and setup correctly. Check out 
  [part 1]({{< ref "/posts/joystick-intro.md" >}}) of the full guide for information
- Understanding of how Joystick Gremlin works and how to use the advanced controls configurations in Star Citizen,
  otherwise I'd recommend just following the [second part]({{< ref "/posts/joystick-config.md" >}}) to really become 
  familiar
  
# Configurations

- **Diagram of the key layout:** [here](https://drive.google.com/file/d/1UM4qPccTYAkluSx1fLwBGfNH6mXuxYqS/view?usp=sharing)
- **SC Control Mapping:** [layout_Ventorvar_HOSAS_3_17_2_exported.xml](https://cdn.discordapp.com/attachments/652921814321725454/999775811257258024/layout_Ventorvar_HOSAS_3_17_2_exported.xml)
- **Dual Thrustmaster Joystick Gremlin Profile:** [Ventorvar_SC_HOSAS_3.17.2.xml](https://cdn.discordapp.com/attachments/652921814321725454/999775811513102516/Ventorvar_SC_HOSAS_3.17.2.xml)

## Loading the SC Control Mapping

- Place the control mapping into the ```RSI\StarCitizen\LIVE\USER\Client\0\Controls\Mappings``` folder
- Launch Star Citizen
- In **Options > KEYBINDINGS > ADVANCED CONTROLS CUSTOMIZATION** menu, use the right arrow in the
- Click the button on the right that says **> CONTROL PROFILES**
- Scroll down and choose the new control mapping
- For each **Joystick** listed on the left side, choose the button next to it that says **None** and change it to **JoyStick**

## Importing Joystick Gremlin Profile

Importing the Joystick Gremlin profile can be a bit tricky, until someone writes a plugin to handle the import, 
this is my recommended method.

- Start **Joystick Gremlin**
- Press buttons to determine which joystick is which, and give each device an appropriate **Device Label**
- Use **Save Profile As** to save the empty profile, call it something like ```GUIDs```
- Go to your JG folder (```C:\Users\{username}\joystick gremlin```) and copy the downloaded profile from above into this 
  folder next to the ```GUIDs.xml```
- Open ```GUIDs.xml``` and the new profile in a text editor (like notepad++)
- In the ```GUIDs.xml``` file you will find a `<device` listing for each of your devices that also shows it's 
  `device-guid` and `label`
- Using this information, copy the `device-guid`s from `GUIDs.xml` into the downloaded profile using the label to match
  up the correct device, and save the profile
- Back in **Joystick Gremlin** choose **File > Load Profile** and choose the newly updated downloaded profile
- Press keys on each device to double check that the profiles loaded correctly

> **Need Help? Have an issue/comment?** Feel free to join my Discord: https://discord.gg/CVBMxJq
