---
layout: post
title:  "Real Time Rendering"
date: 2017-10-01
lang: eng
---
<h2>Real Time Rendering Experiments</h2>
These experiments were made with THREE.js for the rendering course at the University Paul Sabatier in 2017.

<h3 id="loop">Loop Subdivision</h3>
<a href="/RTR/loop.html">Watch the result >></a>

This project implements the loop subdivision for triangular based meshes.
Three new points are created on the edges of each triangle at each iteration and old vertices are moved according to there surroundings.

The code is subdivised into four main steps :
<ol>
	<li>Data pre-process</li>
	<ul>
		<li>Creation of data structures for edges which include adjacent faces</li>
		<li>Add adjacent vertices to each vertex</li>
	</ul>
	<li>New points calculation on edges</li>
	<ul>
		<li>12/16 of the new point position come from vertices of the edge</li>
		<li>4/16 come from the opposit vertices of the two adjacentes faces</li>
	</ul>
	<li>Recalculate the new position of already existing vertices</li>
	<ul>
		<li>A weight is assigned to the already existing vertex and to each adjacents vertices with a formula which sum to 1</li>
	</ul>
	<li>New geometry is created</li>
	<ul>
		<li>Four new faces are created per triangle thanks to new vertices previously calculated</li>
	</ul>
</ol>

For example the cube, Figure 1, with the starting meshes.

<figure>
	<img src="/RTR/images/loop_1.png" width="65%">
	<figcaption>Figure 1 : Studied cube with visible wireframe</figcaption>
</figure>

Which gives us after a step of the subdivision, Figure 2, in red the studied triangle, in blue the newly created edges from the new points and in cyan the old triangle.

<figure>
	<img src="/RTR/images/loop_2.png" width="65%">
	<figcaption>Figure 2 : A cube after one step of subdivision</figcaption>
</figure>
The number of step of subdivision can be selected in between 0 to 9. The user can also select another starting geometry and if the wireframe is shown.

For the moment, the coded algorithm does not includes edges special cases so all geometries are closed ones.

<h3 id="implicit">Implicit Surfaces</h3>
<a href="/RTR/implicit.html">Watch the result >></a>

The marching cube algorithm allows the visualization of implicit surfaces.
Actually, they are characterized from a mathematical equation so they cannot be rendered directly to the screen.

The espace is divided into smaller cubes. Here the initial space is a cube of size 1x1x1 which is divied into 12x12x12 smaller cubes.
The sum of the mathematical functions of each implicit surface is calculated for each vertex of the newly divided space. Here three metaballs are present.
This will allow use to deduce which vertices are inside or outside of our threshold.

For each configuration of the vertices of the cube in the inside or outside of our implicit surface, there are 15 possible cases (and their symmetrics), see Figure 3.
The 256 possible cases are stored in a table. This table gives the triangles to draw from the half-edge for each a cube.

<figure>
	<img src="/RTR/images/MarchingCubes.png">
	<figcaption>Figure 3 : The 15 possible cases of the marching cube <br> Source : Wikipedia</figcaption>
</figure>

We calculate a value coded on eight bits from the vertex, this gave us the index to use in this table to gather triangles to draw in the current small cube.

At this point, the results is simple low poly spheres as shown on Figure 4.

<figure>
	<img src="/RTR/images/implicit_1.png" width="65%">
	<figcaption>Figure 4 : Without linear interpolation, the surface is assumed to cut exactly at the half-edge the small cubes and gives a low-poly style to the rendering</figcaption>
</figure>

Value inbetween vertices are lineary interpollated to aproximate the position where the function exceeds our threshold on each edge.

Then we need to store these calculated points to avoid duplicating the vertices and allow calculation of the normal surface. Result is shown in Figure 5.

<figure>
	<img src="/RTR/images/implicit_2.png" width="65%">
	<figcaption>Figure 5 : Final result with 3 metaballs</figcaption>
</figure>

<h3 id="fxaa">Fast Approximated Anti-Aliasing</h3>
<a href="/RTR/fxaa.html">Watch the result >></a>

The FXAA is an algorithm presented by NVIDIA.

The algorithm is emplemented thanks to a shader which use the texture of a first rendering of the scene.
It's really fast as it based on a study of the luminosity of the objects and a brief edge detection, whereas the other anti-aliasing algorithms are based on multiple renderings.

On figure 6 and 7 are shown the different renderings accessible from the example page and the explication in regards to the algorithm.

<figure>
	<img src="/RTR/images/fxaa_1.png">
	<figcaption>Figure 6 : FXAA_DEBUG_PASSTHROUGH, FXAA_DEBUG_HORZVERT, FXAA_DEBUG_PAIR and FXAA_DEBUG_NEGPOS</figcaption>
</figure>

*FXAA_DEBUG_PASSTHROUGH*: selected pixels to be treated are shown in red, these are the ones supposed to be on an adge where the luminosity gradient is important but also where the luminosity is important enough fot he human eye.<br>
*FXAA_DEBUG_HORZVERT*: pixels are sorted between the ones on an horizontal edge in yellow and vertical edge in cyan.<br>
*FXAA_DEBUG_PAIR*: "pair" of pixels are denoted in different color depending on the direction of the half pixel displacement (90° to the edge).<br>
*FXAA_DEBUG_NEGPOS*: shows the direction in which the algorithm extended the most before encountering a bigger gradient of luminosity, thus the end of the current edge (red for negative and blue for positive).

<figure>
	<img src="/RTR/images/fxaa_2.png">
	<figcaption>Figure 7 : FXAA_DEBUG_OFFSET, FXAA_DEBUG_LOWPASS, FXAA and without treatment</figcaption>
</figure>

*FXAA_DEBUG_OFFSET*: mix between FXAA_DEBUG_PAIR and FXAA_DEBUG_NEGPOS.<br>
*FXAA_DEBUG_LOWPASS*: show where the algorithm used a local blur filter to calculate the value of the new value of the pixel in green and the value calculated with the algorithm in red.<br>

<h3 id="ssao">Screen-Space Ambient Occlusion</h3>
<a href="/RTR/ssao.html">Watch the result >></a>

SSAO algorithm uses the depth buffer. After a first render pass we get the rendered scene and its associated depth map.

The algorithm follows three main steps :

<ol>
	<li>Normal map estimation</li>
	<ul>
		<li>Using the depth map it is possible to estimate the surface normal for each pixel of the image</li>
	</ul>
	<li>Taking the normal and depth into account, an hemisphere of 16 points is generated around the studied point</li>
	<ul></ul>
	<li>For each of the generated point, its depth is compared with the one in the depth map</li>
	<ul>
		<li>If it is inferior, then the point is considered obscured</li>
		<li>The difference with the depth map value is also calculated, if it goes over a certain threshold it isn't taken into account to avoid distant objects to occult each other</li>
	</ul>
</ol>

<figure>
	<img src="/RTR/images/ssao.png">
	<figcaption>Figure 8 : Treated rendering, untreated rendering and occlusion map only</figcaption>
</figure>

The algorithm can be completed by applying a gaussian blur to the occlusion map in order to reduce the noise coming from the random sampling.