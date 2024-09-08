# Week 34 (02.09.2024 - 08.09.2024):
## Plan
1. Record a dynamic video from (first person view) how we go through a room, interact with easy objects ([laptop](../data/week36/recordings), microwave) in a specified predefined way (give a view from different cameras for the first state; interact with the object; give a view from different cameras for the second state)
2. Use hand detection or other tools to automatically detect interaction.
3. Use SAM2 to create masks of the interacted object
4. Use PARIS-like method to recreate articulated objects from sets of multi-view images

After this, I see 2 ways to proceed:
1. Either try to use extracted articulated object mesh and try to track/match it with the one in our video to then add a loss in 4DGS (object matching loss). With this we will try to handle the problem of 4DGS at least locally, so that the representations of articulated objects via splats converge better.
2. Somehow try to assess positions of this recreated articulated meshes in the same environment (maybe tracking will also be helpful here), replace original meshes of these objects (e.g. from 3DGS or Sugar) with new articulated objects and place them in this environment
