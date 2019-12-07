---
title: "Intro to Advanced Joystick Configs - Part 1"
date: "2019-12-06"
author: "ventorvar"
cover: "https://cdn.discordapp.com/attachments/526695875011936279/534173708302942220/joystick-intro-cover.jpg"
toc: true
tags:
  - Star Citizen
  - Joystick Gremlin
  - HOTAS
  - HOSAS
description: >
  Getting the most out of multiple HID inputs for Star Citizen, part 1. We'll
  take a look at the why and how of configuring multiple joysticks on Windows,
  as well as the walk through how to setup and install the pre-requisite
  software.
---

> **Just need the configs?** go the to [TL;DR]({{< ref "/posts/joystick-sc-tldr.md" >}}) 

# The Problem We're Trying to Solve

Using multiple joysticks on Windows can be a huge pain. There is no guarantee of
the input device order when your machine reboots or when they're plugged, even
if you follow the same order every time. This is compounded for Star Citizen
where you're asked to remove the **USER** folder each time there is an update,
and the configuration interface has a long way to go before it's not a pain to
use.

In addition to the difficulties that arise with Windows, each game allows for
varying levels of controller input configuration that might night suite our
needs. In Star Citizen's case, it doesn't allow binding multiple inputs to the
same action, for example, if I wanted to have a **Ship Lights** toggle on my
throttle as well as my joystick.

Luckily, there has been a lot of effort into creating configuration tools that
exist outside of games to fine tune your setup, and setup configurations that
might not even be possible within the game itself.

# Our Configuration

The goal of this guide is to help you get some base configurations and tools
installed, and give you enough understanding of the components to tweak and
build your own configurations. I'll be supplying my configurations as a quick
starting off point though.

My setup consists the [Thrustmaster T16000M FCS Flight Pack](https://amzn.com/B01N2PE8CZ) with an additional 
[Thrustmaster T16000M](https://amzn.com/B01MQEDEEW) giving me:

- Throttle
- Pedals
- Left Joystick
- Right Joystick

{{< image src="https://images-na.ssl-images-amazon.com/images/I/91so7Q7rm6L._SL1500_.jpg" >}}

In Star Citizen, I like to use a HOTAS (Hand On Stick And Throttle) setup while
cruising, and a HOSAS (Hand On Stick and Stick) while dogfighting, or when I
need more fine control over my movements.

{{< image src="https://m.media-amazon.com/images/S/aplus-media/vc/67684a48-d57f-4fc4-9d61-6032c5d6c7bd.jpg" >}}

One of the first issues we run into with a configuration like this is that
Star Citizen doesn't allow you to bind multiple inputs to the same action. For
example, I want to be able to strafe forward/back/left/right using the left
joystick **as well** as the mini-stick on the front of the throttle. By setting
up everything outside of the game, we can create configurations like this quite
easily.

# Prerequisites

To get started, we need to install a few tools and drivers. We'll only need to
do these steps once. We'll be using three tools for our setup.

- vJoy
- HidGuardian
- Joystick Gremlin

vJoy is a virtual joystick device for windows that is going to allow the inputs
from all of our separate physical devices to be mapped to a single virtual
device. This makes the configuration in-game much easier and consistent since we
don't have to worry about our device IDs on windows changing every time we
reconnect them.

Just because we're mapping the inputs from our physical devices to vJoy doesn't
mean that games don't stop seeing the original inputs too. This means that
you'll have a difficult time guaranteeing that you can get the game to
only use the vJoy inputs, rather than the device inputs. To solve that issue,
we're going to use a Windows filter driver called [HidGuardian](https://github.com/ViGEm/HidGuardian) 
which acts as a sort of firewall, only allowing configured applications to see specific devices.


## Install HidGuardian

> **Note:** If HidGuardian does not work well on your system, there is a
> work around for Star Citizen at least. SC will only see devices that are
> present when it is launched. Therefore you can launch SC, then attach your
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


## Install vJoy

Installing vJoy is a more straight forward matter:

- Install the latest [vJoy](https://github.com/shauleiz/vJoy) release. Use the [jshafer817](https://github.com/jshafer817/vJoy/releases) branch if you're running the latest version of Windows 10
- Run **Configure vJoy** from the Start menu
  - Make sure the **Enable vJoy** box is checked at the bottom left of the window
  - vJoy Device 1
    - Ensure all of the **Axes** boxes are checked
    - Set **Number of Buttons** to 64
    - Set **POV Hat Switch** to Continuous, and select **4** for **POVs**
    - All options in **Force Feedback** should be unchecked
    - Click Apply

{{< image src="https://cdn.discordapp.com/attachments/526695875011936279/534164019246792705/vjoy_config.PNG" >}}

> **Note:** While you can definitely setup multiple vJoy devices, you could run into the same problem of your game not
> correctly ordering them, so beware.

## Install Joystick Gremlin

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

# Configuration Guide

Now that the groundwork is all done. We'll continue the guide in [part 2]({{< ref "/posts/joystick-config.md" >}}).

> **Need Help? Have an issue/comment?** Feel free to join my Discord: https://discord.gg/CVBMxJq
