# Self-Driving Car AI
This repository contains the code for a self-driving car AI implemented using Deep Q-Learning. The AI learns to navigate a simulated environment by training a neural network to make driving decisions based on sensory input.

## Features
* Self-driving car AI powered by Deep Q-Learning
* Neural network architecture for decision making
* Experience replay mechanism for efficient training
* Implementation of the Deep Q Learning algorithm
* Saving and loading of AI model checkpoints
## Code Structure
The repository consists of two main code files:

## ai.py: 
This file contains the implementation of the self-driving car AI. It defines the neural network architecture, the experience replay mechanism, and the Deep Q Learning algorithm. The AI learns to select actions based on the current state, and it updates its internal state based on the received rewards and signals from the environment.

The AI learns to navigate a simulated environment by training a neural network to make driving decisions based on sensory input.

### Libraries
* numpy: A library for numerical computing in Python.
* random: Provides functions for generating random numbers.
* os: Allows interaction with the operating system.
* torch: The main library for deep learning in Python.
* torch.nn: Contains neural network-related classes and functions.
* torch.nn.functional: Provides various activation functions and loss functions.
* torch.optim: Contains optimization algorithms for training neural networks.
* torch.autograd: Implements automatic differentiation for calculating gradients.
* torch.autograd.Variable: Wraps a tensor and records operations on it for automatic differentiation.
### Network
* Network class: Defines the architecture of the neural network used by the AI. It consists of two fully connected layers with ReLU activation.
### Experience Replay
* ReplayMemory class: Implements the experience replay mechanism for storing and sampling past experiences. It uses a cyclic buffer to store events and samples a batch of events for training the neural network.
### Deep Q Learning
* Dqn class: Implements the Deep Q Learning algorithm. It initializes the AI with a neural network, replay memory, and optimizer. It keeps track of the last state, action, and reward. It provides methods for selecting actions, learning from experiences, and updating the AI's internal state.
### Methods
* select_action: Selects an action based on the current state using the softmax function applied to the Q-values output by the neural network.
* learn: Performs a Q-learning update using a batch of experiences. It calculates the TD error and updates the neural network's weights using the Adam optimizer.
* update: Updates the AI's internal state with the current reward and signal from the environment. It stores the previous state, action, and reward in the replay memory and performs a learning step if enough experiences have been accumulated.
* score: Computes the average score over the last 100 rewards, indicating the AI's performance.
* save: Saves the current state of the AI (neural network and optimizer) to a file.
* load: Loads the last saved state of the AI from a file, if available.
#### Usage
The code is structured as a Python script that can be executed directly. It creates an instance of the Dqn class, which represents the AI agent, and runs a simulation of the self-driving car. The AI learns and makes decisions based on the input from the environment.

The AI's performance is measured using the average reward over a sliding window of the last 100 rewards. The current state of the AI can be saved and loaded using the save and load methods.

#### Note
This code assumes the existence of a trained model file, last_brain.pth, in the same directory. If the file doesn't exist, the AI will start from scratch and learn from scratch.



## map.py: 
This file represents the simulated environment in which the self-driving car AI operates. It provides methods for interacting with the environment, such as receiving sensory input, applying actions, and providing rewards.

The car uses a neural network (represented by the Dqn class in ai.py) to make decisions and navigate a map filled with sand.

### Libraries
The code begins by importing the necessary libraries:

* numpy for numerical computations.
* matplotlib.pyplot for plotting graphs.
* Kivy libraries for building the user interface and game elements.
* The Dqn class from ai.py for the artificial intelligence component.
### Global Variables
Next, some global variables are defined:

* last_x and last_y to keep track of the last point on the map where sand was drawn.
* n_points to store the number of sand points on the map.
* length to store the length of the sand track on the map.
* brain is an instance of the Dqn class, representing the artificial intelligence brain of the car.
* action2rotation is a list that maps actions to rotations for the car.
* last_reward stores the reward from the last action taken by the car.
* scores is a list to store the scores achieved by the car during training.
* first_update is a boolean variable used to initialize the map.
### Initialization Function
The init function initializes the map by setting the sand array, goal position, and first_update flag.

### Car Class
The Car class represents the car in the simulation. It inherits from the Widget class provided by Kivy and defines properties such as angle, rotation, velocity, sensors, and signals. The move method updates the position and rotation of the car based on the given rotation value. It also updates the sensor positions and calculates the corresponding signals based on the sand array.

### Ball Classes
The Ball1, Ball2, and Ball3 classes are simple classes that represent the sensor balls displayed on the screen.

### Game Class
The Game class represents the game environment and inherits from the Widget class. It contains instances of the car and sensor ball classes. The serve_car method initializes the car's position and velocity. The update method is called periodically and performs the main logic of the game. It updates the environment variables, calculates the car's orientation, and calls the brain.update method to update the AI. It also handles collisions with sand and the goal, updating the reward accordingly.

### Painting Tools
The MyPaintWidget class represents the drawing area where the user can draw sand on the map using touch events. The on_touch_down and on_touch_move methods handle the touch events and update the sand array accordingly.

### API Buttons
The CarApp class is the main application class that inherits from the App class provided by Kivy. It builds the game interface, sets up the update interval, and defines methods for clearing the canvas, saving the AI model, and loading a saved model.

### Main Execution
The code checks if it is being executed directly and then creates an instance of the CarApp class and runs the application.


## Usage
To use the self-driving car AI, follow these steps:

1. Clone the repository:

2. Install the required dependencies. Make sure you have Python and PyTorch installed.

3. Open a terminal or command prompt and navigate to the project directory:

4. Run the map.py script:

    python map.py

The AI will start training and navigating the environment. You can monitor its performance through the displayed reward scores.

## Saving and Loading Model Checkpoints
The AI model can be saved and loaded to resume training or use a trained model. The model checkpoints are saved in the form of a .pth file. The following methods are available:

* save: Saves the current state of the AI (neural network and optimizer) to a file named last_brain.pth.

* load: Loads the last saved state of the AI from the last_brain.pth file, if it exists.

## Contributing
This script is written for the educational purposes. Contributions to this self-driving car AI project are welcome. If you find any issues or have suggestions for improvements, please open an issue or submit a pull request.

## License
This project is licensed under the MIT License. Feel free to use, modify, and distribute the code as needed.

## Acknowledgements
This self-driving car AI project is inspired by the work of researchers and developers in the field of autonomous vehicles. Special thanks to the PyTorch community for providing the deep learning framework. This work is for the educational puprposes and does not intend for commercial use. 

## References
Mnih, V., Kavukcuoglu, K., Silver, D., Rusu, A. A., Veness, J., Bellemare, M. G., ... & Petersen, S. (2015). Human-level control through deep reinforcement learning. Nature, 518(7540), 529-533.