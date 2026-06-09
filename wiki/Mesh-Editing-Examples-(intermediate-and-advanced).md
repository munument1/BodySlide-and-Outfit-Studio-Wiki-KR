Originally written by sts1skj for Outfit Studio 5.0.7. The example workflows still apply to current releases, but newer versions include additional tools and quality-of-life options around the same mesh-editing workflow.

* [Example 1 (Intermediate): Collapsing a vertex with more than three connections](#example-1-intermediate-collapsing-a-vertex-with-more-than-three-connections)
* [Example 2 (Intermediate): Closing a one-triangle hole](#example-2-intermediate-closing-a-one-triangle-hole)
* [Example 3 (Intermediate): Creating a one-triangle hole](#example-3-intermediate-creating-a-one-triangle-hole)
* [Example 4 (Advanced): Regularizing a mesh to remove texture distortion](#example-4-advanced-regularizing-a-mesh-to-remove-texture-distortion)
* [Example 5 (Advanced): Cutting out a lattice](#example-5-advanced-cutting-out-a-lattice)
* [Example 6 (Advanced): Refining a coarse, low-polygon region](#example-6-advanced-refining-a-coarse-low-polygon-region)
* [Example 7 (Advanced): Restoring a small accidentally-deleted portion of a surface
](#example-7-advanced-restoring-a-small-accidentally-deleted-portion-of-a-surface)
* [Example 8 (Advanced): Smoothing a surface by shortening edges with edge-flipping
](#example-8-advanced-smoothing-a-surface-by-shortening-edges-with-edge-flipping)

***
### Example 1 (Intermediate): Collapsing a vertex with more than three connections
1. Suppose a surface has a vertex that we want to get rid of, and that vertex has four or more connections to other vertices. Consider this vertex from "CBBE Body" from the Skyrim SE mod "Caliente's Beautiful Bodies Enhancer" v1.5.5:

![1](https://i.imgur.com/xqPCgsC.png)

2. We can't use Outfit Studio's collapse-vertex tool on this vertex directly, because that tool only works on vertices with at most three connections. However, we can reduce the number of connections using the flip-edge tool:

![2](https://i.imgur.com/pC26c5H.png)

3. Once there are only three connections left, we can use collapse-vertex to remove it:

![3](https://i.imgur.com/ek23AKT.png)
***
### Example 2 (Intermediate): Closing a one-triangle hole
1. Suppose a surface we're editing is missing a triangle, leaving a hole:

![1](https://i.imgur.com/PpwUpan.png)

2. To close the hole, we need to collapse one of the three vertices at the corners of the hole. To collapse a vertex, it needs to have no more than three connections. Let's suppose we pick the bottom vertex from the image above to collapse. It has six connections. We have to use flip-edge three times to reduce the number of connections to three:

![2](https://i.imgur.com/QaRY0wj.png) ![3](https://i.imgur.com/QbiKosM.png) ![4](https://i.imgur.com/um0msTH.png)

(In the last flip, we flip the edge to the right so that it runs vertically from the top middle vertex in the image to the bottom middle vertex.)

3. Then we can collapse the vertex, which closes the hole.

![5](https://i.imgur.com/u2ja0EY.png)

4. Of course, we've lost a vertex that we didn't want to lose, leaving a messy mesh. A single use of split-edge and then flip-edge cleans it up:

![6](https://i.imgur.com/oSFiox2.png) ![7](https://i.imgur.com/x55ubyQ.png)
***
### Example 3 (Intermediate): Creating a one-triangle hole
1. Suppose we want to punch a one-triangle hole in a surface:

![1](https://i.imgur.com/winsKm6.png)

2. Outfit Studio's "Delete Vertices" command can punch holes in surfaces, but only by deleting a vertex. So we need to add a vertex in the middle of the triangle. Using split-edge twice will do that:

![2](https://i.imgur.com/Rc4XW9a.png) ![3](https://i.imgur.com/425BeGC.png)

3. This leaves us with an extra vertex (in the middle of the rectangle) that we didn't want. We can collapse it after doing one edge flip:

![4](https://i.imgur.com/okNjNf5.png) ![5](https://i.imgur.com/s6p1755.png)

4. Now we just need to delete the new vertex in the middle of the triangle we want to punch out. First mask it using the mask tool (with a very small brush size):

![6](https://i.imgur.com/4aO3RAj.png)

5. Invert the mask:

![7](https://i.imgur.com/0vUvjJG.png)

6. And finally do "Delete Vertices":

![8](https://i.imgur.com/xlnrNx0.png)

***
### Example 4 (Advanced): Regularizing a mesh to remove texture distortion
1. Consider the following textured surface (this is the outfit "Keo - Farm Clothes 3" from the Skyrim SE mod "Keo's Skimpy Outfits - SSE CBBE BodySlide" version 1.4).

![1](https://i.imgur.com/JTUU98N.png)

2. The cloth on the right of the gap looks okay, but the cloth on the left has some ugly texture distortion. Turning on "Show Wireframe" reveals part of the problem:

![2](https://i.imgur.com/S04bxbi.png)

3. On the right, the mesh is regular. On the left, it's not. One way to clean up this texture distortion is to regularize the mesh on the left; then any remaining UV errors should be obvious in the UV editor. First, use collapse-vertex to remove some of the obviously unwanted vertices:

![3](https://i.imgur.com/QlplFqL.png)

4. Next, pick some more vertices to eliminate, and eliminate them. The goal is to end up with just enough vertices for a regular mesh. In the interest of brevity, I'll do as many as I can at once. First, identify the vertices to eliminate:

![4](https://i.imgur.com/1oxbG45.png)

5. Then flip some edges so that some of the vertices to be deleted have only three connections:

![5](https://i.imgur.com/6KFR1yr.png)

6. Collapse them:

![6](https://i.imgur.com/HU5VLyH.png)

7. Flip more edges so that the two remaining vertices to be deleted have only three connections:

![7](https://i.imgur.com/7TsXHq7.png)

8. And collapse them:

![8](https://i.imgur.com/8VjyqOk.png)

9. Now we need to regularize the mesh. First, regularize the triangulation by flipping a few edges:

![9](https://i.imgur.com/CdVDYUE.png)

10. Then use the move tool (with a very small brush size) to move the vertices into a nice grid:

![10](https://i.imgur.com/c1yHwsM.png)

11. Now, in the UV editor, the vertices with bad UV coordinates are obvious:

![11](https://i.imgur.com/25kW5e1.png)

12. Just three vertices need their UV coordinates adjusted:

![12](https://i.imgur.com/3yXqlVN.png)

13. Resulting in a smooth texture on the outfit, at least in this spot:

![13](https://i.imgur.com/ZOcn06M.png)

***
### Example 5 (Advanced): Cutting out a lattice
1. Suppose we want to cut some pieces out of a surface that already has a lattice texture in order to show a little more skin. The example I'll use is "Farm Clothes 1" from the Skyrim SE mod "Caliente's Beautiful Bodies Enhancer" version 1.5.5:

![1](https://i.imgur.com/4NQiOpU.png)

2. The area does not have enough vertices:

![2](https://i.imgur.com/a4pLZrk.png)

3. We need to add enough vertices so we have one for each corner of each hole we want to cut. For now, we'll just add vertices, and worry about positioning them later. Use the split-edge tool to add the desired vertices:

![3](https://i.imgur.com/3u0zgNA.png)

4. Then flip some edges so that we have edges along the boundary of each hole we'll cut:

![4](https://i.imgur.com/gPm5ga9.png)

5. The next two steps can be done in either order: adjusting the space position and UV position of each vertex. I find it easier to adjust the UV coordinates of our new vertices first. In the UV editor, before adjusting:

![5](https://i.imgur.com/fSZrTKo.png)

6. After adjusting the UV coordinates:

![6](https://i.imgur.com/YLJInFY.png)

7. Then we need to adjust the space coordinates of the vertices. Before:

![7](https://i.imgur.com/Kw0VtDn.png)

8. And after:

![8](https://i.imgur.com/dx7o95l.png)

9. Next, we need to cut out our holes. One of them already has a vertex to delete. We add a vertex to the middle of each of the other three holes, by splitting two edges, flipping an edge, and collapsing a vertex for each:

![9](https://i.imgur.com/OQVOGou.png)

10. Then we can mask the four vertices, invert the mask, and delete the vertices:

![10](https://i.imgur.com/QgBNBRp.png)

Of course, more holes would need to be cut to complete the lattice.

***
### Example 6 (Advanced): Refining a coarse, low-polygon region
1. Consider this region of the "Merchant" outfit from the Skyrim SE mod "Caliente's Beautiful Bodies Enhancer" version 1.5.5:

![1](https://i.imgur.com/kTfTBkY.png)

2. It looks okay with all of the sliders set to zero:

![2](https://i.imgur.com/uGQq2sO.png)

3. But it starts to look a bit rough if we set the "AppleCheeks" and "Butt" sliders to 1:

![3](https://i.imgur.com/MSUta8f.png)

4. The problem is that the surface doesn't have enough vertices. We can add more vertices with the split-edge tool. If we use the tool on each diagonal edge, we can double the number of vertices:

![4](https://i.imgur.com/7zYTMqv.png)

5. This may be good enough. To be certain, though, let's split all the horizontal and vertical edges, doubling the number of vertices again:

![5](https://i.imgur.com/2CrLBw7.png)

6. I also flipped a few edges along the top and bottom of the area in order to shorten them.

![6](https://i.imgur.com/TmfN7Yh.png)

7. Now, the split-edge tool does an okay job of generating coordinates and slider diffs for new vertices, but it's far from perfect. Normally, after adding a bunch of vertices like this, you should check to make sure the result is smooth, both with all the sliders set to zero and with each individual slider set to 1. The split-edge tool appears to have done a reasonable job in this case, however, so we'll skip the smoothing step. The result:

![7](https://i.imgur.com/kTowCMA.png)

That's much better.
***
### Example 7 (Advanced): Restoring a small accidentally-deleted portion of a surface
1. Suppose we've accidentally deleted a small piece of a surface and we didn't notice right away, so it's too late to undo the change:

![1](https://i.imgur.com/SI0FuFP.png)

2. It's messy, but we can roughly restore the missing piece. First, move all of the vertices along the edge of the missing piece to where we'd like the new boundary to be, approximately:

![2](https://i.imgur.com/3wS0xLk.png)

3. This gives us more boundary vertices than we want. Flip some edges to reduce the number of connections for each unwanted vertex to three:

![3](https://i.imgur.com/EJWQCDK.png)

4. Then collapse the two unwanted vertices:

![4](https://i.imgur.com/9Tu8fwD.png)

5. Now, our surface is missing three internal vertices. Use the split-edge tool to add them:

![5](https://i.imgur.com/zt0iLd6.png)

6. Then flip some edges to give a regular triangulation again:

![6](https://i.imgur.com/P0jwpOr.png)

7. Now, the UV coordinates are a little messed up:

![7](https://i.imgur.com/LXx9qiO.png)

8. And need to be fixed:

![8](https://i.imgur.com/m44ZJ9c.png)

9. The surface looks okay now, but it could use some smoothing, and the slider diffs may need adjusting. But we'll skip that. The result:

![9](https://i.imgur.com/elMJz2W.png)
***
### Example 8 (Advanced): Smoothing a surface by shortening edges with edge-flipping
1. It's possible for a surface to be too rough even though it has plenty of vertices. One possible cause of this is long, narrow triangles. Consider this portion of "CBBE Body" from the Skyrim SE mod "Caliente's Beautiful Bodies Enhancer" version 1.5.5:

![1](https://i.imgur.com/2pnqIjf.png)

2. It has some long, thin triangles, but it looks okay with all the sliders set to zero:

![2](https://i.imgur.com/8bnoM0I.png)

3. With "AppleCheeks" set to 1, though, it starts to look a bit rough:

![3](https://i.imgur.com/9uInL83.png)

4. We can smooth this area out significantly by just flipping some edges. The goal is for the triangle edges to be as short as possible; the longer they are, the more they can indent the curved surface.

5. Before flipping:

![4](https://i.imgur.com/DaQ7dKX.png)

6. After flipping:

![5](https://i.imgur.com/HMsTvIP.png)

7. The resulting surface is a little bit smoother:

![6](https://i.imgur.com/rpz5CGg.png)