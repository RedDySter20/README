# MineNopoly

A Spigot (Bukkit) Minecraft plugin that implements automated Monopoly bank into the game.


## Features

- Monopoly bank functionality using a `chest`, `barrel` or any `shulker_box` in which game items are placed and removed from
- US, UK and RU game localizations support
- Player balance tracking using a scoreboard
- _Chance_ and _Community chest_ cards randomization
- _Houses_ implementation using `sea_pickles` (can be placed up to four in a single block)
- _Hotels_ `lantern` blocks immediate breaking without tools
- `player_head` blocks immediate breaking (assumed to be tokens)
- A book with links to get game items and a list and descriptions of all game properties
- Built-in dice randomizer
- Bank block breaking protection; game items consuming/placement protection
- Anti-counterfeiting game items protection via [NBT data](https://minecraft.fandom.com/wiki/NBT_format)


## Usage

### How to play?

You just build a playing field, place a chest (can also be a barrel or a shulker box) somewhere and call `/mn start <chest coordinates>`!  
To get and remove game items use [chat entries](#valid-in-game-chat-entries) and the book you can get via `/mn book <localization>`.  
_Houses_ and _Hotels_ are meant to be placed on street cells; all other items are meant not to be used in any way except keeping in the inventory and transferring between the players.  
To finish the game return all the game items to the bank (and type `--` to remove them) and call `/mn finish`; if you can't return them one of the server operators (by default) should call `/mn finish forced`.

### Commands

`/minenopoly` is the main plugin command, which has the alias `/mn`.

| Command              | Description                                                                   |
|----------------------|-------------------------------------------------------------------------------|
| `/mn help [command]` | Show help for given command, for available commands otherwise                 |
| `/mn book <loc>`     | Get the book to use during the game                                           |
| `/mn start <block>`  | Start the game (chat tracking, scoreboard, etc.) with given block as the bank |
| `/mn finish`         | Finish the game                                                               |
| `/mn finish forced`  | Finish even if not all game items have been returned                          |
| `/mn reload`         | Reload config                                                                 |
| `/mn get <args>`     | Auxiliary command used when clicking on links in the book                     |

### Valid in-game chat entries

_Note:_ Only available during the game.

| Chat entry  | Description                                                                    |
|-------------|--------------------------------------------------------------------------------|
| `+<number>` | Place given amount of game money into the bank                                 |
| `-<number>` | Remove given amount of game money from the bank (with change if needed)        |
| `--`        | Remove all game items from the bank (used action cards, sold properties, etc.) |
| `?`         | Roll the dice (display two random numbers from 1 to 6)                         |


## Configuration ([default](/src/main/resources/config.yml))

- Game distance (see config file for explanation)
- Game money items (also their denominations)
- Plugin messages
  - info
  - error
  - help


## Permissions

| Permission node            | Default | Description                                                             |
|----------------------------|---------|-------------------------------------------------------------------------|
| `minenopoly.help`          | true    | Allows using `/mn help` (lists only available commands)                 |
| `minenopoly.get`           | true    | Allows using `/mn get` and chat entries (allows to play basically)      |
| `minenopoly.book`          | true    | Allows using `/mn book`                                                 |
| `minenopoly.start`         | true    | Allows using `/mn start`                                                |
| `minenopoly.finish`        | true    | Allows using `/mn finish` (without `forced` argument)                   |
| `minenopoly.finish.forced` | op      | Allows using `/mn finish forced`                                        |
| `minenopoly.reload`        | op      | Allows using `/mn reload`                                               |
| `minenopoly.admin`         | op      | Refers to `minenopoly.reload` and `minenopoly.finish.forced` by default |


## Game field

Here is a [litematica](https://github.com/RedDySter20/README/blob/main/minenopoly_field.litematic) of the game field designed by me, however, you can always build your own!
