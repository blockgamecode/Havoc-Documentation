## Note

A note on some of the lingo that might be used in this document:

Storage-Key: All servers have their storage key, which may or may not differentiate them from other servers (More than one server can share the same storage key)

## Wars
  
Wars allow teams to fight for control of locations.  

## Setting Up War Locations  
  
In order to create a new war location, you must do the following:  
  
Go to the center of the location you want to create the war at, then do  
**/war newmap**.
To edit a current exist location, use **/war editloc <locid>**.
  
To add a holdable location, do **/war addholdable <radius\>**. *Undo this with **/war undo-last-holdable***  
  
To add a player spawn point, do **/war addspawn**. *Undo this with **/war cancel-last-spawn***  
Set the map's name with **/war setlocname <name\>**  
  
To finish creating the location and add it to the list: **/war finish**
  
### Some other useful location commands:  
  
**/war view-locations** - View the current war locations (gives option to delete them)  
**/war delete-location <id\>** - Delete the specified war location  

## War administrative commands

To set the next war date: **/war setwardate <date (Format: 1970-01-01 00:00:00)>**

## View war information

To view the info of a specific war: **/war seewarinfo <warID>**
To open the war stats menu: **/war stats**
To view the last X wars: **/war lastwars <X>**
To view the leaders of a current war: **/war leaders**
To view the leaders (Teams or equivalent) of a current war: **/war teamleaders**

# Others

To change to/from the war scoreboard: **/war scoreboard**

## Seasons

Seasons have a default duration of 10 weeks.

Each team has a given score, incremented by performing certain actions in the game (To configure this to a specific gamemode, talk to one of the devs).

Each player also has a score like the teams.

Players may have 2 different scores, one for the player competitions where they only compete against other singular players and the so called teamless score, which is the score of the player for competing with other teams. When a player joins a team, his teamless score is kept and he will now start contributing points towards his team. He may receive 3 reward sets if both his team score, teamless score and player score are in the placements.

Normally players can also receive 2 reward sets one for the player ladder, another for the team ladder.
Team rewards are given equally to all members, player rewards are individual to the player.

At the end of the season, these rewards are given out to the placement first teams/teamless and players.

View further down, in rewards how to set the rewards for a given season.

# Season administrative commands

To generate the next X upcoming season on your storage key so you can preemptively edit some of their attributes: **/seasons genupcoming <X> <Default team reward group> <Default player reward group> <Format for the season name (Available modifiers: %seasonnumber% for the season number)>**

If a season is not preemptively generated, it will be generated automatically when the previous season ends, sharing the same attributes as the previous.

To increment the score of a player: **/seasons incrementpscore <player> <Score>**
To increment the score of a team: **/seasons incrementtscore <team> <score>**

Attempt to end the current season, and consequently assign all of the rewards: **/seasons attemptend**

Change the name of a season: **/season changename <globalid> <new season name>** (To get the season global id, see bellow commands on war info).

Change the team rewards of a season: **/season changereward <globalid> <reward group>** (To get the season global id, see bellow commands on war info).

Change the player rewards of a season: **/season changepreward <globalid> <reward group>**(To get the season global id, see bellow commands on war info).

## Season information

To list the previous X seasons: **/seasons listprevious <X>**
To list the upcoming X seasons (Only generated seasons will be shown): **/seasons listupcoming <X>**

To see the info of a season with a certain number: **/seasons info <season number>**
To see the info of a season by its global id: **/seasons infog <globalid>**

To open the season statistics menus: **/seasons stats**

Do **/seasons help** and **/wars help** to view info on creating each. More info to follow...  

## Setting Up Rewards 
  
Rewards are organized into "reward groups", which are stored in MySQL. Reward groups map placements (i.e. 1st, 2nd, 3rd) to a list of prizes. Prizes can include items (spawned using item registry system with modules, similar to loot lists, crates, etc), commands, crates, etc.  
  
Rewards are created using the /rewards command in GMUtils.  

To create a specific reward in a reward group, do 
**/reward create \<reward group> \<placement> \<reward type> \<reward args>**

 - Reward Group is a numeric id that refers to a group of placement rewards. For example, there will be two reward group per war. One reward group for teams, and one for players. Each group contains rewards for multiple placements.
 - Placement is the numeric placement (i.e 1 for 1st, 2 for 2nd, etc)
 - Reward Type is the type of reward you are creating, and Reward Args are the args that describe that type. **Valid types:**
 
|Reward Type | Description | Args  |
|--|--|--|
| COMMAND| Perform a command from console. | The command to be performed. Use %player% for player name. |
| REG_ITEM| Give the player a special item (from a module). Similar to loot, crates, etc.  | \<Registry Module> \<Item Name> \<Amount> *(ex: Gun AK47 1)*|
| CURRENCY| Give the player a currency. | \<Currency Key> \<Amount> *(Do /curr list to see currency keys)*|
| CRATE| Give the player a crate. | \<Crate Key> \<Amount> *(Do /crate list to see crate keys)*|
| VAULT| Give the player a vault. | \<Vault Name> \<Vault Type> \<Amount> *(Do /vault list to see vaults names and types.)*|
| ITEM| Give the player the item in your hand. | N/A |


Each reward you create will have an individual id, which will be displayed to you when you create the reward. Use **/reward groups** to list active *reward groups*, and **/reward view \<group id>** to view the rewards within a reward group (you can use this to get individual reward ids).

Use **/reward delete \<reward id>** to remove a specific reward.

Use **/reward update \<reward id> \<new reward type> \<reward arguments>** to update a reward. Reward type and arguments are the same as for creeating a reward.

## Setting Rewards

To set rewards for individual wars, use the following commands:
  
**/war setteamreward \<reward group id> <set for all (true/false)>** is used to sets the reward group for team placements.  For the second arg, put true if you want to set the reward for all following wars (if set to false this will only be applied to the current war), and false otherwise.

**/war setplayerrewards \<reward group id> <set for all (true/false)>** is used to sets the reward group for player placements. For the second arg, put true if you want to set the reward for all following wars (if set to false this will only be applied to the current war), and false otherwise.

To set seasonal rewards, use the following commands:

**/season changereward \<season global id> \<reward group id>** is used to sets the reward group for team placements.  

**/season changepreward \<season global id> \<reward group id>** is used to sets the reward group for player placements.

