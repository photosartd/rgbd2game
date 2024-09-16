# Week 37 (09.09.2024 - 15.09.2024):
1. Started working on joining the codebases of [Gaussian Object](https://github.com/GaussianObject/GaussianObject) and
[PARIS](https://github.com/3dlg-hcvc/paris).
2. Encountered some problems:
   1. COLMAP works bad on my usual recorded video (solution: find other method/recording tools like Spectacular Rec or
   MultipleView).
   2. The datasets for articulated objects do not exhibit all the needed files so that we could have a test object at once.
      1. Two real world examples do not have initial point clouds from SfM which are needed for GS.
   3. According to [PARIS Issue](https://github.com/3dlg-hcvc/paris/issues/12) two examples of real world articulated objects
   were constructed manually, aligning their meshes via ICP or similar method.
