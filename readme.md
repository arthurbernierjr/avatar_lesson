# [Lets write some CSS](https://codesandbox.io/s/little-tree-x7jnsu?file=/css/style.css) click here for codesandbox

Fork the codesandbox by clicking the `fork` button link and lets begin writing this


### Lets build our animations

The @keyframes CSS at-rule controls the intermediate steps in a CSS animation 
sequence by defining styles for keyframes (or waypoints) along the animation sequence. 
This gives more control over the intermediate steps of the animation sequence than transitions.

Were gonna do some cool stuff with it

``` css
@keyframes moveInLeft {
    0% {
        opacity: 0;
        transform: translateX(-10rem); }
    80% {
        transform: translateX(1rem); }
    100% {
        opacity: 1;
        transform: translate(0); } }

@keyframes moveInRight {
    0% {
        opacity: 0;
        transform: translateX(10rem); }
    80% {
        transform: translateX(-1rem); }
    100% {
        opacity: 1;
        transform: translate(0); } }

@keyframes moveInBottom {
    0% {
        opacity: 0;
        transform: translateY(3rem); }
    100% {
        opacity: 1;
        transform: translate(0); } }

```
## Add some baseline css
This sets the base CSS for the entire page

```css
*,
*::after,
*::before {
    margin: 0;
    padding: 0;
    box-sizing: inherit; }

html {
    font-size: 10px; }

body {
    box-sizing: border-box; 
    font-family: "Lato", sans-serif;
    font-weight: 400;
    line-height: 1.7;
    color: #777;
    padding: 3rem;
}


```
### This will allow us to reset the font and also normalize our styles agianst all browsers




### Lets build our header

The clip-path CSS property creates a clipping region that sets what part of an element should be shown. 
Parts that are inside the region are shown, while those outside are hidden.

The linear-gradient() CSS function creates an image consisting of a progressive transition between two or more colors along a straight line. 
Its result is an object of the <gradient> data type, which is a special kind of <image>.

```css
.header {
    height: 95vh;
    background-image: linear-gradient(to right bottom, rgba(255, 221, 255, 0.8), rgba(153, 50, 204, 0.8));
    background-size: cover;
    background-position: top;
    position: relative;
    -webkit-clip-path: polygon(0% 0%, 100% 100%, 100% 50%, 50% 100%, 0% 50%);
    clip-path: polygon(0% 0%, 100% 0%, 100% 50%, 50% 100%, 0% 50%); }
.header__logo-box {
    position: absolute;
    top: 4rem;
    left: 4rem; }
.header__logo {
    height: 3.5rem; }
.header__text-box {
    position: absolute;
    top: 40%;
    left: 50%;
    transform: translate(-50%, -50%);
    text-align: center; }

.heading-primary {
    color: #fff;
    text-transform: uppercase;
    backface-visibility: hidden;
    margin-bottom: 6rem; }
.heading-primary--main {
    display: block;
    font-size: 6rem;
    font-weight: 400;
    letter-spacing: 3.5rem;
    animation-name: moveInLeft;
    animation-duration: 1s;
    animation-timing-function: ease-out;
 }
.heading-primary--sub {
    display: block;
    font-size: 2rem;
    font-weight: 700;
    letter-spacing: 1.75rem;
    animation: moveInRight 1s ease-out; }

.heading-secondary {
    font-size: 3.5rem;
    text-transform: uppercase;
    font-weight: 700;
    display: inline-block;
    background-image: linear-gradient(to right, #fdf, #9932CC);
    -webkit-background-clip: text;
    color: transparent;
    letter-spacing: .2rem;
    transition: all .2s; }
.heading-secondary:hover {
    transform: skewY(2deg) skewX(15deg) scale(1.1);
    text-shadow: 0.5rem 1rem 2rem rgba(0, 0, 0, 0.2); }

.heading-tertiary {
    font-size: 1.6rem;
    font-weight: 700;
    text-transform: uppercase; }

```

### Lets build our cool button 


```css

.btn {
    text-transform: uppercase;
    text-decoration: none;
    padding: 1.5rem 4rem;
    display: inline-block;
    border-radius: 10rem;
    position: relative;
    font-size: 1.6rem;
    border: none;
    cursor: pointer; }
```

### We also need to set the buttons link and visited state and set a transition property

```css

.btn, .btn:link, .btn:visited {
    text-transform: uppercase;
    text-decoration: none;
    padding: 1.5rem 4rem;
    display: inline-block;
    border-radius: 10rem;
    transition: all .2s;
    position: relative;
    font-size: 1.6rem;
    border: none;
    cursor: pointer; }
```


