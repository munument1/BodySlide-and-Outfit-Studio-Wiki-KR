Functionality for merging geometry (shapes) can be found under the "Shape -> Merge Geometry..." menu in Outfit Studio.

The following dialog will open where you will need to choose two shapes for merging:

![Merge Geometry](http://i.imgur.com/Ial2p4g.png)

There are a couple of things that need to match up on the source and target shapes for merging to work. Essentially, you can only merge shapes that are set up in a similar way and use the same shader/texture to prevent any unwanted results. Any mismatches will be displayed in the dialog for you.

**Potential situations that will prevent merging include:**
* Target shape must be different from source source.
* Partitions do not match. Make sure the amount of partitions and their slots match up.
* Segments do not match. Make sure the amount of segments, sub segments and their info as well as the segmentation file match.
* Resulting shape would have too many vertices.
* Resulting shape would have too many triangles.
* Shaders do not match. Make sure both shapes either have or don't have a shader and their shader type matches.
* Base texture doesn't match. Make sure both shapes have the same base/diffuse texture path.
* Alpha property mismatch. Make sure both shapes either have or don't have an alpha property and their flags + threshold match.

**Delete source shape:**  
By default the source shape will be deleted after the merge, but there is an option to keep it. By keeping the source shape, you will receive a shape with both of their geometry merged but also still have the original left to work with.