# Godot for Devcade

Some doucmentation for using the [Godot Engine](https://godotengine.org/) with Devcade.

- Input
- Exporting

## Inputs

Godot's built-in [input](https://docs.godotengine.org/en/stable/classes/class_inputevent.html) handler is able to pick up all of Devcade's button inputs. Below is a list of the documented. Godot reads the left and right pads as two different controllers.

```
Left Pad Device ID: 0
Right Pad Device ID: 1

Enum JoyButton:

JOY_BUTTON_A = 0 # Bottom Left Most Blue Button
JOY_BUTTON_B = 1 # Bottom Left Second Most Blue Button
JOY_BUTTON_X = 2 # Top Left Red Button
JOY_BUTTON_Y = 3 # Top Blue Button
JOY_BUTTON_BACK = 4 # Top Right White Button
JOY_BUTTON_GUIDE = 5 # Top Green Button
JOY_BUTTON_LEFT_STICK = 7 # Black Center Button

Enum JoyAxis:

JOY_AXIS_LEFT_X = 0 # Joystick Left & Right
JOY_AXIS_LEFT_Y = 1 # Joystick Up & Down
JOY_AXIS_RIGHT_X = 2 # Bottom Right Most Blue Button
JOY_AXIS_TRIGGER_RIGHT = 5 # Bottom Right Second Most Blue Button

```

## Exporting

Some general advice to follow when developing and uploading a game to Devcade.

- **Ensure that there is a way to exit you game!** ssh-ing in to close a game is not fun.
  - The convention is to close your game after both center buttons are pressed.
- Keep in mind that Devcade has a 1080x2560px (9x21 ratio) display and a refresh rate of 75 Hz
- Export you game for Linux x86_64 and remove the file extension such that it looks like this: `[your game's name]`.
- With Godot, consider packing the [.pck](https://docs.godotengine.org/en/stable/tutorials/export/exporting_pcks.html) file into the executable.
  - Its currently unknown whether not packing the .pck file has any effect, so if you don't pack the file proceed at your own risk.
- Ensure that you game file is zipped with [7Zip](https://www.7-zip.org/) in a folder called `publish`.
- The title of your executable should be the **exact same** as the name you give your game when uploading. This is currently critical to the execution of your game.

This page was last updated 10/2/2023