### Making a Game

If you are looking to make a Devcade game, there are a couple considerations to keep in mind.

#### Choosing a Language

Firstly, you should think about what language you want to develop the game in. The Devcade project currently supports C# using MonoGame, as well as Rust using Bevy. We provide libraries for these languages to help make parts of the development process easier. These libraries assist with things such as interpreting Devcade inputs, reading and writing to pipes for save data, setting the proper aspect ratio, and more.

Although these are the only two languages that we "officially" support, you are not limited to only those two languages. You could theoretically make a Devcade game in whatever language you want, and it will run on Devcade as long as you build it for the appropriate system specifications. However, something to keep in mind is that since we do not have a library for other languages, you would have to figure out how to handle the things our libraries handle yourself.

If you do make a game using something other than MonoGame or Bevy, we encourage you to write up some instructions on how to do the things that a library might provide for you, and open a pull request to the docs site to add your documentation. We would be happy to review it, and we would love to help you get it merged.

#### Devcade Controls

As you get started, you will want to keep in mind the details of the Devcade system you are designing for. For the CSH Devcade cabinet, you will want to note that the display is a 9:21 ultrawide monitor turned vertical (measuring 1080x2560). The computer that the CSH Devcade cabinet is running on has an 8th gen Intel processor and integrated graphics. 

Once youve got something playable you want to put on the cabinet, you should build and zip your game in a manner such that it is self contained and should require no runtimes or other resources. Then head over to the website, log in, and go to the upload page. There should also be instructions on that page for packaging your game. Upload the zip, banner image, and icon image and give it a name and description. If all is good you should be able to hit upload and it should work. Pressing both menu buttons will refresh the games list on the cabinet and hopefully you will see you game!

### Using the API

If you want to work with the Devcade API, check out the [API](Internals/API/) page. This will give you all the information you need to make requests to the API, and which endpoints to use.

### Building a Devcade Cabinet

If you want to make your own Devcade machine, check out the [Hardware](Hardware/) page. This page includes a bill of materials and instructions that were followed when making the first Devcade machine.
