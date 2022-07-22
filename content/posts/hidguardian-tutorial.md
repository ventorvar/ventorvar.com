---
title: "HidGuardian Setup Guide"
date: "2020-09-24"
author: "ventorvar"
toc: false
tags:
  - HOTAS
  - HOSAS
description: >
    Installing and using the HidGuardian Windows Joystick filter.
---

If you're playing a game that doesn't work with devreorder, HidGuardian is
another options to filter your inputs.

## Setting up HidGuardian

> **Note:** If HidGuardian does not work well on your system, there is a
> work around for Star Citizen at least. SC will only see devices that are
> present when it is launched. Therefore, you can launch SC, then attach your
> devices. You'll still have to make sure they are loaded correctly in JG, 
> however

The _easiest_ way to install **HidGuardian** is to use [WhiteKnight](https://www.autohotkey.com/boards/viewtopic.php?t=34890) 
utility. You don't need to follow the directions, just download the tool and follow these:

- Extract **WhiteKnight**
- Run **AutoWhitelister.exe**
- Click **Install** next to **HidGuardian Install state:  Not Installed**
- Close **WhiteKnight**

{{< image src="https://cdn.discordapp.com/attachments/526695875011936279/534163838862491658/whiteknight_install.png" >}}

> **Note:**
> If you'd rather install this manually, you can follow the instructions on vigem's forums 
> [here](https://forums.vigem.org/topic/271/hidguardian-v1-driver-installation)

## Joystick Gremlin Setup

- https://whitemagic.github.io/JoystickGremlin/download/
- Launch **Joystick Gremlin** in admin mode
- Under the **Tools** menu, click **Options**
  - Select the **HidGuardian** Tab
    - Check boxes for each device type you want to use. For my setup, I have a
    box for **T.16000M** and a box for **TWCS Throttle**
- Unplug all of your devices
- Plug your devices back in

{{< image src="https://cdn.discordapp.com/attachments/526695875011936279/534164216224022542/jg_hidguardian.PNG" >}}

Because we're using **HidGuardian**, **Joystick Gremlin** must always be run as an
administrator. To make this easier, we can modify the shortcut so that it will
always start that way.

- Open Start and find **Joystick Gremlin**
- Right-click the shortcut and select **Properties**
- Select the **Compatibility** tab
- Check the box for **Run this program as an administrator**
- Click **Apply** and **OK**

> **Note:** If you ever run **Joystick Gremlin** and down see your joysticks,
> double check that you're running it as an administrator.

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
