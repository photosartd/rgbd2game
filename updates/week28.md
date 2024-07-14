# Week 28 (08.07.2024 - 14.07.2024):
## [4D Gaussian Splatting for Real-Time Dynamic Scene Rendering](https://arxiv.org/abs/2310.08528)
1. By default the [export_perframe_3DGS.py](https://github.com/hustvl/4DGaussians/blob/master/export_perframe_3DGS.py) 
script exports only test Gaussians (those where `camera_idx % 8 == 0`, so each 8th). To analyze we rather need 
sequentially exported Gaussians.
2. After the export, I looked at one of the timestamps' Gaussians in Blender and chose a subset of Gaussians that are
supposed to be at the place of the dishwasher in video:
![Dishwasher in video](assets/week28/dishwasher_in_video.png)
![Gaussians' positions](assets/week28/blender_gaussians_positions.png)
![Gaussians' positions 2](assets/week28/blender_gaussians_positions2.png)
3. I exported the [vertices indices](../data/week28/gaussian_vertices.txt) to look at their color/position changes in python.
4. I measures the mean + std changes in the positions of these Gaussians and found several peaks which correspond
to the most seemable changes in the dishwashers Gaussians in the video:

![Positions changes](assets/week28/positions_changes.png)

Here are **corresponding frames (30, 46, 52, 98, 139, 177)**:
![30](../data/home-stat-end-frames/frame_0030.png)
![46](../data/home-stat-end-frames/frame_0046.png)
![52](../data/home-stat-end-frames/frame_0052.png)
![98](../data/home-stat-end-frames/frame_0098.png)
![139](../data/home-stat-end-frames/frame_0139.png)
![177](../data/home-stat-end-frames/frame_0177.png)

5. So we can see that the changes in positions do really correspond to the changes in the video.
6. Colors of the Gaussians did not show any changes through all the timestamps:
![Colors changes](assets/week28/colors_changes.png)

Code with analysis can be found [here](../data/week28/Week28%20Gaussians%20flickering.ipynb)

### Conclusion
Actually this behaviour could be already predicted if I did not forget that the network actually just predicts ONLY 
Gaussian's **position, rotation and scaling.** Colors must be already fixed in 3DGS training step:
![4DGS](assets/week28/4dgs.png)


## [2D Gaussian splatting for Geometrically Accurate Radiance Fields](https://github.com/hbb1/2d-gaussian-splatting/tree/main)
Results for the static home scene:
1. [Colored home static scene](../data/week28/render_traj_color.mp4)
2. [Depth home static scene](../data/week28/render_traj_depth.mp4)
3. ![Screenshot of the .ply model in Blender](assets/week28/blender.png)

### Conclusion
1. Consistency is bad for the views that were not presented in the video.
2. A lot of flickering and empty space
3. For some reason the .ply model is not consistent with what I get in the videos at all.
