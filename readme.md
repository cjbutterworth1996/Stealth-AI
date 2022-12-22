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

All of these issues were found by the developer playtesting the game with heuristics in mind. After implementing solutions and improvements to the game, I had another person playtest the game and asked them questions about it while they were playing it. I then adjusted the game once again to fix/improve upon any of the issues they mentioned. These heuristics were taken from Jakob Nielsen's 10 general principles for interaction design. They can be found here: https://www.nngroup.com/articles/ten-usability-heuristics/

# Heuristic 1 - Visibility of system status #

Heuristic: The design should always keep users informed about what is going on, through appropriate feedback within a reasonable amount of time.

Analysis: There is no UI whatsoever, which is quite an issue for determining system status. The only indication the user has to when a guard has spotted them is that the guard faces their direction and starts moving towards them. Possible solutions to this include a symbol above the AI's heads to determine what state they're in, audio cues to alert the player that they've been seen, and UI cues such as the screen turning red to alert the player that they've been seen. Also, there is no win/loss state or objective to follow, so the player will be confused about what to do. To fix this, an objective should be added, UI should be added to show the player what the object is, such as a minimap or an arrow pointing to the objective, or even just a message telling the player what to do. A win state to finish the level and a loss state to restart the level also need to be implemented in order to let the player know they have either succeeded or failed in completing the main objective.

Playtester's experience: The alert system feels very much like an Assassin's Creed game and adequately informs the user about the system status at all times.

Solution: There is now an icon system attached to the enemy characters that shows whether they have seen the player or not. 
A hidden icon is shown above their heads while they have not seen the player. an alert icon is show above their heads when they have seen the player. 

