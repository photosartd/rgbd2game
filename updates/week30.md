# Week 30 (22.07.2024 - 29.07.2024):
**Task:** try to analyze motion of Gaussians to detect a cluster that signifies the moving part (door)

**Pipeline ([Notebook](../notebooks/week30/Week30_movement_analysis.ipynb)):**
1. Calculate differences between Gaussians throughout all timesteps
2. Sum them over the window of N (3) timestamps to find big changes in positions
3. Threshold them (by minimum movement) to try to highlight [Gaussians that changed the most in each timeframe](../data/week30/1_unclustered.mp4)
4. Find the moment where the biggest number of Gaussians changed their positions
5. Take these vertices and their positions
6. [Cluster them with DBSCAN](../data/week30/2_problem.mp4) to get 1 cluster of Gaussians for the door

**Problem:**
The main problems in this approach:
1. Too many variables we have to define manually:
   1. `N` - number of timestamps to sum the movements over
   2. `t` - threshold for the minimal movement
2. Movements of Gaussians can be very different for the door (e.g. if it's a revolute joint, the points close to the
axis won't move).
3. Gaussians are bad for clustering: they may be sparse in space (means) and just have big scales of their covariance 
matrix. It means relatively small number of Gaussians can cover a flat surface, which means trying to find the biggest
cluster won't help us.

**Random idea:** try to leverage SAM (2?) to find the Gaussians that contribute to a certain object.
1. Ideally it should be SAM 2 to work with videos
2. Get consistent masks throughout the scene
3. Try to identify the masks for out moving object
4. Backproject the pixels from masks and find only Gaussians that contribute to these pixels (hard)