### We also need the buttons hover state and animation we should divide this up

```css
.btn:hover {
    transform: translateY(-3px);
    box-shadow: 0 1rem 2rem rgba(0, 0, 0, 0.2);
  }
.btn:hover::after {
    transform: scaleX(1.4) scaleY(1.6);
    opacity: 0; }

.btn:active, .btn:focus {
    outline: none;
    transform: translateY(-1px);
    box-shadow: 0 0.5rem 1rem rgba(0, 0, 0, 0.2); }

.btn--white {
    background-color: #ffffff;
    color: #777; }
.btn--white::after {
    background-color: #fff; }

.btn::after {
    content: "";
    display: inline-block;
    height: 100%;
    width: 100%;
    border-radius: 10rem;
    position: absolute;
    top: 0;
    left: 0;
    z-index: -1;
    transition: all .4s; }

.btn--animated {
    animation: moveInBottom .5s ease-out .75s;
    animation-fill-mode: backwards; }

```

### Lets set create the cool nav with the pure css popup using a hidden checkbox

```css
.navigation__checkbox {
    display: none; }

.navigation__button {
    background-color: #fff;
    height: 7rem;
    width: 7rem;
    position: fixed;
    top: 6rem;
    right: 6rem;
    border-radius: 50%;
    z-index: 2000;
    box-shadow: 0 1rem 3rem rgba(0, 0, 0, 0.1);
    text-align: center;
    cursor: pointer; }

.navigation__background {
    height: 6rem;
    width: 6rem;
    border-radius: 50%;
    position: fixed;
    top: 6.5rem;
    right: 6.5rem;
    background-image: radial-gradient(#fdf, #9932CC);
    z-index: 1000;
    transition: transform 0.8s cubic-bezier(0.86, 0, 0.07, 1); }

.navigation__nav {
    height: 100vh;
    position: fixed;
    top: 0;
    left: 0;
    z-index: 1500;
    opacity: 0;
    width: 0;
    transition: all 0.8s cubic-bezier(0.68, -0.55, 0.265, 1.55); }

.navigation__list {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    list-style: none;
    text-align: center;
    width: 100%; }

.navigation__item {
    margin: 1rem; }

.navigation__link:link, .navigation__link:visited {
    display: inline-block;
    font-size: 3rem;
    font-weight: 300;
    padding: 1rem 2rem;
    color: #fff;
    text-decoration: none;
    text-transform: uppercase;
    background-image: linear-gradient(120deg, transparent 0%, transparent 50%, #fff 50%);
    background-size: 220%;
    transition: all .4s; }
.navigation__link:link span, .navigation__link:visited span {
    margin-right: 1.5rem;
    display: inline-block; }

.navigation__link:hover, .navigation__link:active {
    background-position: 100%;
    color: #9400D3;
    transform: translateX(1rem); }

.navigation__checkbox:checked ~ .navigation__background {
    transform: scale(80); }

.navigation__checkbox:checked ~ .navigation__nav {
    opacity: 1;
    width: 100%; }

.navigation__icon {
    position: relative;
    margin-top: 3.5rem; }
.navigation__icon, .navigation__icon::before, .navigation__icon::after {
    width: 3rem;
    height: 2px;
    background-color: #333;
    display: inline-block; }
.navigation__icon::before, .navigation__icon::after {
    content: "";
    position: absolute;
    left: 0;
    transition: all .2s; }
.navigation__icon::before {
    top: -.8rem; }
.navigation__icon::after {
    top: .8rem; }

.navigation__button:hover .navigation__icon::before {
    top: -1rem; }

.navigation__button:hover .navigation__icon::after {
    top: 1rem; }

.navigation__checkbox:checked + .navigation__button .navigation__icon {
    background-color: transparent; }

.navigation__checkbox:checked + .navigation__button .navigation__icon::before {
    top: 0;
    transform: rotate(135deg); }

.navigation__checkbox:checked + .navigation__button .navigation__icon::after {
    top: 0;
    transform: rotate(-135deg); }
    .card-container {
        display: flex;
        flex-wrap: wrap;
    }

```

----------------------------------

References:


[All About Floats](https://css-tricks.com/all-about-floats/)

[Solving Clearfix](https://css-tricks.com/snippets/css/clear-fix/)

[linear gradient](https://developer.mozilla.org/en-US/docs/Web/CSS/linear-gradient)
