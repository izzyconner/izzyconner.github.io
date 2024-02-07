---
layout: single
title:  "Games Get Developed Engine"
date:   2022-01-24 00:57:03 -0500
tags: code classwork building-game-engines cpp games
---
For the final project in CS4850 Building Game Engines, my team (3) and I improved our tile map editor and built a simple 2D game engine based on the previous games made in the course.
<hr>
### *Tools, libraries, and languages used: C++, SDL, VSCode, Pybind, Python, tkinter*

[Github repo][github-repo]

[Original site here][game-engine-site]
<hr>
 While I had worked on the first iteration of the tile map and sprite editors, my main contribution to the final project was designing and coding the engine itself, as well as a small script demo of a 2D platformer.

## The design choices
For the design of the game engine, we decided to implement a component system where each subsystem of the engine (physics, sound, sprite, etc) was represented as a component that could be assigned to a Game Object, such that a Game Object would represent a collection of components. Resource managers were also implemented for any type of assets that would have to be loaded in (textures/sprites, audio, fonts, etc). This minimized the memory and runtime the engine had to use to load in assets by keeping track of which had already been requested and loaded in. We also heavily relied on an implementation of the factory pattern, in which each component was created and kept track of by a factory class for that subsystem. This allowed us to update each subsystem in the appropriate order without having to loop through each Game Object, or keep separate lists of components after they were created.

While the engine handled all of the 'heavy lifting', we also wanted users to be able to easily script their own games. To do this, we used the Pybind library to expose certain classes like GameObject and our various Components. This meant that users could write Python scripts using these exposed classes and code their own games.

## The Photographic Evidence

See our brief code walkthrough and engine demo below:

<iframe width="560" height="315" src="https://www.youtube.com/embed/5T_sPXCNY4o" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

<br>
<br>
Although I didn't work on this iteration of the tooling, I've also linked the walkthrough of our teams tile map editor below:

<iframe width="560" height="315" src="https://www.youtube.com/embed/qyyo-C-4Mvs" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

<br>
Debug Mode
![Debug Mode in Engine](/assets/images/DebugMode.png)

Normal Mode
![Debug Mode in Engine](/assets/images/NormalMode.png)

Our engine architecture diagram
![Engine archtecture diagram](/assets/images/EngineArchitectureDiagram.png)

## Post Mortem (written by our team)

For our TileMap Editor we wanted to create an environment where the user could easily load up any sprite sheets that they had, and have the tiles or gameobject within that sprite sheet be easily accessible to them within our environment. They would be able to see all of the individual tiles displayed in a grid with the properties for each tile being displayed when you click on that tile. Then being able to paint that tile into the game world, and ideally also be able to paint background tiles into the world. We also wanted to be able to have a displayed hierarchy of all of the different game objects within the level and give the user accessibility to change any aspects of the gameobject that they would want. In our current iteration we provide the user the ability to visually paint their tiles onto a tile map, and also visually place game objects onto the tilemap. We also allow the user to edit specific settings about the gameobjects. 

If we were given an extra 8 weeks to improve on our current design, we would most likely spend most of it working on updating user experience. Tkinter would still work fine for the basics of building up what we already have, and it does it’s job well enough for our purpose. The actual work that we would allote most of our time to is cleaning up the UI so it is much simpler and easier for the user to see and edit what information they would like to edit. The information panel currently only has set information that we pre-determined that the user would be able to edit. It would be nice if the user was able to add any other parameters that they believe that the object or tile should have, such as maybe allowing for moving tiles and such. And being able to add user customizability to the interface so that they could move the windows to specific areas that they feel would be better for their specific work.

Our Engine pulls JSON files that are produced from our Editor and is able to turn them into playable levels, and it also reads through a JSON with a list of all of the GameObjects on that level. However, that feature was not able to be fully produced in time for this assignment. If there were an extra 8 weeks of time, we would have been able to properly implement this function fully to be able to incorporate the full capabilities of our editor.

For bugs and problems that we encountered, there were 2 big ones that ended up cutting into a lot of our developement time. The first was that as we started exposing our collision logic with Pybind, we began to have some really glaring issues with collision detection. This was in part caused by the second issue, not realizing certain primative types weren’t being assigned default values that need to have those default values. This was leading to undefined behaviour that was causing us to think our logic itself was incorrect in a number of places, including our collision, which in turn caused us to waste quite a bit of time trying to track down the error before we realized that it was being caused by the uninitialized variables. Our collision detection itself had some issues in regards to scalability of the objects that were coliding that we had to spend quite a bit of time fixing to get them to collide properly.

[github-repo]: https://github.com/izzyconner/games-get-done
[game-engine-site]: https://j-ober7.github.io/GGDSite/
