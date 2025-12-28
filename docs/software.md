# How Devcade Works

Devcade is a project with many moving parts and a couple of ways that data moves around. In this section I will attempt to explain and overview how it all fits together and works at a high level. For more details on the workings or usage on any individual part, check out its dedicated page which is pulled directly from the readme of its repo.

## All the parts
### Onboard
The software running on the Devcade cabinet itself is known as the [onboard](/onboard-repo) and is further broken into two parts. First is the frontend, which primarily acts as the interface to the user and is relatively simple. It displays the list of games, plays animations, allows the user to scroll and select games or filters, etc. What it doesn't do however, is the rest of the actions needed to make anything more than visuals happen. That is handled by the backend.
The backend is a separate program within the same repository that runs in the background of the Devcade cabinet handling all of the dirty work. It talks to the frontend and any running game through a couple of sockets so that the parts that take user input can tell the backend what actually important actions to take. It performs all the actions like downloading data such as games and metadata from the API, launching games, and uploading data. Details of these actions, interactions, and interfaces should be found in its dedicated page. 

### Website
The [Devcade website](/website-repo) is, as you might expect, the [main public website](https://devcade.csh.rit.edu) for the project. It serves a couple of purposes, to act as a public landing page with basic information on what the project is and why its cool, and to be the direct interface for users looking through all the games or uploading new games. The former is a simple goal performed with mostly static sections of the site but the latter is lots of back and forth with the API. 
The website also handles accounts in a couple of forms to restrict some games from view, and to keep track of who uploaded a game. The way we have it set up at the moment it integrates with our organizations existing SSO auth as well as offering an option to log in with google for RIT accounts. At this time there is no login for the general public outside of the Rochester Institute of Technology.

### Game Libraries
Games running on Devcade sometimes need to interact with the cabinet or other infrastructure while running. This might include simply mapping controls in a more convenient manner, saving or loading data from our servers, or in some cases, other cabinet specific actions such as reading ID cards from an NFC reader or other future actions. Currently we only have an official [library for MonoGame](/library-repo) in C# but there are some other community supported ones and you also don't necessarily need to use one to get your game working on Devcade.

### API
The [API](/api-repo) is the point between the infrastructure running in the background and the website, onboard, and anything else that wants to interact with the data we store. We have it set up at the ['api/'](https://devcade.csh.rit.edu/api/) route within the main websites domain and in addition to its repository readme, it also hosts [swagger docs](https://devcade.csh.rit.edu/api/docs/) for all of the routes it provides. 

The sources of data that this API talks to and provides an interface for are a database and S3. The postgresql database stores metadata about games, tags, and users while the S3 buckets store games themselves, game images and banners, as well as any save data from games utilizing that feature. 

### Game Templates
While not necessarily part of the vital operation of Devcade, we do provide templates for people to use when making games for the project. At the moment we just have one for [MonoGame](/template-repo). They set up some things for the user such as the library and aspect ratio.

### Flatpakify
[Flatpakify](/flatpakify-repo) is a tool developed to help users package their games into Flatpaks. This is required in order for games to be uploaded and run on Devcade but can be an unfamiliar process to many. This tool helps to simplify that process by doing most of it for you, given the right input. It is originally designed to work with C# projects but with some workarounds it can be used on other projects as well.

### Documentation
Thats what you are reading here. You probably know why its here, but in addition to providing useful information that doesn't otherwise have a home, it also brings the READMEs of all of the other repos together into one convenient spot for viewing, [including its own](#/).

## The standard flow of operation

In the normal course of operation of a functioning setup, just about everything is initiated by the Devcade cabinet itself. The software running on the cabinet, known as the [onboard](/onboard-repo), starts up as the computer turns on and the frontend immediately asks the backend to reach out to the [API](/api-repo) for all of the data needed to show a user all of the games available. The API grabs the data needed from the database and S3 and sends it back. The backend then receives it, caches some of it that wasn't already, and passes it to the frontend. 

The user may then select a game and play it from the now populated frontend. The frontend tells the backend to launch this game and if it is already downloaded it will get the hash of the game from the API and check if the downloaded version is current. If not, or if it was never downloaded in the first place, it downloads the game from the API. At this point the backend runs the game. From here the game might ask the backend for some actions through the games library such as saving data. The backend would once again, make the API requests and pass them around. Once the game closes, we return to the base state of the frontend displaying the games and waiting for input.

## The game makers flow

For a developer looking to make a game, the rest of the project comes into play. They might start with the [template](/template-repo) which gets them started for working with Devcade and includes the [library](/library-repo). With this they build out their game, maybe using some library functions along the way. Once they are ready to put the game on Devcade, they head to the [website](/website-repo), log in, and create a new game. Following the instructions, they compile their game and follow [Flatpakify](/flatpakify-repo)s instructions to package it together. This gets uploaded to the website and further through the API to find its spot on the servers. 

Once that new game has been uploaded, the next time someone refreshes the onboard and it gets a fresh list of games, it will be displayed and playable!
