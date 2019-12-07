---
title: "Intro to Advanced Joystick Configs - Part 2"
date: "2019-12-06"
author: "ventorvar"
cover: "https://cdn.discordapp.com/attachments/526695875011936279/534175949562839050/joystick-config-cover.jpg"
toc: true
tags:
  - Star Citizen
  - Joystick Gremlin
  - HOTAS
  - HOSAS
description: >
  Getting the most out of multiple HID inputs for Star Citizen, part 2. After
  preparing our system, we'll talk about the configuration methodology, and
  walk through setting our devices from the ground up.
---

> **Note:** This is part 2 of a series. If you haven't already installed all
> the required tools, go check out [part 1]({{< ref "/posts/joystick-intro.md" >}}) first.

> **Just need the configs?** go the to [TL;DR]({{< ref "/posts/joystick-sc-tldr.md" >}}) 

# Getting familiar with Joystick Gremlin

The keystone to our entire setup is [Joystick Gremlin](https://whitemagic.github.io/JoystickGremlin/) 
(JG). JG allows you to remap inputs from your devices to other inputs on your system. For example, you can
configure it so with you press the trigger button on your left joystick, it
presses the **Shift** key on your keyboard. This opens an entire array of
possibilities that we'll only begin to touch on.

{{< image src="https://cdn.discordapp.com/attachments/526695875011936279/534222975533056011/joy-config-diagram.png" link="true">}}

In this guide, we'll be configuring a profile for a single game, Star Citizen.
Also, we'll be basing this guide on two Thrustmaster T16000M joysticks and
TWCS Throttle, but the concepts being discussed here apply to any game and any
input device.

# Philosophy

When configuring input devices, I prefer to keep the game as close to a
default configuration as possible. This means if I uninstall/reinstall, or
move between machines, I just have to have my JG profiles, and I don't have to
worry about re-configuring within the game more than I have to.

This means that I also prefer to rebind physical joystick buttons to
emit keyboard commands for the default key bindings rather than configure
joystick buttons within the game.

## Planning it out

Before we start configuring JG and Star Citizen, it's good to come up with a
plan. One of the easiest ways I've found is to use Drawings in Google Docs.

{{< image src="https://cdn.discordapp.com/attachments/652921814321725454/652995104109494274/joystick_drawing.jpg" link="true">}}

You can copy mine from [here](https://docs.google.com/drawings/d/14IJUqXRCJyYPlzwZPWcJVJUpznWHdLOK20iptyyzc4g/). 
I label the physical input with the in-game action on top, and the keyboard or joystick input on
the bottom. As you can see, most of my inputs map to keyboard commands, with only a few joystick buttons 
(J1, J2, J3, etc). It's also useful to have a the [in-game keyboard map](https://cdn.discordapp.com/attachments/652921814321725454/652922995341393950/SC3_7_2_KeyMappings_v1.pdf)[^2]
handy when creating this.

# Joystick Gremlin Configuration

## Identifying Devices

First, we're going to configure the two joysticks. There is a small controller
icon under the menu bar that can be black or green. This is the **Activate**
button. When activated, the button will be green and will process all inputs
as configured. To work on our configuration, though, we're going to deactivate
JG, making sure the button is black.

{{< image src="https://cdn.discordapp.com/attachments/526695875011936279/534227285910224896/jg_activate_button.PNG" link="true">}}

In JG we have two tabs for our joysticks. The way to tell them apart is select
of the tabs, then move the left and right joysticks one at a time. When moving
or pressing buttons, JG will select the physical input on the left side that
corresponds with the input you're creating on your joystick. When you've
determined which joystick is which, use the **Device Label** field under the
tabs as a reminder.

## Mapping Axes

One of the more complex mappings are the axes. We'll be mapping the roll, pitch
and yaw axes from our left and right joysticks onto a single vJoy device. We'll
be using this standardized frame reference[^1].

[{{< image src="https://upload.wikimedia.org/wikipedia/commons/b/b1/RPY_angles_of_spaceships_%28local_frame%29.png" >}}](https://en.wikipedia.org/wiki/Axes_conventions#/media/File:RPY_angles_of_spaceships_(local_frame).png)

On your right joystick:

- Move the stick to determine the **pitch** (front to back) physical input
  (it will be Axis 2)
- Enter "Pitch" into the **Action Description** box
- Select **Remap** from the **action** (left) dropdown, and click **Add**
- In the new **Remap** action form, choose **vJoy Device 1**, **Axis Y**

Repeat these steps for **roll** (side to side) to the **X** axis and **yaw**
(twist) to the **Z** axis

{{< image src="https://cdn.discordapp.com/attachments/526695875011936279/534239533080772608/jg_axes_map.PNG" link="true">}}

On your left joystick we'll be configuring strafe forward/back, left/right and
up/down. Follow the same steps from above, except on your left joystick and
mapping:

- Forward/Back -> **vJoy Device 1**, **Axis X Rotation**
- Left/Right -> **vJoy Device 1**, **Axis Y Rotation**
- Up/Down -> **vJoy Device 1**, **Axis Z Rotation**

### Testing it out

To test our configuration, open the **Monitor vJoy** application. Ensure to
**activate** JG by clicking the **activate** button which turns it green. Now
when you move your left and right joysticks, you should see the corresponding
axis move in the vJoy monitor.

### Inverting axes

If we loaded this up right now and tried it out in Star Citizen we'd find that
the strafe Forward/Back and Up/Down would be reversed. Rather than fixing this
in game, we can fix it in JG by inverting the curve. To do that:

- Select the **Strafe Forward/Back** action
- Within the **Remap** action that has already been configured, select
  **Responsive Curve** from the action dropdown and click **Add**
- Click the **invert** button in the **Response Curve** action form

Repeat the steps for the **Strafe Up/Down** input

{{< image src="https://cdn.discordapp.com/attachments/526695875011936279/534243371959713792/jg_response_curve.PNG" link="true">}}

### Doubling up inputs

I want to be able to strafe in all directions from my throttle as well. To do
this I just had to bind the axes on the throttle to the same axes that I bound
my left controller to. Since the game will be configured just to use the
rotational axes, it doesn't matter which physical input is the one manipulating
the virtual interface. This is how I'm able to control the same functions from
multiple devices at once.

## Mapping Hats

In order to use the hats like other buttons, you need to configure them first.

- Select the **Hat 1** on the right stick
- Select **Hat Buttons** from the **containers** dropdown (to the right of the
  actions dropdown) and click **Add**

{{< image src="https://cdn.discordapp.com/attachments/526695875011936279/534250224923967489/jg_hats.PNG" link="true">}}

You can now treat the individual directions of the hat as buttons using the
following instructions.


## Mapping Buttons

Joystick buttons can be mapped in two different ways (for our use case). If
we're mapping a physical button to a vJoy button (for instance the trigger on
the right stick), this would use the **remap** action.

- Find the right trigger physical input but clicking **Button 1** on the left,
  or by physically pressing the trigger button while the **Right** joystick
  tab is selected
- Select the **Remap** action and click **Add**
- Configure the **Remap** form to **vJoy Device 1** and **Button 1**

If we're mapping a physical input to a keyboard command, then we use the **map
to keyboard** action.

- Find the **Gimbal Lock** button on the left joystick by physically pressing
  the bottom right-most button on the right side buttong group while the **Left** joystick tab is selected (Button 10)
- Select the **Map to Keyboard** action and click **Add**
- Press the **Record keys** button in the **Map to Keyboard** form
- Press **Left Alt + R** on your keyboard and release

{{< image src="https://cdn.discordapp.com/attachments/526695875011936279/534246929622892555/jg_gimbal_lock.PNG" link="true">}}

Continue this process for every physical button you'd like to configure. For
Star Citizen (3.4), you can use [this](https://imgur.com/a/v4eofhx) as a good
reference. However, key bindings change frequently and I'd advise you try to
find a current version of the advanced key bindings.

# Configuring Star Citizen

At this point, you should have every physical button that you want to configure
either **remap**'d to the vJoy device, or to a keyboard press. Now we'll go into
Star Citizen and do some final configurations.

Ensure that JG is in the **active** state. The **Activate** button should be
green and the **Status** at the bottom left of the window should be
**Running and Active**.

## Resetting to SC defaults

First, we'll reset the Star Citizen configuration.

- Delete your **USER** folder (within your RSI installation folder ```RSI\StarCitizen\LIVE\USER```)
- Launch Star Citizen

> **Note:** It is my preference to unbind the mouse from pitch/yaw which allows
> you to look around with the mouse without worrying about the ship moving. To
> do this, after you've reset the controls, in **Options > KEYBINDINGS > ADVANCED CONTROLS CUZTOMIZATION** 
> make sure you're on the **Keyboard / Mouse** configuration in the bottom right, then expand **Flight -
> Movement** and clear **Pitch** and **Yaw** by selecting the item with a left click, then right-clicking on the item

Now all of the keyboard mappings we've created in JG should match up to their
in-game equivalents.

## Configuring Joystick Inputs

Still in the **ADVANCED CONTROLS CUSTOMIZATION** UI, use the right arrow in the
bottom right button that currently says **Keyboard / Mouse** to select
**Joystick / HOTAS**. None of the built-in control profiles match our purpose,
so we're going to completely clear the joystick configuration, and configure
the vJoy inputs that we've configured. There are also a few things that don't
have a keyboard command configured by default, so we've set them to a joystick
button.

- Click the button on the right that says **> CONTROL PROFILES**
- Scroll down and choose **Clear All Device Bindings**
- For each **Joystick** listed on the left side, choose the button next to it that says **None** and change it to **JoyStick** 

Now that the controls are cleared, we must assign certain bindings using the following table. Do this by clicking on 
the item twice, then moving the joystick in the desired axis, or pressing the intended button. Use your joystick 
configuration map for a reference.

> **Note:** You will get a message that things have already been bound and if that's ok. Always press yes.

| Group                     | Action                                 | Binding         |
| ------------------------- | -------------------------------------- | --------------- |
| Flight - View             | Look left / right                      | Z-Axis          |
|                           | Look up / down                         | Y-Axis          |
|                           | Look Behind                            | Button 19       |
| Flight - Movement         | Pitch                                  | Y-Axis          |
|                           | Yaw                                    | Z-Axis          |
|                           | Roll                                   | X-Axis          |
|                           | Speed Limiter (Abs.)                   | Slider 1        |
|                           | Acceleration Limiter (Abs.)            | Slider 2 (Dial) |
|                           | Strafe up / down                       | Z-Axis Rotation |
|                           | Strafe left / right                    | Y-Axis Rotation |
|                           | Throttle forward / back                | X-Axis Rotation |
|                           | G-force safety (Toggle)                | Button 30       |
| Flight - Targeting        | Aim left / right                       | X-Axis          |
|                           | Aim up / down                          | Y-Axis          |
|                           | Scanning Radar Ping                    | Button 1        |
|                           | Scanning Increase Radar Angle          | Button 3        |
|                           | Scanning Decrease Radar Angle          | Button 2        |
| Mining                    | Fire Mining Laster (Toggle)            | Button 1        |
|                           | Switch Mining Laser (Toggle)           | Button 2        |
|                           | Increase / Decrease Mining Laser Power | Slider 2        |
| Flight - Turrets          | Aim left / right                       | X-Axis          |
|                           | Aim up / down                          | Y-Axis          |
| Flight - Weapons          | Fire Weapon Group 1                    | Button 1        |
|                           | Fire Weapon Group 2                    | Button 3        |
|                           | Acquire missile lock                   | Button 2        |
|                           | Launch missile                         | Button 2        |
| Ground Vehicle - General  | Look left / right                      | X-Axis          |
|                           | Look up / down                         | Y-Axis          |
|                           | Look behind                            | Button 19       |
|                           | Fire Weapon Group 1                    | Button 1        |
|                           | Fire Weapon Group 2                    | Button 3        |
| Ground Vehicle - Movement | Drive Forward / Backward               | Y-Axis          |
|                           | Turn Left / Right                      | Z-Axis          |
|                           | Primary Fire                           | Button 1        |
|                           | Secondary Fire                         | Button 3        |
| Ground Vehicle - Gunner   | Primary Fire                           | Button 1        |
|                           | Secondary Fire                         | Button 3        |
| Social - General          | Re-spawn                               | Button 1        |

## Saving the Configuration for Later Use

In Star Citizen, you can save your current configuration as a control profile to
reload later. At the main menu:

- Choose **OPTIONS**, then the **KEYBINDINGS** tab and click **ADVANCED
  CONTROLS CUSTOMIZATION**
- Click the button on the right that says **> CONTROL PROFILES**
- Click 'Save Control Settings'
- Enter a name for your control setup, and click **Save**
- Copy the control settings profile from the
  ```RSI\StarCitizen\LIVE\USER\Controls\Mappings``` folder.

Whenever you need to delete your **USER** folder, simply copy the
**layout_*_exported.yml** back into the ```USER\Controls\Mappings``` folder and
use the **CONTROL PROFILES** button in Star Citizen like you did to load the
advanced keyboard controls above.

# Next Steps

## Advanced Axis Curves

In my configuration, I use a custome response curve for the **Speed Limiter** axis (Z-Axis on the Throttle 
mapped to Slider) so that I can have more precise control over the lower 1/8th of the limiter region. This is done the
same way we inverted the axes above, except we configure it at as **Cubic Bezier Spline** curve and use the control 
points to adjust the response curve to our liking. This is very much personal preference, but you can see what I've
done for the speed limiter as a reference. (You'll note that this is also inverted, which is the way SC requires it)

{{< image src="https://cdn.discordapp.com/attachments/652921814321725454/652990562554740756/JG_Speed_Limit_Curve.PNG" link="true">}}

## Future Thoughts

Now that we've got our base JG profiles configured and can play the game, we
can start tweaking the configuration for specific situations in the game. In a 
future guide we'll cover creating custom modes for mining, a director mode and a
precision mode for dogfighting that will give us better accuracy while firing weapons.

[^1]: https://en.wikipedia.org/wiki/Axes_conventions#Frames_for_space_navigation
[^2]: https://www.reddit.com/r/starcitizen/comments/e0zrde/sc_372_keyboard_mouse_gamepad_and_joystick/


> **Need Help? Have an issue/comment?** Feel free to join my Discord: https://discord.gg/CVBMxJq