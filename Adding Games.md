# The Holy Guide to Archipelago Game Integration

This guide walks through the process for developing a new game into Archipelago ecosystem.

There are two key requirements to successfully incorporate a game:

- A **world definition** that sets up all the locations, regions, items, rules, etc. to generate a seed.
- A **game client** capable of communicating with the Archipelago MultiServer.

A intermediate level of Python experience is required for writing the world definition, but game clients can be in any language as long as they can communicate with the server via the [AP Network Protocol](https://github.com/ArchipelagoMW/Archipelago/blob/main/docs/network%20protocol.md).

## World Definition

Creating a randomizer for Archipelago involves several steps that may need to be done, but the most important step is creating the world definition that holds all the logic and information about your game.

All games, thereafter called "worlds", exist in the `worlds` folder (who would have guessed?), and the Archipelago Generator and MultiServer reads from this directory to find game implementations.

A typical world definition will include the following information:

- Basic meta data about the game.
- A table of possible items.
- A table of possible locations.
- A table of possible randomizer options.
- Rules for determining when locations are "accessible".
- The underlying logic for how to generate a world.

To follow python conventions, your world folder should be formatted like so: `game_name`. Inside your `game_name` folder, you can have as many python files as you need to structure your game, but you will be required to include a `__init__.py` file to host your main game class so Archipelago knows where to pull your world data from.

Let's create an example game, called "Zorp". Create a folder named `zorp` in the `worlds` directory, then create a new `__init__.py` file in that folder.

