### Collin Butterworth's COMP280-A1 Project ###

## Documentation for Worksheet 1 ##
My AI has 5 states in its behaviour tree with sub-states in each of them. The AI is modeled after a typical stealth game AI, and I had a lot of help developing it using this tutorial series on YouTube by Ryan Laley: https://youtube.com/playlist?list=PL4G2bSPE_8un8IplTvVrqPRt7Ey8-3obR

The first and default state that they are in is a patrol state. There are Patrol Point objects placed throughout the environment and stored in an array for the AI to move through. At each patrol point, they rotate to face the attached arrow component, and can be told to wait for a specific amount of time. Additionally, there is a variable wait time setting to randomly adjust the amount of time they wait at said Patrol Point. When they have reached the end of their patrol route, I have added 3 possible behaviours to be used: stay, go back, and loop. If they are told to stay, they will stay at their last Patrol Point. If they are told to go back, they will turn around and go back through their patrol route in reverse order. If they are told to loop, they will move to the first Patrol Point and restart the patrol route.

The second state is a searching state. This is set up so that the AI will not resume their patrol immediately after losing sight of the player, instead, they will move to the player's last known location.

The third state is when they spot the player. They will start chasing the player at an increased speed. Once they lose sight of the player, they will move to the player's last known location, wait 2 seconds, search around in a short distance determined by a task to find a random point within a given radius 3 times waiting 2 seconds at each search point, and then if they still haven't found the player, they move into the "suspicious" state.

The fourth state is the suspicious state. They will search in a very large radius for 10 seconds without waiting at any search point. If they still have not found the player by then, they will enter the fifth state.

The fifth state is the giving up state. They will exit the suspicious state and move back to their patrol route and re-enter the first state.

On top of the behaviour tree for the AI, I have given them walking animations. Likewise, the player also has walking animations. As the player, you can crouch by pressing shift or prone by holding shift. I couldn't find any free assets for the prone animation, but there are crouching animations.