# Recreating Boxhead 2Play

## Motivation
Boxhead 2Play was one of my favourite flash games growing up. Since flash player has been discontinued, I would like to bring the game into the modern era and allow a new generation to experience it.

## Objectives
- Playable in browser without excessive plugins
- Gamepad support
- Splitscreen support
- True to original game
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

For this project I would like to start out by using three js in the prototype phase. Later on I might use Rogue Engine or Babylon JS

In order to stay true to the original game, I would aim to set up an orthographic camera and position it in a way that matches the original 2d game overview camera.
