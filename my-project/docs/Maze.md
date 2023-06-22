# Nic's Maze Help



## Maze Info.
The Maze Code is a program that implements a maze-solving algorithm known as the "Left-hand follower" algorithm. Here's an explanation of the code:

1. The code begins by importing the necessary modules: `maze`, `agent`, and `COLOR` from the `pyamaze` package.

2. Two functions, `RCW()` and `RCCW()`, are defined. These functions rotate the directions based on the current direction. `RCW()` rotates the directions in a clockwise manner, and `RCCW()` rotates them in a counter-clockwise manner.

3. The `moveForward()` function takes a cell coordinate as input and returns the new cell coordinate and the direction the agent is facing after moving forward based on the current direction.

4. The `wallFollower()` function is the main algorithm implementation. It initializes the `direction` dictionary with initial directions ('forward', 'left', 'back', 'right') set to ('N', 'W', 'S', 'E'). It also initializes the `currCell` variable with the bottom-right cell coordinate of the maze.

5. Inside a while loop, the algorithm checks if the current cell is the starting cell (top-left). If it is, the loop breaks.

6. The algorithm then checks if there is no wall on the left side of the current cell. If there is no wall, it further checks if there is no wall in the forward direction. If there is no wall, it calls the `RCW()` function. Otherwise, it moves forward to the next cell by calling the `moveForward()` function and appends the corresponding direction to the `path` string.

7. If there is a wall on the left side, the algorithm calls the `RCCW()` function to rotate the directions in a counter-clockwise manner. It then moves forward and updates the current cell and appends the corresponding direction to the `path` string.

8. After the while loop, the algorithm creates a copy of the `path` string called `path2`. It removes any occurrences of 'EW', 'WE', 'NS', or 'SN' from `path2` using the `replace()` method. This step ensures that the path does not contain unnecessary back-and-forth movements.

9. The `wallFollower()` function returns two paths: `path`, which represents the complete path taken by the left-hand follower algorithm, and `path2`, which represents the simplified path without back-and-forth movements.

10. In the main section of the code, a `maze` object is created with a size of 5x5. The maze is loaded from a CSV file using the `CreateMaze()` method.

11. An `agent` object, `b`, is created to represent the agent in the maze. It is assigned the shape 'arrow' and the color green.

12. The `wallFollower()` function is called with the maze object as an argument, and the returned paths are assigned to `path` and `path2`.

13. The simplified path (`path2`) is traced in the maze using the `tracePath()` method of the maze object, with the agent `b` and `path2` as the input.

14. The `path` string representing the complete path is printed.

15. Finally, the maze is run using the `run()` method of the maze object, which displays the maze with the agent following the path.

Overall, this code implements the "Left-hand follower" algorithm to solve a maze and displays the path taken by the algorithm in the maze visualization.

# Maze
    # The maze Works Well. ScreenShots are on the Document on BlackBoard

## Code Of the Maze

    MAZE Left hand follower 
    from pyamaze import maze,agent,COLOR

    def RCW():
        global direction
        k=list(direction.keys())
        v=list(direction.values())
        v_rotated=[v[-1]]+v[:-1]
        direction=dict(zip(k,v_rotated))

    def RCCW():
        global direction
        k=list(direction.keys())
        v=list(direction.values())
        v_rotated=v[1:]+[v[0]]
        direction=dict(zip(k,v_rotated))

    def moveForward(cell):
        if direction['forward']=='E':
            return (cell[0],cell[1]+1),'E'
        if direction['forward']=='W':
            return (cell[0],cell[1]-1),'W'
        if direction['forward']=='N':
            return (cell[0]-1,cell[1]),'N'
        if direction['forward']=='S':
            return (cell[0]+1,cell[1]),'S'

    def wallFollower(m):
        global direction
        direction={'forward':'N','left':'W','back':'S','right':'E'}
        currCell=(m.rows,m.cols)
        path=''
        while True:
            
            if currCell==(1,1):
                break
            if m.maze_map[currCell][direction['left']]==0:
                if m.maze_map[currCell][direction['forward']]==0:
                    RCW()
                else:
                    currCell,d=moveForward(currCell)
                    path+=d
            else:
                RCCW()
                currCell,d=moveForward(currCell)
                path+=d
        path2=path
        while 'EW' in path2 or 'WE' in path2 or 'NS' in path2 or 'SN' in path2:
            path2=path2.replace('EW','')
            path2=path2.replace('WE','')
            path2=path2.replace('NS','')
            path2=path2.replace('SN','')
        return path,path2
            


    if __name__=='__main__':
        myMaze=maze(5,5)
        myMaze.CreateMaze(loadMaze= "maze--2023-06-12--19-28-11.csv")

        # a=agent(myMaze,shape='arrow',footprints=True)
        b=agent(myMaze,shape='arrow',color=COLOR.green)
        path,path2=wallFollower(myMaze)
        # myMaze.tracePath({a:path})
        myMaze.tracePath({b:path2})

        print(path)
        myMaze.run()




