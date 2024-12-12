# Using NEAT to teach AI to play flappy bird
Implementation of a NEAT (NeuroEvolution of Augmenting Topologies) in famous and beloved mobile game flappy bird. 

Using this algorithm the AI learns to play the game and adaptively improve its performance through evolving neural networks. 

Using NEAT to teach the AI to play the game proved to be more efficient compared to other approaches like Q-learning since it offers advantages like dynamic structures of neural networks, sparse reward handling, no need for a state-action table etc.

Requirements to run the program are specified in `requirements.txt`

# Flappy bird game mechanics
- The bird falls due to gravity, and the player must make it "flap" to stay airborne. It moves continuously forward and must navigate through vertically spaced pipes that appear from the right.

Obstacles:
- Pipes are randomly generated with varying gaps, moving from right to left. The game ends if the bird collides with a pipe or falls to the ground.

Gameplay Objective:
- The goal is to pass through as many pipes as possible. The score increases each time the bird successfully clears a gap, requiring real-time decision-making based on the bird's position, velocity, and the location of obstacles.

Pygame Implementation:
- The game is implemented using the Pygame library, which handles graphics rendering, user input, and the game loop. The loop updates the bird’s position, checks for collisions, and renders the game state.


# How it works
1. The NEAT algorithm begins with a population of 20 randomly generated neural networks (genomes), as defines in the [NEAT] section of `config_file.txt`

2. Fitness Evaluation: Each bird's performance is measured using a fitness function, which increases based on the bird's survival time and how many pipes it successfully passes. For every pipe cleared, a fitness bonus is added.

3. Selection and reproduction: Genomes with higher fitness scores are selected for the next generation. These genomes undergo mutation (e.g., changes in weights, biases, or network structure) and crossover (combination of two genomes) to produce new offspring, as specified in the [DefaultGenome] section.

4. Mutation and evolution: Mutations include adding or removing nodes and connections with probabilities of 0.2 and 0.5, respectively. Connection weights are altered based on predefined mutation rates.
The networks use a feed-forward structure (feed_forward = True), and the default activation function is tanh.

5. Extinction and restart: If all genomes fail to meet the fitness threshold of 100, the population is not reset due to reset_on_extinction = False.

6. Stopping Criterion: The algorithm runs for up to 50 generations or until a bird achieves a fitness score of 100, as specified by the fitness_threshold parameter.

7. Saving the Winner: The genome with the highest fitness score is saved as winner_genome.pkl for later use.

8. AI Demonstration: The saved genome can be loaded by the AI_mode.py script to demonstrate the AI playing the game automatically.

# Demonstration
![flappy-bird_generation-0](https://github.com/user-attachments/assets/eafdccdc-3801-4c95-a782-29f09afc019e)
Program in generation 0

![flappy-bird_generation-2](https://github.com/user-attachments/assets/524b8c9a-b254-4ed0-a63c-13dd7096cff3)
Program in generation 2





