---
title: "Intro to Advanced Joystick Configs - Part 1"
date: "2022-07-21"
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

> **Just need the configs?** For SC head to [TL;DR]({{< ref "/posts/joystick-sc-tldr.md" >}})

> **A note on the update:** If you followed the previous version of this guide, you no longer need HidGuardian! Also
> Joystick Gremlin no longer needs to run as an administrator.

# The Problem We're Trying to Solve

Using multiple joysticks on Windows can be a huge pain. There is no guarantee of
the input device order when your machine reboots or when they're plugged, even
if you follow the same order every time. This is compounded for Star Citizen
where you're asked to remove the **USER** folder each time there is an update,
and the configuration interface has a long way to go before it's not a pain to
use.

In addition to the difficulties that arise with Windows, each game allows for
varying levels of controller input configuration that might suite our
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
[Thrustmaster T16000M](https://amzn.com/B01MQEDEEW), as well as two
[VKB Gladiator Ks](https://vkbcontrollers.com/?product=scg-space-combat-grip-kosmosima-stand-alone) giving me:

- Throttle
- Pedals
- Left Joystick (T16K or VKB Gladiator K LH)
- Right Joystick (T16K or VKB Gladiator K RH)

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
- Joystick Gremlin
- HidHide

vJoy is a virtual joystick device for windows that is going to allow the inputs
from all of our separate physical devices to be mapped to a single virtual
device. This makes the configuration in-game much easier and consistent since we
don't have to worry about our device IDs on windows changing every time we
reconnect them.

Just because we're mapping the inputs from our physical devices to vJoy doesn't
mean that games don't stop seeing the original inputs too. This means that
you'll have a difficult time guaranteeing that you can get the game to
only use the vJoy inputs, rather than the device inputs. To solve that issue,
we're going to use a tool called [HidHide](https://github.com/ViGEm/HidHide)
which acts as a sort of firewall, only allowing configured applications to see
specific devices.

## Install vJoy

Installing vJoy is a more straight forward matter:

- Install the latest [vJoy](https://github.com/shauleiz/vJoy) release. Use the
  [jshafer817](https://github.com/jshafer817/vJoy/releases) fork if you're running the latest version of Windows 10
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
> correctly ordering them. So make sure you configure devreorder to preserve the order of the multiple vJoy devices.

## Install HidHide

Find the latest release from https://github.com/ViGEm/HidHide/releases and reboot your computer after installation.

## Install Joystick Gremlin

Simply download and install the latest MSI version from: https://whitemagic.github.io/JoystickGremlin/download/

## Configure HidHide

Now that Joystick Gremlin is installed, we need to configure HidHide to allow JG to see the devices, and hide them from
everything else. To do this launch the `HidHide Configuration Client` from the start menu.

- On the `Applications` tab, click the `+` button and browse to the `Joystick Gremlin` exe (by default this
  is `C:\Program Files (x86)\H2ik\Joystick Gremlin\joystick_gremlin.exe`)

{{< image src="https://cdn.discordapp.com/attachments/652921814321725454/999709699517718608/unknown.png" >}}
 
- On the `Devices` tab, ensure the checkboxes next toy our devices are `checked` and the checkbox for the vJoy devices are `not checked`. Also ensure the `Enable device hiding` checkbox at the bottom is `checked`. If you ever need to disable hiding, you can simply uncheck this box.

{{< image src="https://cdn.discordapp.com/attachments/652921814321725454/999710656129405168/unknown.png" >}}

# Verify Setup

At this point, **Joystick Gremlin** should have a tab for each of your devices in
its main window, as well as a **Keyboard**, **vJoy Device #1** and **Settings**
tabs.

{{< image src="https://cdn.discordapp.com/attachments/526695875011936279/534169767406469150/jg_verify.PNG" >}}

# Configuration Guide

Now the groundwork is all done. We'll continue the guide in [part 2]({{< ref "/posts/joystick-config.md" >}}).

> **Need Help? Have an issue/comment?** Feel free to join my Discord: https://discord.gg/CVBMxJq
