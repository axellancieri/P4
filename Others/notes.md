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

<!-- ================================= 
  Button Transitions
==================================== -->

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
  <!-- Image Transforms & Transitions
==================================== */ -->
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
