# Artificial Intelligence Nanodegree
## Introductory Project: Diagonal Sudoku Solver

# Question 1 (Naked Twins)
Q: How do we use constraint propagation to solve the naked twins problem?  
A: When looking for naked twins, we can dramatically reduce our search space with respect to all possible pairs of boxes.
A pair of twins must

* each have exactly $2$ remaining possible values (We could generalize this to higher _multiples_ like triplets, but the search space grows combinatorically)
* be peers of one another

# Question 2 (Diagonal Sudoku)
Q: How do we use constraint propagation to solve the diagonal sudoku problem?  
A: We use constraint propagation analogously to the "simple" sodoku in the exercises:
The two diagonals are simply additional units that we need to consider in the games rules.

We then solve the puzzle by first reducing it as far as possible "deterministically", i.e. by iteratively 
applying Elimination, Only Choice and Naked twins, until the puzzle is solved or no more progress is possible with these techniques.
In the latter case, we start "Search", which (using the search space that has ben drastically constrained by the reduction above) 
tries to make a "guess" in a field that's so far undetermined. After making the guess, we recursively try to solve this smaller puzzle and pop out when we've either found a solution, which then also be valid for the original problem, or determine that the puzzle with the guess is impossible to solve. In the latter case, the value that has been guessed can be eliminated, and we can either continue to reduce the puzzle (new reduction steps might have been made possible by elimination) or proceed searching by making the next guess right away.

Ultimately this results in either a valid solution, or the determination that the puzzle is impossible to solve, if the entire search space has been exhausted.

### Install

This project requires **Python 3**.

We recommend students install [Anaconda](https://www.continuum.io/downloads), a pre-packaged Python distribution that contains all of the necessary libraries and software for this project. 
Please try using the environment we provided in the Anaconda lesson of the Nanodegree.

##### Optional: Pygame

Optionally, you can also install pygame if you want to see your visualization. If you've followed our instructions for setting up our conda environment, you should be all set.

If not, please see how to download pygame [here](http://www.pygame.org/download.shtml).

### Code

* `solution.py` - You'll fill this in as part of your solution.
* `solution_test.py` - Do not modify this. You can test your solution by running `python solution_test.py`.
* `PySudoku.py` - Do not modify this. This is code for visualizing your solution.
* `visualize.py` - Do not modify this. This is code for visualizing your solution.

### Visualizing

To visualize your solution, please only assign values to the values_dict using the ```assign_values``` function provided in solution.py

### Submission
Before submitting your solution to a reviewer, you are required to submit your project to Udacity's Project Assistant, which will provide some initial feedback.  

The setup is simple.  If you have not installed the client tool already, then you may do so with the command `pip install udacity-pa`.  

To submit your code to the project assistant, run `udacity submit` from within the top-level directory of this project.  You will be prompted for a username and password.  If you login using google or facebook, visit [this link](https://project-assistant.udacity.com/auth_tokens/jwt_login for alternate login instructions.

This process will create a zipfile in your top-level directory named sudoku-<id>.zip.  This is the file that you should submit to the Udacity reviews system.

