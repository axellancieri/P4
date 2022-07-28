@mixin roundy($dim, $brdr:null) { <!-- Giving border parameter default none to avoid errors -->
  height: $dim;
  width: $dim;
  border: $brdr;
  border-radius: 50%;
}
.img-featured {
  @include roundy(165px, 4px solid $white);
  margin-top: 75px;
  position: relative;
  z-index: 100;
  @media (max-width: $break-xs) {
   display: none;  
  }
}


// Create a flex container
  @mixin flexy(
    $disp: flex,
    $dir: null,
    $wrap: null,
    $just: null) {
    display: $disp;
    flex-direction: $dir;
    flex-wrap: $wrap;
    justify-content: $just;
  }


=====================================
// Media queries
@mixin mq($break) {
   @if $break == 'xs' {
    @media (max-width: $break-xs) {
      @contet;
     }
    } 
              
   @else if $break == 'sm' {
     @media (min-width: $break-s) {
        @contet;
        }
   }
     @else if $break == 'med' {
      @media (min-width: $break-m) {
        @contet;  
        }
   }   
      
   @else if $break == 'lg' {
    @media (min-width: $break-l) {
        @contet;  
        }
     }   
}
    ---

<!-- Following whats below we can see like how it owuld apply on scss code, but above we can leave it altogether -->
  @include mq('lg') {
    width: 45%;
  }
}

    @include flexy($wrap:wrap);
    @include mq ('med') {
     @include center (90%);
  }
}  

-----

//Storing values in maps
<!-- How to recall a map value standalone -->
   @if $break == 'xs' {
    @media (max-width: map-get($breakpoints: 'xs')) {
      @contet;
     }
    } 
<!-- OP or compliated (?) version -->
// Media queries
@mixin mq($break) {
$value: map-get($breakpoints, $break);
$sm: map-get($breakpoints, 'sm');
            
   @if $value < $sm {
    @media (max-width: $value) {
      @contet;
     }
    } 
   @else {
    @media (min-width: $value) {
        @contet;  
        }
     }   
}

======================================
//  Loops
=================

<!-- Bsically look into this if you have something that erpeats itself a lot, sass can make it a lot more easier with @for or @each -->

//@for $i from 1 through 20 {
//  .box-#{$i} {
//    background-color: adjust-hue(tomato, $i * 20);
//  }
//}

$teachers: ('andrew', 'alena', 'joel', 'danielle', 'nick');

@each $teacher in $teachers {
  .teacher-#{$teacher} {
    background-image: url('img/#{$teacher}.jpg')
  }
}

 -- 
// Theme colors
$themes: (
  'ent': #79ccf5,
 'arch': #fd6fa6,
  'edu': #23bbae,
  'sim': #2377bb,
  'soc': #ada3f0,
'games': #3cb144,
  );

   -

 @each $theme, $color in $themes {
  .icn-#{$theme} {
    color: $color;
  }
}

Making the above statement into a mixin to make ot more re usable

// Colors
@mixin themes($map) {
  @each $theme, $color in $map { <!-- Changed that $map that was before $themes-->
      &-#{$theme} {     <!-- Changed the icn to & to make it more reusable -->
    color: $color;
  }
 }            
} 
-
.icn {
  @include themes($themes);
}
--
=============================

// ERROR, WARN 
@if $value == null {
  @error "'#($break)' is not a valid breakpoint name."
}
