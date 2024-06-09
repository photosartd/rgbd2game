# Updates
## Week 23: 03.06.24 - 09.06.24
### Dmitrii
#### Done
1. Looked up the [ParaHome paper](https://jlogkim.github.io/parahome/), installed it, executed
and figured out what's happening in the code. Changed some parts of it to save full 3D
meshes (all parts in one object) of all meshes.
2. Looked up [learning3d repo](https://github.com/vinits5/learning3d), installed it and
[inferenced PointNet model on ModelNet40 dataset](../notebooks/week1_similarity_retrieval.ipynb),
saved embeddings.
3. [Inferenced PointNet on ParaHome objects](../notebooks/week1_similarity_retrieval.ipynb) and 
saved embeddings.
4. Calculated confusion matrix for all object types from ModelNet40 dataset that exist
also as ParaHome objects. 

#### Questions:
1. Do I use PointNet in a right way to extract embeddings (deleting the last layer 
and changing it to nn.Identity?)
2. Why are the results of the confusion matrix so bad?
    - PCs from ModelNet40 look a bit different from those sampled from ParaHome meshes?
3. What's next?
