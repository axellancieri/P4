<!-- Therminal and shell -->
The clear program clears output from the terminal screen, moving the prompt up to the top.
By default the Bash shell also supports a keyboard shortcut that does the same thing.
Just hold the "Ctrl" key, and press "l". (That's a lower-case "L".)



<!-- Common Git Commands -->
Starting a repo
git init
Committing files
git add and git commit
git status
git log
Managing committed files
git rm and git mv
git revert
Working with remotes
git clone
git pull
git remote
git push

================================= 
  Button Transitions
====================================

.button {
  opacity: 0;
  transition-property: opacity, background, box-shadow;
  transition-duration: .5s;
  transition-delay: .2s, .3s, 0s;
}
/*
You can also do
transition: <transition-property> <transition-duration> <transition-timing-function> <transition-delay>;
*/
/*
example above with .button

.button {
  opacity: 0;
  transition: opacity .5s ease-out .2s, background .5s ease-out .3s, box-shadow .5s ease-out 0s;
}
*/

.photo-overlay:hover .button {
  opacity: 1;
}

.button:hover {
  background: rgba(74,137,202,1);
  box-shadow: 0 0 0 3px rgba(255, 255, 255, .7);    
}
.btn-icon {
  transition-property: opacity, left;
  transition-duration: .5s;
  transition-delay: .3s;
  transition-timing-function: ease-out;
}
.button:hover .btn-icon {
  opacity: 1;
  left: 80%;
}
====================================
  <!-- Image Transforms & Transitions
 */ -->
img {
  transition: transform .5s;
}
img:hover {
/*  transform: skewX(10deg);*/
    transform: scale(1.5);
  
img {
	transition: transform .5s;
  transform-origin: 0 0; /*Can also state (bottom right) or like 100% 100% (that would be left up given its 100% x and 100% y*/
}
<!-- */
transition-timing-function: cubic-bezier(0.5,3.0,0.5,-2.0); -->
img:hover {
/*	transform: rotate(45deg);*/
  transform: translateX(-150px);
/*  can alos translate like 150px 50px to move the images diagonally, its horizontal first value vertical second*/
}
/*
It's common to use multiple transforms at once.
For example: transform: rotate(-5deg) scale(1.1);

================================= 
  Photo 3D Transforms & Transitions
====================================

.content {
  perspective: 700px;
  perspective-origin: 50% 50%; /*  to change the view angle*. You can use px, right, bottom, etc or %. Keep in mind 0% 0% would be left up and 100% 100% right bottom/
}
.photo {
  transition: transform 1s cubic-bezier(.55, -.62, .27, 1.2);
  transform-style: preserve-3d;
}

.photo:hover {
<!-- /*  transform: rotateY(-180deg); this is previous example, also he stated you can use rotateZthat is, towards and away from the viewer.*/ -->
 transform: rotate3d(1, 0, 0, 180deg);<!-- /*  being x,y,z,degrees*/ -->
}

.side-a,
.side-b {
  backface-visibility: hidden;
}

.side-b {
  transform: rotateX(180deg);

}
<!-- /*

Keep in mind !
3D transformed elements share the same perspective defined in the parent container. Because of this, some elements will have more depth than others, making each transform look different. In this video, we'll apply 3D perspective directly on single elements to make the rotations consistent.

He changed .container class to .photo gallery thats on every picture so you'd see the same perspective on every photo and it would look the same. He had to undo perspective-origin to archieve that too
*/ -->
================================= 
  CUBE CUBE CUBE CUBE
====================================
.cube-container {
	box-shadow: 0 18px 40px 5px rgba(0,0,0,.4);
perspective: 800px; /*  giving it same perspective on every cube to have them behave equally so it looks better*/
}

.photo-cube {
  transition: transform 2s ease-in-out;
  width: 220px;
  height: 200px;
  transform-style: preserve-3d;
}

.photo-cube:hover {
  transform: rotateY(-270deg);
/*  not making it 360 degrees because we want it to stop on the back side not on the front again*/
}
/*He grabbed .photo-cube and did transform: translate3d(100,-50, 50px) and did like a spiral spin outside of the cube place. */

.front,
.back,
.left,
.right {
  width: 100%; 
  height: 100%;
  display: block;
  position: absolute;
}
/*we want to make it 100% the size of the parent width and height*/
/*
since 3 out of the 4 sides are images, we want to set the display to block
*/
/*We could have used a single class he said IDKDKDKOASDOANDOSAIDK*/
.front {
  transform: translateZ(110px);
}
/*Can also use translate 3d, it goes x,y,z. On the above case it'd be transform: translate3d(0,0,100px);*/
.back {
  transform: translateZ(-110px) rotateY(270deg);
  transform-origin: center left;
  
}
.left {
  transform: rotateY(-270deg) translateX(110px);
  transform-origin: top right;
}
.right {
  transform: translateZ(-110px) rotateY(180deg);
}
/*
			<div class="cube-container">
				<div class="photo-cube">

					<img class="front"src="img/photos/1.jpg" alt="">
					<div class="back photo-desc">
					  <h3>Earth from Space</h3>
					  <p>Aenean lacinia bibendum nulla sed consectetur. Fusce dapibus, tellus ac cursus commodo.</p>
						<a href="#" class="button">download</a>
					</div>
					<img class="left" src="img/photos/2.jpg" alt="">
					<img class="right" src="img/photos/3.jpg" alt="">

				</div>
			</div>	
*/
=========================================
//  Color Functions
=========================================

// Variables
$base: #a3acec2;
$base-dar: darken($base, 25%);
$base-light: lighten($base, 25%);

$complement: complement($base);
$complement-light: lighten($complement, 10%);
// Header
header {
  
  h1 {

  }
  p {
    color: $base-dark;
  }
}

// Nav
.main-nav a {
  color: $base-light;
}

// Button
.btn {
  color: $base;
  background-color: $complement;
  &:hover {
    background-color: rgba($complement-light 0.7);
  }
}

======================================
//  Functions
======================================

//@function divide ($a, $b) {
//  @return ($a / $b);
//} That was an example

@function px-to-pc($target, $context: $max-width) {
  @return ($target / $context) * 100%;
}


.test {
  width: px-to-pc(400px);
}
  
  =================================
  
  $base-font-size: 16px;

// Function with px to rem
  
base-font-size: 16px
  
@function px-to-rem($target, $context: $base-font-size) {
  @return ($target / $context) * 1rem;
}
h1 {
  font-size: px-to-rem(60px);
}
    
// WTF function with flex basis
flex: 1 50%, after doign the below he changed that fuction (would be like flex basis) to flex: 1 per-line (2);
  On another media that would fit 3 blocks (above was 2 blocks) he did flex-basis: per-line(3);
== LAYOUT
$max-width: 1000px;
$gutter: 10px;    

@function per-line($items) {
 $g-pct: px-to-pc($gutter) * 2; This to know the marigns of combined far left and right
 $g-total: $items * $g-pct; To know the size of each row or flexline
 @return (100% / $items) - $g-total; to return the basis as the flex basis. We'll return the value to use as the flex basis.
We'll divide the 100% or the total available width by the number of itemes per line then we'll substract the total gutter value
}