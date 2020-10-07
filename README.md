# Map-Generation
Four types of gridworld maps are used in this research to model different subterranean environments in simulation: cave, urban, tunnel, and hybrid, a combination of the three.  Examples of these maps are shown in Figure 1.  The maps used for map prediction and sensor coverage were generated based on John Conway's Game of Life [1], a famous cellular automaton which applies four rules to all gridworld cells.  For map generation, these rules were simplified to be:

1. A living cell with less than *death limit* living neighbors dies.
2. A living cell with greater than or equal to *death limit* living neighbors lives.
3. A dead cell with greater than *birth limit* living neighbors becomes alive.
4. A dead cell with less than or equal to *birth limit* living neighbors dies.

The *death limit* and *birth limit* parameters are changed based on the type of map generated.  The maps used in this research are two-dimensional boolean arrays where false (alive) is represented by a black cell, meaning the cell is occupied and cannot be traversed, and true (dead) is represented by a white cell, meaning the cell is free and can be traversed.  When initializing the map, we randomly set each cell to be dead or alive with the percent chance of being alive changed based on the different environment maps discussed.  We calculate the new cell value for each cell based on the values of its eight neighbors and our simplified rules of The Game of Life and put the resultant value into its corresponding position in a new grid, so that the new values do not affect the old.  We repeat this process on each updated grid for the user defined number of steps, in our case three.  Figure 2 demonstrates the map changing over these steps to become a map with the same properties as one of the cave maps we used for simulation testing.

![maps](/4maps.png)<br/>
*Fig. 1: The four types of maps used for simulation testing.*

![maps](/buildmap.png)
*Fig. 2: From left to right, we see the map improved with iterations based upon The Game of Life to produce a cave-like map.  The last map on the right is the final map used for testing with all islands of free cells not neighboring the main free cave cells removed to allow traversal among all free cells.*
