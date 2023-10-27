# Multi-agent-path-finding
Step-Wise Depiction
• Path finding for conflict based search for 2 robots.

– The function pathfinding takes four arguments: maze1, maze2, sp1, and
sp2.
maze1 and maze2 are representations of mazes where the robots move.
sp1 and sp2 are lists containing the starting and ending points for two robots,
where each list contains four coordinates (start, intermediate, intermediate,
end).
The function computes the paths for the first robot (Robot i) and the second
robot (Robot j) using the astar algorithm. The computed paths are stored
in p1 and p2.

– The paths are divided into three segments:
p1a, p1b, and p1c represent the path from the start to the first intermediate
point, the path between the intermediate points, and the path from the last
intermediate point to the end for Robot i.
Similarly, p2a, p2b, and p2c represent the path segments for Robot j.

– The complete paths for Robot i and Robot j are then formed by concatenating
these segments.

– The code initializes an empty list conflict to store conflict nodes between
the two robots.

– It checks for conflicts by iterating through the paths of the two robots. When
a common node is found in their paths, it is added to the conflict list. The
loop breaks after finding the first conflict.

– If there is a conflict (i.e., if conflict is not empty), the code modifies maze1
to mark the conflict node as an obstacle for Robot i.

– It then recursively calls the pathfinding function with the modified maze1
to compute new paths for Robot i and Robot j (with the obstacle in place).
The paths without conflicts are stored in previous p1 and previous p2.

– Finally, the function returns the non-conflicting paths for both robots (now
stored in p1 and p2) and the modified maze1 with the obstacle.

• Path finding for conflict based search for 3 robots.

– The function pathfinding Robots takes six arguments: maze1, maze2,
maze3, sp1, sp2, and sp3.

maze1, maze2, and maze3 represent the mazes for R1, R2, and R3, respectively.
sp1, sp2, and sp3 are lists containing the starting and ending points for each
robot, where each list contains four coordinates (start, intermediate, intermediate,
end).

– The function calls the pathfinding function twice to find non-conflicting
paths for R1 and R2. The result is stored in previous p1 and previous p2.

– The non-conflicting paths for R1 and R2 are then extracted from previous p1
and previous p2 and stored in p1 and p2, respectively.

– The function again calls the pathfinding function twice, this time for R3
and R2, and stores the non-conflicting paths in previous p3 and previous p2b.

– The non-conflicting path for R3 with R2 is extracted from previous p3 and
stored in p3.

– Another call to the pathfinding function is made for R3 and R1, storing
the non-conflicting paths in previous p3b and previous p1b.

– The non-conflicting path for R3 with R1 (and R2) is extracted from previous p3b
and stored in p3b.

– The function returns the non-conflicting paths for R1, R2, and R3 (and R2)
as p1, p2, and p3b.

• Node Class: The Node class is a basic representation of a node in A∗ path finding.
Attributes:
– prent: This attribute represents the parent node. It’s used to keep track of
the previous node that leads to the current node in the path.

– location: This attribute represents the location or position associated with
the node in the search space.

– g: This attribute represents the actual cost (or path cost) from the start node
to the current node.

– h: This attribute represents the estimated heuristic cost from the current node
to the goal node.

– f: This attribute represents the total cost, which is the sum of the actual cost
g and the heuristic cost h.

Methods:
– eq : This is a special method in Python used to check if two nodes are
equal. It compares the location attribute of two nodes. If the location of
two nodes is the same, it considers them equal.

• Function for A* algorithm.
– Create two Node instances for the start and end points, initializing their g,
h, and f values to 0. The g value represents the actual cost from the start
node, the h value is the heuristic estimate of the cost to the goal, and the f
value is the sum of g and h.

– Initialize two lists: open list and closed list. The open list contains nodes
that need to be explored, and the closed list contains nodes that have already
been explored.

– Add the start node to the open list.

– Start a loop that continues until there are nodes in the open list to explore.

– In each iteration of the loop: Find the node in the open list with the lowest
f value. This node is the one with the lowest estimated total cost.
Remove the current node from the open list and add it to the closed list.

– Check if the current node is the goal node. If it is, construct and return the
path by backtracking from the goal node to the start node using the prent
links. The path is reversed to get it from start to end.

– If the goal node is not found, generate possible child nodes by considering
adjacent positions (top, right, left, and bottom). Discard positions that are
out of bounds or are not walk-able (maze value is 0).

– For each child node, calculate the g (path cost from the start), h (heuristic
cost to the goal), and f (total cost). If a child node is already in the open list
and has a lower g value, skip it. If a child node is in the closed list, skip it.

– Add the child nodes to the open list for further exploration.

• The main function testing A∗ path finding and Conflict-Based Search (CBS) path
planning algorithms for three robots in a maze. Here’s a breakdown of what the
code does:

– The code defines three maze environments , maze1, maze2, and maze3, to
represent the environments for three robots (R1, R2, and R3). These mazes
contain positions for robots as (1), pickup points as (2), deliver points as (3),
destination points as (4), and obstacles as (0).

– Sets up the starting points for each robot’s path in the sp1, sp2, and sp3 lists.

– Loops through three iterations, one for each robot (R1, R2, R3).

– Inside the loop for each robot: The script specifies the starting and ending
points for the robot’s path (e.g., R1 to P1, P1 to E1, E1 to D1). It calls
the astar function to find and print the paths for each segment of the robot’s
journey.

– After completing A∗ path finding for all three robots, we calculate and print
the total time taken for A∗ path finding algorithm.

– The pathfinding Robots function is called to find non-conflicting paths for
R1, R2, and R3 using CBS. The resultant paths are printed.