![tutorial-slide-hidden](https://media.github.falmouth.ac.uk/user/748/files/ad02832d-ce2b-4008-8f65-4ea3a454167d)
<p><p align = "center">
  Fig.1 - Hidden Icon
  </p>

![tutorial-slide-alert](https://media.github.falmouth.ac.uk/user/748/files/1d3c0588-8ab5-4f23-8239-2a78c08fbe28)
<p><p align = "center">
  Fig.2 - Alert Icon
  </p>

Once they give up searching for a player, the alert icon switches back to the hidden icon. On top of that, when an enemy sees a player, they let out a shout, letting the player know they've been seen even if they aren't looking at the enemy who has seen them. Win/loss states have been implemented as well. The player must reach the exit door to win, and if an enemy touches a player, they lose. The objective, mechanics, and controls have all been outlined in a tutorial sequence before the game starts. The door also has a green arrow above it to let the player know where it is.

![tutorial-slide-objective](https://media.github.falmouth.ac.uk/user/748/files/08d90d28-c296-4638-858a-bff2c3683d4b)
<p><p align = "center">
  Fig.3 - Objective Door
  </p>

Alert symbol: <a href="https://www.flaticon.com/free-icons/alert" title="alert icons">Alert icons created by Freepik - Flaticon</a>

Hidden symbol: <a href="https://www.flaticon.com/free-icons/user-interface" title="user interface icons">User interface icons created by Febrian Hidayat - Flaticon</a>

Sound effect: <a href ="https://www.unrealengine.com/marketplace/en-US/product/human-vocalizations" title="battle cry sound effect">Battle cry sound effect created by Gamemaster Audio</a>

# Heuristic 2 - Match between system and the real world #

Heuristic: The design should speak the users' language. Use words, phrases, and concepts familiar to the user, rather than internal jargon. Follow real-world conventions, making information appear in a natural and logical order

Analysis: No words, phrases, or concepts should feel alien to anyone who is familiar with stealth games. When the tutorial slides are added, they will include easily recognizable terms like alert, searching, key, door, objective, crouch, etc. that anyone with a basic understanding of the English language and/or familiarity with stealth games should be able to easily understand.

Playtester's experience: The tutorial and terms are all very easy to understand and anyone with a basic understanding of the English language should not have any difficulty understanding it.

Solution: Tutorial slides have been added with easy to understand, familiar terms. Any important terms have been highlighted by being in all caps.

# Heuristic 3 - User control and freedom #

Heuristic: Users often perform actions by mistake. They need a clearly marked "emergency exit" to leave the unwanted action without having to go through an extended process.

Analysis: There is currently no way to exit the game or reset the level. A pause function and option to reset the level or exit the level/game needs to be added to allow the user freedom to easily try again or quit the game.

Playtester's experience: The only way to reset the level is to lose to an enemy. This isn't really an issue, just thought I'd bring it up. The pause menu should be adjusted to return to the main menu and not exit the game though.

Solution: A pause function has been added with options to resume or exit the game. After the playtester's feedback, I adjusted it to have an option to return to the main menu instead of exiting the game. On the loss screen, the player has an option to reset the level without going to the main menu as well as the option to return to the main menu. On the win screen, the player has the option to exit the game or to return to the main menu.

![tutorial-slide-pause](https://media.github.falmouth.ac.uk/user/748/files/3f9674c4-cb01-414b-8be2-c9bcbf01681e)
<p><p align = "center">
  Fig.4 - Pause Menu
  </p>

# Heuristic 4 - Consistency and standards #

Heuristic: Users should not have to wonder whether different words, situations, or actions mean the same thing. Follow platform and industry conventions.

Analysis: There should be no confusion about terminology in the game. The words that will be used in the tutorial slides will be easily recognizable and mean the same thing that they generally mean in real life and in other video games.

Playtester's experience: Same thing as with the second heuristic, everything is easily understandable to basic-level English speakers.

Solution: All tutorial slides have easily understandable terms and key terms are highlighted with all caps.

# Heuristic 5 - Error prevention #

Heuristic: Good error messages are important, but the best designs carefully prevent problems from occurring in the first place. Either eliminate error-prone conditions, or check for them and present users with a confirmation option before they commit to the action.

Analysis: There is no possibility for error because there is currently no objective and no feasible way to escape the game environment. Once an objective is added, the player will only be able to exit the game environment if they complete the objective or quit the game.

Playtester's experience: I could not find any way to break the game. There is no way to leave the level or do anything else that was not intended.

Solution: The player is stuck in a level that is impossible for them to leave without either exiting via a menu, through the objective door, or getting caught by an enemy.

# Heuristic 6 - Recognition rather than recall #

Heuristic: Minimize the user's memory load by making elements, actions, and options visible. The user should not have to remember information from one part of the interface to another. Information required to use the design (e.g. field labels or menu items) should be visible or easily retrievable when needed.

Analysis: There is currently no objective for the user to keep in mind. The user can crouch or prone, but the game does not tell them this. A possible solution is to have the options and the keybindings show in the on-screen UI to remind them they can do these things. Also, when an objective is added, some part of the UI should be easily visible that reminds them what they are supposed to be doing. Additionally, as with the movement controls, a UI element should let the player know they have the option to pause the game and open the pause menu.

Playtester's experience: There is currently no HUD UI overlayed on the player's screen, but a tutorial at the beginning of the game showcased all of the inputs available to the player. This is not an issue as the controls are very simple and easy to remember.

Solution: A tutorial slideshow detailing player inputs was added. No UI was overlayed onto the screen as I felt it would be too cluttered and unnecessary.

# Heuristic 7 - Flexibility and efficiency of use #

Heuristic: Shortcuts — hidden from novice users — may speed up the interaction for the expert user such that the design can cater to both inexperienced and experienced users. Allow users to tailor frequent actions.

Analysis: Right now, there is no customizability withing the game. While the game is a short tech demo with hardly any variability, there is still room for improvement in this aspect. A difficulty mode could be added that adds more guards/obstacles to sneak past, options could be added to skip the tutorial, and options could also be added to hide the UI.

Playtester's experience: There is a rather impressive option to choose difficulty which modifies the number of enemies. Hard mode deletes the user interface entirely. You are also given the option to skip the tutorial. No issues with this heuristic.

Solution: The player now has the ability to skip the tutorial if they don't wish to view it, and they have 3 difficulty levels to choose from. See Fig. 5 for details.

![Difficulty Selection](https://media.github.falmouth.ac.uk/user/748/files/5b3d08db-7d00-469a-b227-3a6acd8e4884)
<p><p align = "center">
  Fig.5 - Difficulty Selection
  </p>

# Heurisitic 8 - Aesthetic and minimalist design #

Heuristic: Interfaces should not contain information that is irrelevant or rarely needed. Every extra unit of information in an interface competes with the relevant units of information and diminishes their relative visibility.

Analysis: There is no UI whatsoever, so technically, this heuristic is being met to a very satisfying degree. This heuristic will need to be re-analyzed via playtesting once the UI is implemented.

Playtester's experience: The UI is as minimal as possible, and if you choose hard difficulty, there is no UI whatsoever.

Solution: The player has the option to choose hard difficulty, which removes the UI entirely. Even playing or normal or easy difficulties though, there is very minimal UI.

# Heuristic 9 - Help users recognize, diagnose, and recover from errors #

Heuristic: Error messages should be expressed in plain language (no error codes), precisely indicate the problem, and constructively suggest a solution.

Analysis: There are no errors that require messages in the game currently. Once an objective is added, a message should pop up if the player tries to complete the objective in an incorrect manner.

Playtester's analysis: There are no error messages, but seeing as how there is no way for the player to actually do something wrong, this is not an issue. The win/loss screens are very easily recognizable and tell the player what happened.

Solution: There are no errors that the player can make. If they get caught by an enemy, they are show a loss screen, telling them they lost. If they reach the objective door, they are shown a win screen, telling them they won.

![loss screen](https://media.github.falmouth.ac.uk/user/748/files/318dfc67-cc5f-4096-8696-f5dfb24b0450)
<p><p align = "center">
  Fig.6 - Loss Screen
  </p>

![Win Screen](https://media.github.falmouth.ac.uk/user/748/files/b648607f-282b-4215-a1ac-09814c231c06)
<p><p align = "center">
  Fig.7 - Win Screen
  </p>

# Heuristic 10 - Help and documentation #

Heuristic: It’s best if the system doesn’t need any additional explanation. However, it may be necessary to provide documentation to help users understand how to complete their tasks.

Analysis: There are no tasks for the user to complete, so there is no need for additional explanation other than to perhaps let the user know that there is nothing they actually have to do. Once an objective is placed in the game, a series of tutorial slides will optionally pop up informing the user the game's controls, objectives, and win/loss states. Also, if a difficulty system is added, the user should be informed why a certain difficulty setting is harder/easier than the others.

Playtester's experience: The difficulty selection clearly states what changes with each difficulty and there is a large, bright green arrow pointing to the exit door. I had no issue understanding any of the UI.

Solution: The objective door is clearly marked with a big, green arrow, and the difficulty selection screen details the differences between each setting.
