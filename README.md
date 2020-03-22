# MutiTypeGamepad
A class for easier use of SFML Joystick events, with automatic controller type detection and button mapping.

## Setup
1. Import and add files into your project.
2. This class uses SFML, so make sure you have it set up correctly in your project.
3. Include this class in the file you intend to use this in.
4. Create a Gamepad object.
5. Call the connect() function on the object (with a controller connected to the computer).
6. OPTIONAL: The class will try identify the controller type in the connect() function, but this is not perfect. It is recommended you have some sort of pop up or dialog to ask the user what type of controller they are using, and manually set the type using the setControllerType(ControllerType) function.

## Usage
Once the setup has been completed, the controller can be used by calling the update() function, and then the getCurrentState() function, then using . to specify which button you're looking for. Example of this below:<br><br>

``` c++
Gamepad gamepad;
gamepad.connect();

gamepad.update();

if (gamepad.getCurrentState().FaceButtonRight)
{
    // Do something
}
```


Each attribute in the gamepad state has a different type, for example:

``` c++
// DpadLeft is a bool
if (gamepad.getCurrentState().DpadLeft) { ... }

// LTrigger is a float
if (gamepad.getCurrentState().LTrigger > 50.0f) { ... }

// LeftThumbStick is a sf::Vector2f
if (gamepad.getCurrentState().LeftThumbStick.x > 0.0f) { ... }
```

### Button Clicks
If you want to check for a button click, opposed to simply checking if it's down, you can use the getPreviousState() function along with the getCurrentState() function. Example below:

``` c++
// The following statement is only true the frame the bottom face button is pressed
if (gamepad.getCurrentState().FaceBottom && !gamepad.getPreviousState().FaceBottom) { ... }
```

## Special Usage
While the functionality listed above should be enough for most use cases, there are many more functions included for more specific functionality, and for this reason, I would recommend reading through the comments in the header file, as the comments should cover the use of each function.
