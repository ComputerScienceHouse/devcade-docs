# First Game

So, you want to make a Devcade game? Well you chose the right place.

#### Choosing a Language

We officially support and have resources for Monogame games written in C# and have community support for Bevy games written in Rust. Many other engines and frameworks have been explored and proven to work, but don't yet have full support.


Although these are the only two languages that we "officially" support, you are not limited to only those two languages. You could theoretically make a Devcade game in whatever language you want, and it will run on Devcade as long as you build it for the appropriate system specifications. However, something to keep in mind is that since we do not have a library for other languages, you would have to figure out how to handle the things our libraries handle yourself.

If you do make a game using something other than MonoGame or Bevy, we encourage you to write up some instructions on how to do the things that a library might provide for you, and open a pull request to the docs site to add your documentation. We would be happy to review it, and we would love to help you get it merged.

#### Resources

Here are links to resources that we provide for Monogame and Bevy:

- [Monogame Template](/template-repo)
- [Monogame Library](/library-repo)
- [Flatpakify](/flatpakify-repo)
- [Rust Library](https://docs.rs/devcaders/latest/devcaders/) (Community supported)

#### Devcade Controls

As you get started, you will want to keep in mind the details of the Devcade system you are designing for. For the CSH Devcade cabinet, you will want to note that the display is a 9:21 ultrawide monitor turned vertical (measuring 1080x2560). The computer that the CSH Devcade cabinet is running on has an 8th gen Intel processor and integrated graphics.

For more specific information about the cabinet hardware, check out the [Hardware](/Hardware/) section

### Uploading to Devcade

Once youve got something playable you want to put on the cabinet, you should build and zip your game in a manner such that it is self contained and should require no runtimes or other resources. Then head over to the website, log in, and go to the upload page. There should also be instructions on that page for packaging your game. Upload the zip, banner image, and icon image and give it a name and description. If all is good you should be able to hit upload and it should work. Pressing both menu buttons will refresh the games list on the cabinet and hopefully you will see you game!

### Using the API

If you want to work with the Devcade API, check out the [API](Internals/API/) page. This will give you all the information you need to make requests to the API, and which endpoints to use.

### Building a Devcade Cabinet

If you want to make your own Devcade machine, check out the [Hardware](Hardware/) page. This page includes a bill of materials and instructions that were followed when making the first Devcade machine.
