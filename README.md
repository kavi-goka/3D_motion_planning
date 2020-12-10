# 3D_motion_planning

**1. Explain Started Code**

The starter code for motion planning provided along with the course is similar to the Backyard Flyer project but it modified in the following ways. 


A) States and transitions:
  • The State and transitions of the backyard flyer code: 

    Manaul --> Arming ---> Take-off ---> Waypoints ---> Landing ---> Disarm

  • The States and trasnitions for the motion planning starter code: 

    Manual ---> Arming ---> *Planning* ---> Take-off ---> Waypoints ---> Landing ---> Disarm

   As seen from above, there is an extra state which is the planning which is called right after arming the drone. The line 67 calls the function self.plan_path().


B) Waypoints:

  • Backyard Flyer code:
  
  After the drone has reached a specific altitude, the state changes from the Take-off to Waypoint which is in between lines 49-53. The waypoints are hand coded into a function called calculate_box() which is called in line 51 and is defined in line 114. The state will be in waypoints until there are waypoints left to be reached. 
  
  • Motion Planning Starter code:
  
  After arming, the plan_path() is excuted. Within this function, the grid start is defined in line 139 and tje grid goal is hand coded to add 10 metres in line 143. Bith the start and goal are fed into the A* algorithm along with the defined grid and heuristics. The output path is corrected to waypoints and then the waypoints are sent to the execute. 
 
 
 **2. Modify your code to read the global home location from the first line of the colliders.csv**
 
 This was performed in between the lines 127 and 134 where we extract the lat and long from the collider.csv sheet. Then, we set it to the home position between line 136 - 139.
 
 
