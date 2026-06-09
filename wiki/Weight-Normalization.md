## Weight Normalization

For skinned meshes in NIFs, the bone weights of every vertex must add up to a factor of 1. In addition, at most four bones may have weights on a single vertex.

In order to guarantee this, when a NIF file is saved, Outfit Studio throws out all but the four strongest bone influences on each vertex and then normalizes the remaining weights so that they add up to exactly 1.

#### Live Normalization
With live normalization on (see "Normalize Weights" checkbox), instead of waiting for you to save the file before normalizing, Outfit Studio normalizes as you paint with the weight paint brush.

![Normalize Weights checkbox](https://i.imgur.com/snrKoJq.png)  

If you increase the weight for a bone on a vertex, weight is taken away from other bones for that vertex. If you decrease the weight, it is added to other bones. Adding weight to other bones that already have some weight is preferred over adding weight to bones that have zero weight.

#### Normalized/locked bones
You can control which bones have weight taken away or added by toggling the "modify during normalization" flag next to the bone.  
![Bone Toggles](https://i.imgur.com/8JW093S.png)

There are two main modes of operation for these flags:
* If no bones have the "modify" flag set, or the only bones with the "modify" flag set are the selected bone and the x-mirror bone, then the "modify" flags are ignored. Weight is added or removed from any other bone during normalization.
* Otherwise, only those bones with the "modify" flag set (not including the selected bone or the x-mirror bone) will have their weights modified during normalization. All other bones are locked.

There are two special cases worth mentioning:
* If the weights are not already normalized (which can happen for some vertices after doing "Copy Weights"), painting with the weight brush will cause Outfit Studio to attempt to normalize weights for all vertices within the brush's radius. This can cause a sudden big change in weights.
* If just one bone has the "modify" flag set other than the selected bone and the x-mirror bone, and that modifiable bone has zero weight for the vertices you're brushing, then the selected bone can only take weight from the x-mirror bone and vice versa. This is handy for equalizing weights on the centerline.