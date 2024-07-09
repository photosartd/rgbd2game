# Week 27 (01.07.2024 - 07.07.2024):
## [4D Gaussian Splatting for Real-Time Dynamic Scene Rendering](https://arxiv.org/abs/2310.08528)
### [Video](https://www.youtube.com/watch?v=OBtGcGHLX2I&t=160s)
What I've tried:
1. [Static scene of a room - main camera](../data/video_rgb_stat.mp4) - **works**
2. [Moving scene - main camera](../data/home-moving.mp4) - **works**
3. [Moving scene - start camera](../data/home-stat-start.mp4) - **does not work**
4. [Moving scene - mid camera](../data/home-stat-mid.mp4) - **does not work**
5. [Moving scene - end camera](../data/home-stat-end.mp4) - **does not work**

### How to reproduce
1. Clone [4DGaussian](https://github.com/hustvl/4DGaussians/tree/master) repository and install everything according to README.
2. Train a needed model according to instructions.
3. For rendering, there is a script `render.py` according to README. However, if you need to **render the scene from one
arbitrary view** through all the timestamps $t$, put the script [render_arbitrary.py](../scripts/week27/render_arbitrary.py)
in 4DGaussians repo alongside `render.py` file and use it in the same way:

```python
python render_arbitrary.py --model_path "output/dnerf/bouncingballs/"  --skip_train --configs arguments/dnerf/bouncingballs.py 
```

4. To change the camera view, find the row with `deepcopy(cameras[N])` in `render_arbitrary` script and change `N` to 
needed camera index (not more than the number of frames in the video).

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