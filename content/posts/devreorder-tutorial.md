---
title: "devreorder Setup Guide"
date: "2022-07-19"
author: "ventorvar"
toc: false
tags:
  - HOTAS
  - HOSAS
description: >
    Installing and using the devreorder Windows Joystick filter.
---

> Note: This was a previous method for controlling how games see your input devices. This is no longer used in the 
> primary guide but is kept here for reference.

dinput8 DLL wrapper called [devreorder](https://github.com/briankendall/devreorder) 

## Setting up devreorder

> **Note:** If devreorder doesn't work with your game, [HidGuardian]({{< ref "/posts/hidguardian-tutorial.md" >}}) is
> another option to hide inputs from your game

- Download the latest release [here](https://github.com/briankendall/devreorder/releases) (the zip file)
- Unzip `x64/dinput8.dll` to your Star Citizen `LIVE\Bin64` folder next to `StarCitizen.exe`
- Unzip `devreorder.ini` to your Star Citzen `LIVE` folder (where `Data.p4k` is)

### Configure devreorder

- Use the `DeviceLister` tool in the `devreorder` release zip to list active joystick devices.

{{< image src="https://cdn.discordapp.com/attachments/652921814321725454/759469426235015188/unknown.png" >}}

- Edit `devreorder.ini` in our SC `LIVE` folder, and copy the `vJoy Device` GUID (including the brackets, e.g.
  `{a3c2c570-0f81-11ea-800a-444553540000}`) to the `[visible]` section. In my case, I have two vJoy devices I'm playing
  with, so my config (without comments) will look like this:

```
[order]
{5dfaa060-0f83-11ea-8003-444553540000}
{a3c2c570-0f81-11ea-800a-444553540000}

[visible]
{5dfaa060-0f83-11ea-8003-444553540000}
{a3c2c570-0f81-11ea-800a-444553540000}
```

> **Note:** I'm also using the `[order]` section since I have two vJoy devices that I want the game to see. This way
> they will always show up to the game in the same order.

To test that devreorder is working, launch Star Citizen and look at the console ouput (or `LIVE\Game.log`) and look for
the line `Input initialization`. If things are working, you should only see your `visible` devices, like so:

```
<2020-09-24T17:51:34.892Z> Input initialization
<2020-09-24T17:51:35.223Z> - Connected joystick0: vJoy Device {BEAD1234-0000-0000-0000-504944564944}
<2020-09-24T17:51:35.318Z> - Connected joystick1: vJoy Device {BEAD1234-0000-0000-0000-504944564944}
```

# Verify Setup

At this point, **Joystick Gremlin** should have a tab for each of your devices in
its main window, as well as a **Keyboard**, **vJoy Device #1** and **Settings**
tabs.

{{< image src="https://cdn.discordapp.com/attachments/526695875011936279/534169767406469150/jg_verify.PNG" >}}

Launch the **Set up USB Game Controllers** tool from the Start menu, and you
should see **vJoy Device**, and none of your joysticks you configured in
**HidGuardian** tab in **Joystick Gremlin**.

{{< image src="https://cdn.discordapp.com/attachments/526695875011936279/534164342992797696/game_controllers.PNG" >}}

> **Need Help? Have an issue/comment?** Feel free to join my Discord: https://discord.gg/CVBMxJq
