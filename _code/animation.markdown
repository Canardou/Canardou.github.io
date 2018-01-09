---
layout: post
title:  "Animation"
date: 2018-01-09
lang: eng
---
<h2>Animation</h2>
Tous les projets utilisent THREE.js comme librairie pour la gestion de la géométrie et du rendu.

<h3>Squelette</h3>
Comme cela est le but du TP, la gestion du squelette est effectuée à l'aide d'un classe personnalisée de "Bones". En effet il existe déjà une gestion du squelette dans THREE.js.

Nos spécifications sont telles que :
<ol>
	<li>Un os dispose d'une zone d'influence sphérique, son influence décroit avec la distance</li>
	<li>Les os sont organisés selon une hiérarchie, chaque os dispose d'un parent sauf l'os initial</li>
	<li>Un vertex ne peut être influencé par au moins deux os</li>
	<li>Les os doivent disposer d'une interface de débug (affichage de la zone d'influence et du parent)</li>
</ol>

Finalement notre os peut être appelé avec un constructeur assez simple qui prends en entrée une position x,y,z, un rayon d'influence en son centre, son parent et une couleur pour le debug.

On notera que du fait que l'influence est calculée automatiquement, on doit passer par deux structures d'os pour avoir un comportement plus simple d'animation, un premier os sert de rotule tandis qu'un second (enfant du premier) génère l'air d'influence à un certaine distance. Dans la figure 1, on peut voir que l'os en vert n'a pas de zone d'influence dans ce but, il y a 3 os dans cet exemple, le rouge, le vert et le bleu.

<figure id="figure1">
	<img src="/Animation/images/bones_example.png" width="65%">
	<figcaption>Figure 1 : Exemple simple</figcaption>
</figure>

<h3>Matrice de rotation et Quaternion</h3>

Comme JavaScript est plutôt lent, on implémente immédiatement la gestion du blending à l'aide du GPU. Le shader peut être lu dans l'exemple en lien à la fin de cette partie.

Il existe deux façons de représenter les rotations et les translations, par des matrices de rotations 4x4 ou par des duals quaternions. Les deux méthodes ont leurs avantages et leurs défauts. Dans les deux nous mettons en place un linear blending avec au maximum deux os (il est possible d'en avoir plus avec le code fourni mais cela génère des résultats peu esthétiques).

Dans le cas d'une interpolation par matrice de rotation, on peut voir apparaître un écrasement au niveau du point de rotation. Cela donne l'impression qu'on pli une paille (Figure 2) et peut poser problème pour l'animation des membres de personnages un peu épais.

<figure id="figure2">
	<img src="/Animation/images/matrix.png" width="35%">
	<figcaption>Figure 2 : Interpolation linéaire avec matrices de rotations</figcaption>
</figure>

Dans le cas d'une interpolation via les duals quaternions, on voir apparaitre un coude au niveau du point de rotation (Figure 3).

<figure id="figure3">
	<img src="/Animation/images/quat.png" width="35%">
	<figcaption>Figure 3 : Interpolation linéaire avec dual quaternions</figcaption>
</figure>

L'intérêt principal de du linear blending en utilisant des dual quaternions repose sur la gestion de la torsion, en effet alors que pour des matrices de rotation on a un amincissement du volume lors d'une torsion il n'y a rien de tel pour les dual quaternions où la surface s'enroule naturellement autour de l'axe de torsion. (Figure 4)

<figure id="figure4">
	<img src="/Animation/images/dual_torsion.png" width="45%">
	<figcaption>Figure 4 : Différence pour une torsion entre dual linear blending<br>(Pavé avec interpolation de matrices, puis de dual quaternions et Cylindre idem)</figcaption>
</figure>

Toutes ces configurations peuvent être reproduites sur l'exemple en ligne suivant : <a href="/Animation/simple.html">Voir l'exemple interactif</a>

<h3>Exemple d'animation avec un squelette hiérarchique</h3>

On met en place un squelette hiérarchique  pour animer "Marvin" notre cobaye. On utilise pour cela la position "rest" de notre modèle pour choisir la position des bones et leur aire d'influence (Figure 5). On anime ensuite à l'aide de transformation de type rotation seulement pour ne pas distendre le modèle.

<figure id="figure5">
	<img src="/Animation/images/marvin.png" width="65%">
	<figcaption>Figure 5 : Marvin et son squelette et l'animation de marvin</figcaption>
</figure>

L'animation est visible sur l'exemple interactif suivant : <a href="/Animation/marvin.html">Voir Marvin bouger</a>