### Collin Butterworth's COMP280-A1 Project ###

## Documentation for Worksheet 1 ##
My AI has 5 states in its behaviour tree with sub-states in each of them. The AI is modeled after a typical stealth game AI, and I had a lot of help developing it using this tutorial series on YouTube by Ryan Laley: https://youtube.com/playlist?list=PL4G2bSPE_8un8IplTvVrqPRt7Ey8-3obR

The first and default state that they are in is a patrol state. There are Patrol Point objects placed throughout the environment and stored in an array for the AI to move through. At each patrol point, they rotate to face the attached arrow component, and can be told to wait for a specific amount of time. Additionally, there is a variable wait time setting to randomly adjust the amount of time they wait at said Patrol Point. When they have reached the end of their patrol route, I have added 3 possible behaviours to be used: stay, go back, and loop. If they are told to stay, they will stay at their last Patrol Point. If they are told to go back, they will turn around and go back through their patrol route in reverse order. If they are told to loop, they will move to the first Patrol Point and restart the patrol route.

The second state is a searching state. This is set up so that the AI will not resume their patrol immediately after losing sight of the player, instead, they will move to the player's last known location.

The third state is when they spot the player. They will start chasing the player at an increased speed. Once they lose sight of the player, they will move to the player's last known location, wait 2 seconds, search around in a short distance determined by a task to find a random point within a given radius 3 times waiting 2 seconds at each search point, and then if they still haven't found the player, they move into the "suspicious" state.

The fourth state is the suspicious state. They will search in a very large radius for 10 seconds without waiting at any search point. If they still have not found the player by then, they will enter the fifth state.

The fifth state is the giving up state. They will exit the suspicious state and move back to their patrol route and re-enter the first state.

On top of the behaviour tree for the AI, I have given them walking animations. Likewise, the player also has walking animations. As the player, you can crouch by pressing shift or prone by holding shift. I couldn't find any free assets for the prone animation, but there are crouching animations.

## Documentation for Worksheet 2 ##

All of these issues were found by the developer playtesting the game with heuristics in mind as well as having another person playtesting the game and asking them questions about it while they were playing it. These heuristics were taken from Jakob Nielsen's 10 general principles for interaction design. They can be found here: https://www.nngroup.com/articles/ten-usability-heuristics/

# Heuristic 1 - Visibility of system status #

Heuristic: The design should always keep users informed about what is going on, through appropriate feedback within a reasonable amount of time.

Analysis: There is no UI whatsoever, which is quite an issue for determining system status. The only indication the user has to when a guard has spotted them is that the guard faces their direction and starts moving towards them. Possible solutions to this include a symbol above the AI's heads to determine what state they're in, audio cues to alert the player that they've been seen, and UI cues such as the screen turning red to alert the player that they've been seen. Also, there is no win/loss state or objective to follow, so the player will be confused about what to do. To fix this, an objective should be added, UI should be added to show the player what the object is, such as a minimap or an arrow pointing to the objective, or even just a message telling the player what to do. A win state to finish the level and a loss state to restart the level also need to be implemented in order to let the player know they have either succeeded or failed in completing the main objective.

Playtester's experience: 

Solution:

# Heuristic 2 - Match between system and the real world #

Heuristic: The design should speak the users' language. Use words, phrases, and concepts familiar to the user, rather than internal jargon. Follow real-world conventions, making information appear in a natural and logical order

Analysis: No words, phrases, or concepts should feel alien to anyone who is familiar with stealth games. When the tutorial slides are added, they will include easily recognizable terms like alert, searching, key, door, objective, crouch, etc. that anyone with a basic understanding of the English language and/or familiarity with stealth games should be able to easily understand.

Playtester's experience:

Solution:

# Heuristic 3 - User control and freedom #

Heuristic: Users often perform actions by mistake. They need a clearly marked "emergency exit" to leave the unwanted action without having to go through an extended process.

Analysis: There is currently no way to exit the game or reset the level. A pause function and option to reset the level or exit the level/game needs to be added to allow the user freedom to easily try again or quit the game.

Playtester's experience:

Solution:

# Heuristic 4 - Consistency and standards #