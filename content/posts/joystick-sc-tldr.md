---
title: "TL;DR - Advanced Joystick Configs for Star Citizen "
date: "2019-12-07"
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
configurations as a starting point whether or not you have the same joystick setup. Below I've provided 

> **Note:** This was last updated for Star Citzen 3.7.2-LIVE.3658647 and may or may not work with the current build

## Requirements

- vJoy, Joystick Gremlin and HIDGuardian must be installed and setup correctly. Check out 
  [part 1]({{< ref "/posts/joystick-intro.md" >}}) of the full guide for information
- Understanding of how Joystick Gremlin works and how to use the advanced controls configurations in Star Citizen,
  otherwise I'd recommend just following the [second part]({{< ref "/posts/joystick-config.md" >}}) to really become 
  familiar
  
# Configurations

- **Google Drawing of key layout:** [here](https://docs.google.com/drawings/d/14IJUqXRCJyYPlzwZPWcJVJUpznWHdLOK20iptyyzc4g/)
- **SC Control Mapping w/o GameGlass:** [layout_Ventorvar_HOSASAT_37_exported.xml](https://cdn.discordapp.com/attachments/652921814321725454/652990605139640320/layout_Ventorvar_HOSASAT_37_exported.xml)
- **SC Control Mapping with GameGlass:** [layout_Ventorvar_HOSASAT_37_GG_exported.xml](https://cdn.discordapp.com/attachments/652921814321725454/652990607085797386/layout_Ventorvar_HOSASAT_37_GG_exported.xml)
- **Joystick Gremlin Profile:** [Ventorvar_SC_37_HOSASAT.xml](https://cdn.discordapp.com/attachments/652921814321725454/652990603302404106/Ventorvar_SC_HOSASAT_37.xml)

## Importing Joystick Gremlin Profile

Importing the Joystick Gremlin profile can be a bit tricky, until I write a plugin to handle the import, this is my recommended method.

- Start **Joystick Gremlin**
- Press buttons to determine which joystick is which, and give each device an appropriate **Device Label**
- Use **Save Profile As** to save the empty profile, call it something like ```GUIDs```
- Go to your JG folder (```C:\Users\username\joystick gremlin```) and copy the downloaded profile from above into this 
  folder next to the ```GUIDs.xml```
- Open ```GUIDs.xml``` and the new profile in a text editor (like notepad++)
- In the ```GUIDs.xml``` file you will find a `<device` listing for each of your devices that also shows it's 
  `device-guid` and `label`
- Using this information, copy the `device-guid`s from `GUIDs.xml` into the downloaded profile using the label to match
  up the correct device, and save the profile
- Back in **Joystick Gremlin** choose **File > Load Profile** and choose the newly updated downloaded profile
- Press keys on each device to double check that the profiles loaded correctly

> **Need Help? Have an issue/comment?** Feel free to join my Discord: https://discord.gg/CVBMxJq
