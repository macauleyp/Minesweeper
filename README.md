# Solving Minesweeper 
This library aims to solve the game Minesweeper as a Constraint Satisfaction Problem (CSP) by developing constraints for each cell observed adjacent to a Minesweeper clue. Furthermore, the library allows for predictive solving by creating a binary tree of potential configurations that satisfy the set of constraints.

# Using the Minesweeper Library
* Installing Package:
	- First clone the repository into some arbitrary root directory. For this example, a directory labeled 'test' will be the root directory for installing the package, and the cloned repository path will be './test/Minesweeper'. 
	- Within the root directory (in this example, 'test') for the repository, execute ```pip install ./Minesweeper```.
		- **Note:** Be sure the ```pip``` version corresponds to Python 3. If not, execute ```pip3 install ./Minesweeper```. Furthermore, it is recommended to use a virtual environment for the package installation. 
	- The package should now be accessible within the virtual environment if the package was configured a virtual environment. 
	
* Example package usuage with filename: test.py
```python
from Minesweeper import MinesweeperSolver
from Minesweeper import MINIMIZE, MineSweeper

driver = MinesweeperSolver(dimensions=16, density=0.4, minimize=MINIMIZE.COST, mode=MineSweeper.PRODUCTION)
driver.run()
	
```
- The following variables are responsible for changing the Minesweeper map configuration along with how the agent attempts to solve the map:

| Variable Name | Type Of Value | Description
|-------------|----------|------------------------------------------------------------------------------------------|
| dimensions | int |  <ul><li>the dimensions for the map </li> <li>**Note:** You must input a value for this within the range 3 <= dimensions <= 256</li></ul> |
| density | float | <ul><li>the mine density for the map</li> <li>**Note:** This input is not required an will default to 0.1, however, if input is provided, it must be within the range 0.01 <= density < 1 otherwise it will default to 0.1</li></ul> |
| density_offset | float | how much to increase the mine density after completion of a trial |
| trials | int | how many trials the agent should conduct |
| subtrials | int | how many sub-trials the agent should conduct at a particular mine density|
| minimize | int | Minesweeper.NONE solves using python random selections, and Minesweeper.COST solves by minimizing cost while Minesweeper.RISK solves by minimizing  RISK |
| copyCacheState | boolean | Saves Agent moves at each step. **Note:** this only shows the agent's move for the last trial conducted|
| mode | int | Use MineSweeper.PRODUCTION for solely seeing the agent's accuracy for solving a map or MineSweeper.PRODUCTION_MAPS to see how the agent's map updates as it solves, or MineSweeper.DEBUG to receive a detailed console log of program execution|
