# Recreating Boxhead 2Play
27/11/2022
## Motivation

![image](https://user-images.githubusercontent.com/7433327/204143272-df4116cc-1331-4067-961e-495860d4562d.png)


Boxhead 2Play was one of my favourite flash games growing up. Since flash player has been discontinued, I would like to bring the game into the modern era and allow a new generation to experience it.

When you go to crazy monkey games and try to play the game, this is what the screen looks like after selecting a level.
<img src="https://user-images.githubusercontent.com/7433327/204144280-010bd1a1-e4b1-4d79-bc6e-05dee3fff7f2.png" width=50%>


Sure, downloading some old version of flash player which is riddled with security issues is an option to play today, but I think most people wouldn't bother. I want to make this game playable in browser, true to the original... this is starting to sound like a list!

## Objectives
- Playable in browser without excessive plugins
- Gamepad support
- Splitscreen support. Ideally, up to 4 players if it performs ok.
- True to original game, however with a very select few quality of life features of my choice as I play test.
  - A requirement to release and press the fire button again before firing will continue after a weapon is switched. In the original game it was very easy to accidentally place an explosive barrel or claymore when your gun ran out of ammo, resulting in your untimely death.
  - Splitscreen in the 2 player co-op mode. I have no idea what the original dev was thinking when they only had splitscreen on the deathmatch mode. Maybe a performance constraint when rendering a hundred zombies twice on the screen? Being trapped by the walls of the level because your friend has moved further away is not a good game experience. 
  - Slightly different approach to weapon ranges. There should be a damage fall-off after a certain range, rather than the bullet path stopping completely. This would hopefully make the deathmatch mode feel a bit better to play.
- Super stretch goal: dedicated server package and online multiplayer.

## Choosing an Engine
In the past I have dived in and directly used the html canvas and javascript. This time I think it would be a good opportunity for me to learn a new framework, or at least benefit from some of the hard work of others.

After some googling I have come up with a few options:

- [Easel JS](https://createjs.com/easeljs) - part of the Create JS suite of game-making tools, including Sound JS and Preload JS. 2d.
- [Phaser](http://phaser.io/) - offers web and mobile support features. 2d.
- [three js](https://threejs.org/) - API used to display 2d and 3d graphics.
- [Babylon js](https://www.babylonjs.com/) - a game engine which uses three js
- [Rogue Engine](https://rogueengine.io/) - another game engine which uses three js

A more comprehensive list can be found [here](https://html5gameengine.com/).

Boxhead is a 2d game. However the player, zombie and devil assets appear to have been made using [Autodesk Softimage](https://en.wikipedia.org/wiki/Autodesk_Softimage), and then exported to some data format which is then used in the flash game.

Given that I will likely need to recreate these 3d assets (given their blocky style this should be faster than trying to make sense of the XSI data in the game files), I think it makes sense to me that I should consider a 3d solution as a viable option here.

I am also unconvinced that scaling graphics is a solved problem even in 2022, compared to flash's scalable vectors. Using scalable vector graphics (SVG) may be a solution for 2d, but I am sceptical about the performance hit that their use might have on the game. Also as stated above, I am going to have to make some 3d assets anyway so...

For this project I would like to start out by using three js in the prototype phase. Later on I might use Rogue Engine or Babylon JS.

In order to stay true to the original game, I would aim to set up an orthographic camera and position it in a way that matches the original 2d game overview camera.

![image](https://user-images.githubusercontent.com/7433327/204143242-d801144a-b22f-4245-a45f-b2efc936ad11.png)


## Before we get too far into this...
The original developer of Boxhead did do a mobile release a few years ago, but in the nicest possible way and with the greatest respect, I am going to assume it is just awful. I'm not even going to look at it.

At time of writing the word Boxhead doesn't even appear on the original creator's website which, for a game series with probably 100 million plays as a conservative estimate, is very telling. The later entries in the series were more focused around in-game currency and social media integration, so Boxhead 2Play is where I am choosing to draw the line in my memory. A special mention goes to the gameplay of Boxhead Bounty which was a fun online PvP experience. 

I really do understand the original dev caving in to the allure of monetisation and social media presence. It is a nice example in my opinion of how a series can pretty much instantly die out when gameplay becomes secondary to business.

Anyway moving on. Recently someone has made a new Boxhead mobile game, some footage [here](https://www.youtube.com/watch?v=jlqIfztUIkY).

![image](https://user-images.githubusercontent.com/7433327/204141858-193eeb6e-6063-43e0-a7fb-f60aac5a8323.png)


This looks **ok**. There are a few things I want to comment on.

They have used perspective camera instead of orthographic. This causes a lot of immediate problems for a game that is trying to recreate the Boxhead magic.

How do you handle the boundary of the playable map area? Due to the nature of the perspective camera, you are going to have space around the edges of a rectangular play area. Maybe you could try to bound the camera to a smaller range, or add some fog effects, anything really. Doing nothing, and centering the camera on the player at all times is not a design choice I agree with. It looks like a tilt ball maze game with some zombies on it.

In the original game, enemies are spawned off-screen. In this mobile game, that is not an option due to the earlier camera design decision.
I do like the way they handled it though, where zombies will climb out of the graves placed in the map.

I did like the dev's use of lighting effects and mobile controls, and hopefully I can a similar level of polish on my version.

Their use of camera shake is a little obnoxious, I will endeavour to limit the amplitude and planes of movements to make this a more subtle effect.

I dislike the 360 degree movement. To me it looks out of place compared to the 8-directional movement of the original game, and it serves to make the enemies look like a swarm walking directly at the player. 

Boxhead is not a complex game, but there is a huge amount of charm in something as simple as a trapped zombie walking back and forth, pausing for thought in-between to change direction. I am not quite sure that this count as emergent gameplay, but it is something I hope I can accurately recreate. I am not sure, but I suspect that this dev has not added walls or barrels to the game since this would complicate the pathfinding. 

Actions speak louder than words so we'll see how far I get!

## First steps
There is a lot to do to get anywhere close to a playable game, even when recreating an existing one! Some roadmap items could include...

- creating the 3d assets and animations (player, zombie, devil, wall, barrel, guns, and more...)
- setting up a three js project, making an orthographic camera.
- recreating the original game levels using my new assets - some sort of compositor like rogue engine or babylon may be useful at this stage
- collision detection - hopefully this can largely be done in 2D using axis-aligned bounding boxes. Possibly 3d raycasting for bullets?
- wave logic - how many zombies/devils spawn and when?
- other game logic - how often do weapons spawn? How fast does the kill combo timer tick down?
- **pathfinding** - this is the big one. Making the zombies behave like they do in the original game is important to really capture the feel.
- setting up splitscreen

For the first steps, I think I want to have a play around with three js and see if my idea of simulating the original 2d view in 3d is working ok.
Maybe setting up a simple scene with an orthographic camera, importing a wall model and some basic world lighting.

This is going to take a long time, and may never be completed, but should be a fun journey for as long as it takes. I'll see you next time!


