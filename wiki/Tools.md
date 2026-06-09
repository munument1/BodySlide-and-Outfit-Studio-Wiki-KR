## ![Transform Tool](http://i.imgur.com/PiYJAb4.png) Transform Tool (F)
The transform tool allows you to move, rotate and scale meshes in all 3 dimensions. Drag the **arrows to move, the circles to rotate and the cubes to scale** the selected shapes.

[![Transform Tool](http://i.imgur.com/rl3KvqBb.png)](http://i.imgur.com/rl3KvqB.png)

## Move Vertex
The move vertex tool lets you drag a single vertex directly in the viewport.

It works with the tool options shown on the toolbar:

* **Merge Vertex** snaps to a nearby vertex on the same mesh and fills any gap.
* **Weld Vertex** snaps to a nearby vertex while keeping separate UV coordinates.
* **Edge Slide** slides the selected vertex along a connected edge.
* **Restrict To Surface**, **Restrict To Plane**, and **Restrict To Normal** limit how the dragged vertex can move.

When using **Merge Vertex** or **Weld Vertex**, Outfit Studio warns you if the selected points are not on a mesh boundary, because boundary vertices are usually the safer targets.

If you only need numeric single-vertex editing instead of drag editing, press **V** outside the **Colors** tab to open the Move Vertex dialog.

## ![Vertex Selection](http://i.imgur.com/qiGhRPw.png) Vertex Selection (Q)
This mode, like the mask brush, allows you to select and deselect single vertices. Drag the mouse over vertices to **unmask/select** them and hold down the CTRL key to **mask/unselect** them.

[![Vertex Edit](http://i.imgur.com/JUticrPb.png)](http://i.imgur.com/JUticrP.png)

## Mesh Editing
#### ![Collapse Vertex](https://i.imgur.com/xRYZ0kG.png) Collapse Vertex
This tool allows you to click on a mesh vertex to delete. The vertex must have no more than three connections to other vertices. If it has exactly three connections, a triangle is added connecting them, so no hole is created.

Before  
![Before](https://i.imgur.com/pk6gzG4.png)  
After  
![After](https://i.imgur.com/o0vfLx6.png)

Before  
![Before](https://i.imgur.com/AGbioQx.png)  
After  
![After](https://i.imgur.com/EE1Z83T.png)

#### ![Flip Edge](https://i.imgur.com/mS4jfga.png) Flip Edge
This tool allows you to click on a mesh edge to flip. The edge must not be on the boundary of the surface or on a weld. The two triangles to either side of the edge are replaced with two new triangles such that the opposite pair of vertices is connected.

Before  
![Before](https://i.imgur.com/ghQwnKF.png)  
After  
![After](https://i.imgur.com/OiHwAIb.png)

#### ![Split Edge](https://i.imgur.com/HpMM2LL.png) Split Edge
This tool allows you to click on a mesh edge to split in two with a new vertex. Neighboring triangles are also split in two. The new vertex will be at the midpoint of the edge, adjusted for surface curvature.

Before  
![Before](https://i.imgur.com/MpaoHHm.png)  
After  
![After](https://i.imgur.com/v14SWJn.png)

Before  
![Before](https://i.imgur.com/7KHGSKR.png)  
After  
![After](https://i.imgur.com/PascrIx.png)