# Nic's Maze Help



## Maze Info.
The Python Maze code is a program that solves mazes using an algorithm called the "Left-hand follower" algorithm. Let's break down how it works:

First, the code imports some necessary modules from a package called "pyamaze." These modules include "maze," "agent," and "COLOR."

Next, two functions are defined: "RCW()" and "RCCW()." These functions are responsible for rotating the directions based on the current direction. "RCW()" rotates the directions in a clockwise manner, while "RCCW()" rotates them counter-clockwise.

The "moveForward()" function takes a cell coordinate as input and determines the new cell coordinate and the direction the agent will be facing after moving forward, based on the current direction.

The main algorithm is implemented in the "wallFollower()" function. It starts by initializing a dictionary called "direction" with the initial directions: 'forward,' 'left,' 'back,' and 'right,' set to 'N,' 'W,' 'S,' and 'E' respectively. Additionally, the variable "currCell" is initialized with the coordinate of the bottom-right cell in the maze.

Inside a while loop, the algorithm checks if the current cell is the starting cell (top-left). If it is, the loop breaks.

The algorithm then checks if there is no wall on the left side of the current cell. If there is no wall, it further checks if there is also no wall in the forward direction. If there is no wall, it calls the "RCW()" function to rotate the directions. Otherwise, it moves forward to the next cell by calling the "moveForward()" function and adds the corresponding direction to the "path" string.

If there is a wall on the left side, the algorithm calls the "RCCW()" function to rotate the directions in a counter-clockwise manner. Then, it moves forward, updates the current cell, and appends the corresponding direction to the "path" string.

After the while loop, a copy of the "path" string is created, named "path2." This copy undergoes some modifications to remove any unnecessary back-and-forth movements by replacing occurrences of 'EW,' 'WE,' 'NS,' or 'SN' with an empty string.

The "wallFollower()" function returns two paths: "path," which represents the complete path taken by the left-hand follower algorithm, and "path2," which represents the simplified path without back-and-forth movements.

In the main section of the code, a maze object with a size of 5x5 is created. The maze is loaded from a CSV file using the "CreateMaze()" method.

An agent object, named "b," is created to represent the agent in the maze. It is assigned the shape 'arrow' and the color green.

The "wallFollower()" function is called with the maze object as an argument, and the returned paths are assigned to "path" and "path2."

The simplified path, "path2," is then traced in the maze using the "tracePath()" method of the maze object. The agent "b" follows the path represented by "path2."

The complete path, "path," is printed.

Finally, the maze is run using the "run()" method of the maze object, which displays the maze with the agent following the path.

In summary, this code utilizes the "Left-hand follower" algorithm to solve mazes. It calculates a path through the maze and provides both the complete path and a simplified version of the path without unnecessary back-and-forth movements. The maze and the agent's path are visualized for easy understanding.

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

        a=agent(myMaze,shape='arrow',footprints=True)
        b=agent(myMaze,shape='arrow',color=COLOR.green)
        path,path2=wallFollower(myMaze)
        myMaze.tracePath({a:path})
        myMaze.tracePath({b:path2})

        print(path)
        myMaze.run()




