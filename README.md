# snesplay
A library for connecting SNES AI bots to an emulator

## Overview
Contains a lua library that scrapes predetermined hex values from a game, transforms them using a user-specified function that turns them to JSON, dumps them into a gamestate file, scrapes control inputs from input files, and applies the control inputs to the emulator.

The end goal of this is to create a "player agent" shim bot that forwards data from the emulator to a gamestate file and imports simulated human input from controller files to be applied to the game. Thus, the program gathers genericizes game information and "presses" input buttons just like a human, giving a clean stand-in link for AI bots to fill in the "thinking" step. The impetus for this is to easily create solo, cooperative, or competative bots that play video games according to their programming.

## Logic
Startup
* Read the hexscrapes.cfg file and dump it to a memory object
* Read the transform.lua file and load it

Each frame
* Scrape the hex values specified in hexscrapes.cfg and assign them to a dictionary
* Call the transform function, passing the dictionary and a dictionary of internal state variables
* Write the result into the gamestate.json file
* Read values from controller1.json
* Read values from controller2.json
* Apply input values to the game state.

