PACMAN, An Illustrative Example
========================
In order to explain the fAARS approach to developing games, we will describe the capabilities of the platform and the game-development process it supports, using the well-known Pacman game as an illustrative example. This game is an immensely popular arcade game that starred a small, yellow, puck-shaped character being chased around by ghosts while trying to eat every “pill” on a map. The rules of this game are very simple. Pacman must attempt to collect all the “pills” and “powerpills”  all around a space, while avoiding being caught by four Ghosts chasing it. If Pacman can eat all the “pills” without being caught, then Pacman wins. Now, let us picture Pacman, but played on a real-life scale: city blocks are the map, Pacman and the Ghosts are players with smart-phones, and QR codes scattered throughout the game area are the “pills” that Pacman needs to scan in order to win the game. 
In 2004, graduate students at the New York University created such a version of the game: “Pac-Manhattan”. It involved ten players: one Pacman, four Ghosts, and a “controller” for Pacman and each of the Ghosts, whose responsibility was keeping each player updated on the positions of others out in the field. 
Our version of the game, developed in the fAARS platform, is very similar: Pacman and four Ghosts each suit up with a smart-phone equipped with a QR code scanner and a data connection. QR codes are affixed around the game area representing the “pills” that Pacman has to collect, and on the players; no special-purpose controllers are required.  In order to create and run fAARS-Pacman, a two-step process should be followed: (a) entering the game rules into the database, and (b) uploading the media content that will be used during game play to an online repository. 
In order to create the game rules, the Actors/Game-Objects of the game should be first identified. An Actor/Game-Object represents a player in the context of a fAARS game. In this case, fAARS-Pacman has a total of five Actors/Game-Objects, one Pacman and four Ghosts. The rules of the game can then be created, in terms of Event-Condition-Action (ECA) rules.

Although a game-authoring environment has not yet been implemented as part of the fAARS platform, the process of entering the rules of a game into the fAARS database is rather straightforward. The first step is to identify the Actors/Game-Objects of the game. For instance, there are five Actors/Game-Objects in fAARS-Pacman, Pacman and the four Ghosts. The regular arcade version game of Pacman has multiple rules that can be represented as Event-Condition-Action rules that can be understood by fAARS. In order to illustrate the process, we will use two Pacman rules as examples:

1.	A Ghost can capture Pacman while Pacman has not eaten a “powerpill”

2.	Pacman can capture Ghosts after Pacman eats a “powerpill”.

Three steps are necessary to define these Pacman rules as fAARS ECA rules:

First, an Event must be defined to cause the first ECA rule to fire. This implies that we need to translate the actions of an Event generator over an Event recipient to the corresponding Event type in the real world. The “capture” and "eat" actions can be translated as follows:

1.	“A Ghost captures Pacman”.

2.	"Pacman captures a Ghost”.

3.	“Pacman eats a powerpill”.

In the context of fAARS-Pacman, these set of events happen in the real world by decoding QR codes using a smart-phone.
Although in the third event specification above a “powerpill” is referred to as the Event recipient, a "powerpill" is a game item that allows Pacman to change its state and increase its score. The way to represent this game item in the context of fAARS-Pacman is to create an instance of an Actor/Game-Objects as the “powerpill”.
The next step in the rule-specification process involves the specification of the Condition(s) to activate one ECA rule. A rule is activated based on the current state of the Actors that are involved in an Event, the generator and the recipient. A set of states for each of the Actors/Game-Objects in a game has to be defined based on their game roles. For example, although in fAARS-Pacman there are five Actors, there are only two game roles: an Actor/Game-Object can be either Pacman or a Ghost. Pacman can be in one of three states at a time: (a) “chasing” a Ghost after having eaten a “powerpill”, (b) “running_away” from a Ghost, or (c) “captured”. In the same way, a Ghost can be in either one of three states at any time: (a) “chasing”, (b) “running_away”, or (c) “captured”. Using this information, the conditions of each of the ECA rules that correspond to each of the Events defined in the previous step are: 

1.	“When Ghost is in the chasing state” and “When Pacman is in the running_away state”.

2.	“When Pacman is in the chasing state” and “When Ghost is in the running_away state”.

