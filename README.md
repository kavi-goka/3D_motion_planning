# 3D Motion Planning

**1. Explain Started Code**

The starter code for motion planning provided along with the course is similar to the Backyard Flyer project but it modified in the following ways. 


*A) States and transitions:*

  • The State and transitions of the backyard flyer code: 

    Manaul --> Arming ---> Take-off ---> Waypoints ---> Landing ---> Disarm

  • The States and trasnitions for the motion planning starter code: 

    Manual ---> Arming ---> **Planning** ---> Take-off ---> Waypoints ---> Landing ---> Disarm

   As seen from above, there is an extra state which is the planning which is called right after arming the drone. The line 67 calls the function self.plan_path().


*B) Waypoints:*

  • Backyard Flyer code:
  
  After the drone has reached a specific altitude, the state changes from the Take-off to Waypoint which is in between [line 49 to 53](backyard_flyer-py#L49-L53). The waypoints are hand coded into a function called calculate_box() which is called in [line 51](backyard_flyer-py#L51) and is defined in [line 141](backyard_flyer-py#L141). The state will be in waypoints until there are waypoints left to be reached. 
  
  • Motion Planning Starter code:
  
  After arming, the plan_path() is excuted. Within this function, the grid start is defined in line 139 and tje grid goal is hand coded to add 10 metres in line 143. Bith the start and goal are fed into the A* algorithm along with the defined grid and heuristics. The output path is corrected to waypoints and then the waypoints are sent to the execute. 
 
 
 
 
 
 **2. Modify your code to read the global home location from the first line of the colliders.csv**
 
This was performed in between the [line 127 to 134](motion_planning.py#L127-L134) where we extract the lat and long from the collider.csv sheet. Then, we set it to the home position between [line 136 to 139](motion_planning.py#L136-L139).
 
 
 
 
 **3. Retrieve your current position in geodetic coordinates then convert to local position**
 
global_to_local function was used in line 148 to derive the local positions using the current geodetic coordinates of the drone. 




**4. Define start point as the current local position**

Between line [line 158 to 160](motion_planning.py#L158-L160), the current local position is set as grid start. 




**5. Modify this to be set as some arbitrary position on the grid given any geodetic coordinates**

Initially, the starter code had a harded coded value for the goal. This had to modified in such a way that the goal can be changed to an arbitary value of Long and Lat. Therefore, between [line 208 to 210](motion_planning.py#L208-L210), new arguments have been added which can be used to input the Lat, long and Altitude that is desired. Between the [line 167 to 171](motion_planning.py#L167-L171), the Lat and Long positions are converted into local posiitons using global_to_local(). 




**6. Search algoritm --> A_star with diagonal motion defined**

Once the start, goal are defined, the A* start algorithm will be called from the planning_utils.py code. Here, the started code had only 4 actions defined, which are North, South, East and West movement. In addition to these motions, diagonal movements were added under the class Action() from [line 55](planning_utils.py#L55) and within valid_action() from [line 85](planning_utils.py#L85). The cost of a diagonal movement was specified to be sqrt 2. 

The following picture clearly illustrates the difference between the code with the diagonal movement enabled (Left Path) and without it (Right Path). 
![](/Images/A_star.png)




**7. Cull waypoints**

The waypoints that were derived from the A-Star Algorithm, multiple points which are not necessary such as WP lying on the same line. This can be eliminated by using the collinerity principle. This is done within the planning_util.py code in line 160, where the prune() function defines the points and checks for collinearity according to the function in [line 181](planning_utils.py#L181)

In the following picture, we have on the right side which is the actual path and the left side is the pruned path. 
![](/Images/WP_1.png)





**8. Excuting code**

Below you can see the code working. 

![](/Images/Code_working.gif)
