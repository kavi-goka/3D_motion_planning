# 3D_motion_planning

*1. Explain Started Code*

The starter code for motion planning provided along with the course is similar to the Backyard Flyer project but it modified in the following ways. 

• The State and transitions of the backyard flyer code: 

Manaul --> Arming ---> Take-off ---> Waypoints ---> Landing ---> Disarm

• The States and trasnitions for the motion planning starter code: 

Manual ---> Arming ---> *Planning* ---> Waypoints ---> Landing ---> Disarm

As seen from above, there is an extra state which is the planning which is called right after arming the drone. The line 69 calls the function self.plan_path().


