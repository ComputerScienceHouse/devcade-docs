# Making Your First Devcade Game

So, you want to make a Devcade game? Well you chose the right place.

We officially support and have resources for Monogame games written in C# and have community support for Bevy games written in Rust. Many other engines and frameworks have been explored and proven to work, but don't yet have full support.

?> Devcade can theoretically run any executable as long as the game is formatted properly, runs on linux, and works with a few other restrictions but you will have to figure some stuff out yourself that would be done for you in one of our libraries and we make no guarantees on getting it to work.

If any of these seem useful to you, or if you want to learn more about what each thing provides, check out the links below.

### MonoGame Template

The MonoGame template is a Github repository that contains a mostly empty Monogame project that you can use as a starting point for making a Devcade game. This project contains the Monogame library already initialized and added to the project, as well as code blocks that will set the aspect ratio of the game window to the aspect ratio of the current Devcade monitor.

More details here: [Monogame Template](/template-repo)

### Monogame Library

The Monogame library contains two main utility classes that make it easier to adapt a Monogame game to Devcade. The first one is a static input manager class that makes it easier for your game to capture inputs from Devcade's control panel. The other one is a helper class to allow games to read and write data to pipes, allowing you to have save data that persists after the game is closed.

More details here: [Monogame Library](/library-repo)

### Rust Library

Similarly to the Monogame library, the Rust library provides utility functions to make it easier to capture input from Devcade's control panel from a Bevy game.

More details here: [Rust Library](https://docs.rs/devcaders/latest/devcaders/) (Community supported)

### Flatpakify

Flatpakify is a repository that makes it easy to package the publish folder of a Monogame project into a Flatpak that is compatible with Devcade.

More details here: [Flatpakify](/flatpakify-repo)