3.	“When Pacman is in the running_away state”.

Finally, the third step of the process involves defining the set of Actions that have to be performed by the platform when an ECA rule fires. There are three different types of Actions that can be performed by the fAARS platform, which are: (1) update the current state of the generator and/or recipient involved in an Event, or/and (2) send a pushed notification to the generator and/or recipient of an Event, or/and (3) update the score of the generator and/or recipient of an Event. In fAARS-Pacman, for each of the Event-Condition values previously defined as part of the ECA rules, the set of Actions to be performed by the fAARS platform are (1), (2), and (3) for both, the generator and the recipient of the Events for all three ECA rules. Details about the Actions performed by the platform as part of each of the ECA rules follows.

ECA rule one: “A Ghost(generator) captures Pacman(recipient)” 

Event: “A Ghost captures Pacman”

Condition: “When Ghost is in the chasing state" and "When Pacman is in the running_away state”

Action: (1) Change the current state of Pacman to “captured”, (2) send a notification to the generator and recipient of the Event with information about what just happened in the game, and (3) update the score of the generator and recipient of the Event accordingly.

ECA rule two: The “Pacman(generator) captures a Ghost(recipient)” 

Event: “Pacman captures A Ghost”

Condition: “When Pacman is in the chasing state” and “When Ghost is in the running_away state”

Action: (1) Change the current state of the corresponding Ghost to “captured”, (2) send a notification to the generator and recipient of the Event with information about what just happened in the game, and (3) update the score of the generator and recipient of the Event accordingly.

ECA rule three: The “Pacman(generator) eats a powerpill(recipient)” 

Event: "Pacman eats a powerpill"

Condition: "When Pacman is in the running_away state"

Action: (1) Change the current state of all the Ghosts to “running_away”, and change the current state of Pacman to “chasing”, (2) send a notification to the generator and recipient of the Event with information about what just happened in the game, and (3) update the score of the generator Event accordingly.

The process of entering the ECA rules into the database is also relatively straightforward. There are four tables in the fAARS database that together contain all the ECA rules of all the games that run in the platform. One of these tables links a game with all its ECA rules. This table is called “ECA_Rules”, and it contains as many entries as the number of ECA rules created for all the games in the platform. The relationship between one MAARG and one ECA rule generates a key value that is exported to three other tables that specify the Event, Condition, and Actions of the ECA rule. The table that contains the Events entries is composed by three columns, where the generator, recipient, and the type of Event can be entered for each of the ECA rules. The Condition table is composed by three columns as well, and these columns contain the conditions that the generator and recipient must comply with. In this table we can save the name of a condition, define to whom the condition applies, and the value of that condition. Each row in this table contains as many conditions as are applicable for a particular ECA rule for both, the generator and recipient of an Event. Finally, the Actions table contains the actions that the fAARS platform has to perform. It is composed by three columns, and contains the name of the action, the recipient of the action, which could be the generator or recipient of an Event, and the value that will be used to perform the action. At run time, when the Event Processing Engine receives an Event during game play, it extracts from the fAARS database all the key values contained in the “ECA_Rules” table based on the ID of the game, and filters the generated list by querying the Event and Condition tables in order to compute the corresponding Actions. This and other functions are performed by the Event Processing Engine, which is described in the following section.

When all the ECA rules of a game are defined and entered into the database, the media content that will be used in the Heads-Up Display (HUD) of the game is uploaded to an online repository. The HUD is the component through which players receive feedback about game state changes during game play, and can run on a smart-phone.
Players can login, and as the game progresses, the game rules are evaluated, and actions are executed by the fAARS game engine in real-time as Events happen during game play. Players walk around a specific physical area while decoding QR codes affixed to players and walls to advance the game, thus generating real world Events. In the context of the fAARS platform, an Event describes an interaction between two Actors. There can be multiple Events during game play, and they are all managed by the fAARS game engine in order to process the ECA rules to update the state of the Actors in the game. Furthermore, at any time during the game, players can track their scores and status on their smart-phones, and they can continue playing the game until either Pacman dies or when Pacman finishes eating all the “pills”. 
