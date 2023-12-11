# AI-models-
**SnakeReinforcementLearningGame
**

steps by step how this game is being implemented and a documentation for the code that is attached to this project. 

we start up by setting up the enviroment for this game:
1. that holds the first step tp define the steps adn the directions that the snake will seek and will need to follow
2. define a class which will hold all the functions that needed to be implmented to define the movements of the snake and the goal that it seeks for and the score that needs to be updated
3. -------------------------------------------------
4. the functions as follows:
5. __init__ which intiates the game and define the size of the frame that we have.
6. reset() which defines that that when teh snake collides to the wall or to itslef it requires to run this function in order to start the game all from the beggining
7. placefood() which defines placing the different colored point as on the frame and set it as a target for the snake adn it would be really imporatnt in teh process of learning teh agent as it is defined as the goal that we have which would define of whether the snake did something rigth to receive a reward or something wrong to receive a punshiment.
8. isCollison() which defines all cases of collssion that the snake can have, either a collison with the target ball itself so with respect the score needs to be increased as a sort of reward, a collssion with itself which means that game over is true and that the game needs to be restarted again, and finally that the snake has collided with tha wall itself which means that also it is a game over and the agent receives a score of negative because of doing something worng in order to learn out it as a sort of trainig.
9. movesnake() which defines the movement of snake itself through out decreasing from the dimensions of the blocksize defined at the beggining in the direction where the snake does move now.
10. ------------------------------------------------
11. now we can create our own model (neural network)
12. using the nn model as an import in order to be able to create our neural network
13. having 3 different network layers, first as an input, second as a hidden layer, and third as an output.
14. ------------------------------------------------
15. then building up the trainer that will process the process of training the model that we have and side from that calculating the loss function that will boost up the process of the trainging and will make it much faster in order for the network to improve the performance of the model that we have.
16. ------------------------------------------------
17. defining the agent that will be used for learning the game the basics of the game and be able after training it well to master the game after relying on the rewards that it will receive and will it does react to it.
18. define the states that the snake can pass through with, sucha as the dange states which defines where the snake would collide and that would lead to "game over" to occur
19. define where the food is fromteh directions using a comparison of the head the snake is and the random comparison food position is.
20. define a remember function which defines a collecting for all the meomery needed and append it all together
21. deifne both a short meomery and long meomery as In trainLongMemory, the code checks if the length of self.memory is less than BATCH_SIZE. If it is, the whole memory is used as a sample for training. Otherwise, it randomly samples BATCH_SIZE experiences from self.memory. Then, it separates the sampled experiences into separate lists of states, actions, rewards, next states, and done flags and uses self.trainner.trainStep() to train the model with these samples.Morever, short-term memory often corresponds to a small buffer that stores recent experiences for immediate learning that is why it is really crucial to have both in order to maintain a good learning process.
22. ------------------------------------------------
23. Last thing is to start the trainign process and define the epochs which outlines the number of games that the model will require in order to master the game technique eventually



More about the principal behind the game adn how reinforcement does work:
-------------------------------------------------------------------------
The concept behind Reinforcement Learning (RL) is easy to grasp. An agent learns by interacting with an environment. The agent chooses an action, and receives feedback from the environment in the form of states (or observations) and rewards. This cycle continues forever or until the agent ends in a terminal state.The goal of the agent is to maximize the sum of the rewards during an episode. In the beginning of the learning phase the agent explores a lot: it tries different actions in the same state. It needs this information to find the best actions possible for the states. When the learning continues, exploration decreases. Instead, the agent will exploit his moves: this means he will choose the action that maximizes the reward, based on his experience.

In the Snake game, our goal is to control a serpent that has an unusual penchant for consuming apples. Whenever the snake successfully devours an apple, it not only receives a reward but also elongates its body. Maneuvering through the playing field, the snake roams freely, but its freedom comes to an abrupt halt upon collision with walls or its own body. Our control over the snake is limited to four directional actions: moving up, down, left, or right.

Now, the challenge lies in teaching a neural network to navigate this game efficiently. We rely on visual information extracted from the game's snapshots to determine the best action to take—essentially transforming this into a classical classification problem for the neural network to solve.

To conform to the recommended reward scale of -1 to 1, I've set the reward mechanism as follows: a reward of 1 is granted when the snake manages to capture an apple, -1 is given when the snake meets its unfortunate demise, and 0 signifies no notable event. This reward structure serves as the backbone for the agent to learn and refine its gameplay strategy based on the received rewards.

However, a potential stumbling block emerges when the agent gets trapped in a local minimum—a scenario where the snake continuously circles the central area, anticipating a higher probability of apple appearances there. To counteract this behavior, we need to incentivize actions that benefit the agent in the long term, not just in the immediate moment. By encouraging the agent to prioritize actions that lead to sustained success rather than immediate gains, we aim to steer clear of these local minimum traps and guide the agent towards more strategic and adaptive gameplay







