# wc3-systems

Ideas for Warcraft III: Reforged systems for custom maps.

## Systems

### Unit Routine System

- Based on https://github.com/tdauth/tpof-talras/blob/master/src/Asl/Systems/World/Struct%20Routine.j
- Allows units to have daily routines at certain times of the day.

### Dialog Pages System

- Based on https://github.com/tdauth/tpof-talras/blob/master/src/Asl/Systems/Gui/Struct%20Dialog.j.
- Increases the maximum of dialog buttons per dialog.
- Automatically add buttons "Next" and "Previous".


### Weather/Four Seasons System

- Replace treees in seasons.
- Replace ground textures in seasons.
- Replace buildings and units in seasons.
- Weather effects depending on seasons and time.
- Lightnings during rain.
- Rays at day and night.
- Exclude regions from weather effects.

### AI Ships System

Warcraft III AI does not support ships. It even has issues building shipyards etc.
Features:

* Building shipyards.
* Defending ships.
* Custom attack waves at areas which are reachable by sea.
* Repairing ships.
* Transport ships (a bit harder).

### Handle Group System

Motivation: `force` and `group` support player and unit but other types should be supported, too.

Something like:

```
local itemgroup g = CreateItemGroup()
call ItemGroupAddItem(g, whichItem)
set tmpItem = FirstOfItemGroup(g)
call ItemGroupRemoveItem(g, whichItem)
call ItemGroupClear(g)
call DestroyItemGroup(g)
call IsItemInItemGroup(g, whichItem)
```

for every handle type and as trigger action.

### Idle Icon System

[Idle Icon System](https://github.com/tdauth/wc3-idle-icon-system): Custom idle icons for warrior types, heroes etc. inspired by games like AoM.

### Votekick system

[Votekick System](https://github.com/tdauth/wc3-votekick-system): Allows starting a votekick against a player with "-votekick X" where X is the player number or color. Typing "-yes" approves the votekick. By default, if more than half or players vote "-yes" he/she is kicked from the game. There is a time limit how long the votekick lasts and every player has a cooldown on how often he/she can start a votekick. Besides, there is a global votekick cooldown/only one votekick at a time.
This could also be based on a more general vote system.

### Multiboard Stats system

Multiboard based system which allows you to configure columns and lines with predefined stuff like: Player name, hero level, gold, lumber, unit kills etc.

### Turret System

https://github.com/tdauth/wc3-modern-warfare/tree/master/systems

### Black Arrow System

https://github.com/tdauth/wowr/tree/master/systems

### Item Unstack System

https://github.com/tdauth/wowr/tree/master/systems

### Player Stats system

Show player score and team score like in AoE which can be hidden with a button.

### Mock system

Allows sending mocks via chat, enabling/disabling them and easily configure sounds with texts from the original game.

### Vote system

Players can vote about choices with some timeout. If a player leaves the vote is subtracted, if the timeout expires a default vote is used.
Could provide an advanced UI compared to the basic dialogs or chat commands or tavern units/heroes for races, professions etc.
It could also be more abstract than the votekick system and the votekick system could be based on this.


### Item Craft System

Combining different items into new items.

### Unit/Item Respawn system

See my system in The Power of Fire. Units, heroes, items can respawn with custom time values, conditions and random creep/item tables. Besides, creeps can drop stuff etc.

### Save Code system

Basic save code system which can store different properties which are represented by integers. Save codes can be restricted to player hashes and contain checksums. See [World of Warcraft Reforged](https://github.com/tdauth/wowr).

### Missing fields system

Some fields for object types might be missing from the new natives like icons.
We can provide functions to register and retrieve icons for object IDs in a performant way if there are no natives to get the icons.
Icons are useful in multiboards, custom UI etc.

```
globals
  constant integer ICON_TYPE_ACTIVE_BUTTON = 0
  constant integer ICON_TYPE_PASSIVE_BUTTON = 1
  constant integer ICON_TYPE_ACTIVE_BUTTON_DIS = 2
  constant integer ICON_TYPE_PASSIVE_BUTTON_DIS = 3
  constant integer ICON_TYPE_RESEARCH_BUTTON = 4
  constant integer ICON_TYPE_RESEARCH_BUTTON_DIS = 5
  constant integer ICON_TYPE_OFF_BUTTON_DIS = 6
  constant integer ICON_TYPE_ON_BUTTON = 7
  constant integer ICON_TYPE_ON_BUTTON_DIS = 8
  constant integer ICON_TYPE_OFF_BUTTON = 9
  constant integer ICON_TYPE_OFF_BUTTON_DIS = 10
  constant integer ICON_TYPE_SCORE_BUTTON = 11
  constant integer ICON_TYPE_UPRADE_BUTTON = 12
endglobals

function GetObjectIdIcon takes integer id, integer t returns string
function HasObjectIdIcon takes integer id, integer t returns boolean
function SetObjectIdIcon takes integer id, integer t, string iconPath returns nothing

// Adds all Warcraft III icons.
function AddStandardObjectIdIcons takes nothing returns nothing
```

