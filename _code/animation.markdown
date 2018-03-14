---
layout: post
title:  "Animation"
date: 2018-01-09
lang: eng
---
<h2>Animation</h2>
These experiments were made with THREE.js for the rendering course at the University Paul Sabatier in 2017.

<h3>Skeleton</h3>
We handle bones with a custom class even if THREE.js already provides one.

Our requirements for a bone are:
<ol>
	<li>A bone has a sphere of influence and it decreases with the distance</li>
	<li>Hierarchical bones, each one has a parent except the first one</li>
	<li>A vertex can be affected by two bones</li>
	<li>A debug interface should be provided to show area of influence and parent of a bone</li>
</ol>

Finally, a constructor can be called to create our bone. It takes in entry the position, the radius of the sphere of influence, its parent and a color for debug purposes.

Because of the implementation and automation of the computing of the area of influence, if one would want to have a more classical bone API, they would have to create two bones.
The first one would be the kneecap and the second the area of influence at a fixed distance. The simple example Figure 1, uses this hierachy with 3 bones created and two visible in debug.

<figure id="figure1">
	<img src="/Animation/images/bones_example.png" width="65%">
	<figcaption>Figure 1 : Simple example</figcaption>
</figure>

<h3>Rotation matrix and Quaternion</h3>

JavaScript is not really fast, so we immediately move calculation for blending onto the GPU. The code of the shader is exposed in the example at the end of this section.

We implement two way of representing rotations and transaltions, with rotation matrices and with dual quaternions.
Both methods have their advantages and flaws.
A linear blending is then applied with two bones (in our case, up to four could be handled but it generated uneasthetic results).

Rotation matrix blending creates a crushing at the point of rotation.
It is like a folded straw Figure 2, and can be problematic when animating character with large limbs.

<figure id="figure2">
	<img src="/Animation/images/matrix.png" width="35%">
	<figcaption>Figure 2 : Linear interpolation with rotation matrices</figcaption>
</figure>

Dual quaternions blending creates a bulge around the point of rotation as shown on Figure 3.

<figure id="figure3">
	<img src="/Animation/images/quat.png" width="35%">
	<figcaption>Figure 3 : Linear interpolation with dual quaternions</figcaption>
</figure>

One of the main advantage of the duals quaternions linear blending is the handling of wringing.
Whereas for rotation matrices we can spot a thinning of the volume during wringin, there is nothing like it with dual quaternions and the surface naturally roll up around the axis of rotation  as shown in Figure 4.

<figure id="figure4">
	<img src="/Animation/images/dual_torsion.png" width="45%">
	<figcaption>Figure 4 : Comparison of a wringing between our two implementations<br>(Cuboid and cylinder with linear blending of matrices and dual quaternions)</figcaption>
</figure>

All these configurations can be reproduced on the online example : <a href="/Animation/simple.html">Interactive example</a>

<h3>Use case of animating a character with a hierarchical skeleton</h3>

We set up a hierarchical skeleton in order to animate "Marvin" our character. We use the rest position to place and create bones thanks to the debug mode Figure 5.
We can then animate thanks to rotation transformations only so as to not distend the model.

<figure id="figure5">
	<img src="/Animation/images/marvin.png" width="65%">
	<figcaption>Figure 5 : Marvin's skeleton and the resulting animation</figcaption>
</figure>

Animation can be visualized online : <a href="/Animation/marvin.html">Animation of marvin</a>