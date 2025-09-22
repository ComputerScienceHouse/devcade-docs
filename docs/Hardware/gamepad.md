# Gamepad

The control panel on Devcade has two sets of controls for Player 1 and Player 2.

Each set of the controls contains an 8 Directional Analog Joystick (N,S,E,W, Diagonals). The joystick accepts input in Binary for each direction.

In addition, each player has 2 rows of 4 arcade buttons. Labeled A1-A4, and B1-B4 for the top and bottom rows respectively.

Each button on the Top row has a different color and is the same for both players, whereas the bottom row is one color and different for the players.

Lastly, there is one menu button for each player, positioned such that the two menu buttons are next to each other in the center of the control panel.

### Button Names to Color Mapping

##### Top Row

The top row of buttons for both players follow the following color scheme:

A1 - Red <br>
A2 - Blue <br>
A3 - Green <br>
A4 - White <br>

##### Bottom Row

For the bottom row of buttons, all 4 of them are purple for Player 1, and all of them are yellow for Player 2. The joystick for each player also has a ball top of the same color as the bottom row of buttons for that player.

### Control Panel Diagram

```
            Player 1                   Player 2

    ^     A1 A2 A3 A4                 ^     A1 A2 A3 A4
 <Stick>               Menu  Menu  <Stick>
    v     B1 B2 B3 B4                 v     B1 B2 B3 B4
```

### Control Panel Wiring
The control panel is wired to a Pi-Pico through GPIO, where it emulates the inputs to an Xbox controller, and sends it over to the Computer.

The Pi-Pico runs the following program written in Rust to emulate the input to an Xbox Controller: https://github.com/Mstrodl/devcade-controller/.

#### GPIO Pin Map
##### Player1:
- A1-A4: {13, 12, 11, 10}
- B1-B4: {17, 16, 15, 14}
- N,E,S,W: {27, 22, 28, 26}
- Menu: 9

##### Player2:
- A1-A4: {6, 7, 2, 3}
- B1-B4: {4, 5, 0, 1}
- N,E,S,W: {20, 18, 21, 19}
- Menu: 8

#### Xbox Controller Mapping
- A1 = Buttons.X
- A2 = Buttons.Y
- A3 = Buttons.RightShoulder
- A4 = Buttons.LeftShoulder
- B1 = Buttons.A
- B2 = Buttons.B
- B3 = Buttons.RightTrigger
- B4 = Buttons.LeftTrigger
- Menu = Buttons.Start
- StickDown = Buttons.LeftThumbstickDown
- StickUp = Buttons.LeftThumbstickUp
- StickLeft = Buttons.LeftThumbstickLeft
- StickRight = Buttons.LeftThumbstickRight
