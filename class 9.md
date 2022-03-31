# Graphics compression
Graphics includes:
1. Create models
2. Reflectance properties of models 
3. Lighting and Rendering
4. Animation

Graphics in multimedia:
1. 2D graphical animation
2. VR
3. AR
4. Combining images/video with graphics
5. 3D compression - Compression of geometry for display and transmission

| Raster Display                                                                              | Vector Display                                                             |
| ------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------- |
| digital images created or captured                                                          | saved as vector statements                                                 |
| saved as grid of x and y coordinates on display space (and for 3D graphics, a z coordinate) | represented by sequence of points to be connected and filled by some color |
| takes a lot more memory                                                                     | takes a lot less memory                                                    |
| fixed resolution once created                                                               | infinite resolution                                                        |
| All graphics ultimatedly converted to raster graphics for display purpose                   | need to be rasterized into an image to be displayed                        |
| operations: compositing, painting, filter effects etc                                       | operations: translation, rotation, zoom-in etc                             |                                                                                                                                                                   |                                                                            |

## Mathematical representation
### Primitives
#### 2D
- points $(x, y)$ vector of points 
- lines
- polygons: vecotr of points and faces

#### Transformation
These are not commutative
1. Translation 
2. Rotation (origin)
3. Scale (origin)
	1. Uniform scaling
	2. Non-uniform scaling 

对于闭合3D图形来说面的数量和点的数量成如下关系

$$\#\ of\ faces = 2\times\#\ of\ vertices$$
所以我们需要 $96n+6nlogn$ bits来表示一个有$n$个顶点的图形。
## Compression
- quantizing vertex positions
- removing redundancy in connectivity information
	- what are redundancies: edges
	- Topological surgery
		- Construct a vertex spanning tree (no cycle in the tree)
			- DFS
			- BFS
			- Evaluate next point by entropy (more flat)
		- Encode vertex spanning tree 
		- Compress vertex positions (use DPCM to store $(dx,dy,dz)$)
		- Encode triangle tree 
		- Compute and compress marching pattern
- do both

## Polyhedral simplification
简化多边形，去掉多边形中的一些点，同时尽量让其形状不变
- Progressive meshes (remove vertex and connectivity one by one)
	- 去掉一条边和边上的两个点，用这两个点的中点代替。根据flatness来决定去除哪条边