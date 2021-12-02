---
Sass file creating
---
# Sass for Beginner to mastered

## Installation 
* First you can install in vsCode extention by typing live Sass Compiler.
you can modify the settings file in Json, edit and give a path to your project : 
```
"liveSassCompile.settings.formats":[
    {
        "format": "expanded",
        "extensionName": ".css",
        "savePath":"/dist/css" 
    }
]
```
when you that, you just have to create a new html file in a folder, go the root and create another folder name it as you want like SCSS, and create a main file with `.scss extention`. 
livecompiler are watching your main.scss file and automaticaly compile to give you a css file create wtith map file. 

## How to use Scss Variable 

in your main file : 
```
$primary-color: #D12424
$primary-color: #D12424
$primary-color: #D12424
$primary-color: #D12424;

//now you can call it like this 

body {
  background : $primary-color;
  font-weight: map-get($font-weights, bold)
}
```
you can compare maps in scss with array in js. like this : 

```
$font-weights:(
  "regular":400
  "medium":500
  "bold": 700
);
```
# nesting in Scss 'nidification'

You can use & to tell css it's a child of. in example when you give a className to some paragraph with a div parent like , .div class myDiv => p class myParagraph.
```
.myDiv {
 width: 80%;
 margin: auto, 0;

 &myParagraph {
   $font-weight: map-get(font-weights, bold);
   
   &:hover {
     color: bleu;
   }
 }
 
}
```
# Partial you Scss to give a good way to maintain you code: 
juste create in you SCSS folder a new file with the name you want starting by underscore: like _reset, _variables, _home, _about etc. In your main file you can call them with **@import './<choose your partial>'**

# function in SCSS 

we can create a function in SCSS just like in JavaScript; 
```
@function weight ($weight-name) {
  @return map-get ($font-weights, $weight-name)
}
font-weight: weight(bold, or medium, or regular)
```

# Use a mixin in Sass

you can create a mixin if you dont want to type and reapeat all the time , css flex et justify etc; 
just do like this 
```
@mixin flexCenter {
  display: flex; 
  justify-content: center;
  align-item: center
}
// in your class you have to include the mixin
//ie in main 
.main {
  @include flexCenter; 

}
// and remember mixin define style
```
another exemple mixin use to define theme

```
@mixin theme ($light-theme:true){
  @if $light-theme {
    background: lighten($primary-color,100%)
    color: darken($text-color; 100%)
  }
}

.light {
  @include theme (light-theme:true/or false)
}
//this create a double theme
```
# Also use mixin to do responsive

in this snippet like a exemple in your main Scss; before that you have to create a variable $mobile: 800px;

```
@mixin mobile{
  @media(max-width, $mobile) {
    @content;
  }
}
// to include this 
@include mobile {
  flex-direction: column;
}

```
So you can create different variable for all type of screen. you got responsive.

## Extend style to another class

use #{&}_nameOfYourParagraph {
  extend
}

## Notes 
To use fontawesome you have to suscribe for free, and load their js for icons.
[fontawesome.com](https://www.fontawesome.com/kits) you can set an account for free, copy and past your kits in your project.
