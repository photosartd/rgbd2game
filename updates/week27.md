# Week 27 (01.07.2024 - 07.07.2024):
## [4D Gaussian Splatting for Real-Time Dynamic Scene Rendering](https://arxiv.org/abs/2310.08528)
### [Video](https://www.youtube.com/watch?v=OBtGcGHLX2I&t=160s)
What I've tried:
1. [Static scene of a room - main camera](../data/video_rgb_stat.mp4) - **works**
2. [Moving scene - main camera](../data/home-moving.mp4) - **works**
3. [Moving scene - start camera](../data/home-stat-start.mp4) - **does not work**
4. [Moving scene - mid camera](../data/home-stat-mid.mp4) - **does not work**
5. [Moving scene - end camera](../data/home-stat-end.mp4) - **does not work**

### Conclusion
1. Dynamic scenes work (COLMAP can create them)
2. Other camera positions for the current timestamp $t$ except for the main
position do not work. The most plausible explanation - the scene lacks training
data (different views of cameras for consistency). It's possible that they will
work in case we have more views.
3. It does not make sense now to utilize this approach for environment creation
since it lacks consistency between views. Yes, we can extract one Gaussian PC, but
we could as well do it with 3D Gaussian, we do not need a 4D one here.
4. There are almost 0 methods for motion analysis on Gaussians except for those
on usual PCs.