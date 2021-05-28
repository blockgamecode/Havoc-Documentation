# Wars  & Seasons
  
Wars allow teams to fight for control of locations.  
  
  
## Setting Up War Locations  
  
In order to create a new war location, you must do the following:  
  
Go to the center of the location you want to create the war at, then do  
**/war newmap**  
  
To add a holdable location, do **/war addholdable <radius\>**. *Undo this with **/war undo-last-holdable***  
  
To add a player spawn point, do **/war addspawn**. *Undo this with **/war cancel-last-spawn***  
  
Set the map's name with **/war set-map-name <name\>**  
  
### Some other useful location commands:  
  
**/war view-locations** - View the current war locations (gives option to delete them)  
**/war delete-location <id\>** - Delete the specified war location  

## Creating Seasons and Wars

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
  
**/war set-team-reward \<reward group id> <set for all (true/false)>** is used to sets the reward group for team placements.  For the second arg, put true if you want to set the reward for all following rewards, and false otherwise.

**/war set-player-reward \<reward group id> <set for all (true/false)>** is used to sets the reward group for player placements. For the second arg, put true if you want to set the reward for all following rewards, and false otherwise.

To set seasonal rewards, use the following commands:

**/season set-team-reward \<season global id> \<reward group id>** is used to sets the reward group for team placements.  

**/season set-player-reward \<season global id> \<reward group id>** is used to sets the reward group for player placements.

