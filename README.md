#Logo Presenter#
A customizable template for presenting logo options. Display logos in a scrolling gallery with an option to reverse the color scheme.

##Demos##

<a href="http://drewbot.github.io/my-internship-journal/">MIJ</a>

<a href="http://drewbot.github.io/auto-junction-logo/">Auto Junction</a>

<a href="http://drewbot.github.io/time-2-track/">Time 2 Track</a>

##Installation##

```
$ git clone git@github.com:drewbot/logo-presenter.git
$ npm install
$ bower update
```
Remove "git" and "gitattributes".

##Use##

####HTML####
There are three sections already in place. Each section represents an option.

To add aditional options simply copy and paste a section and update the section id and class to the next index, then update main.js as noted below.

**index.html**

```
<section id="option-4" class="option-4">
  ...
</section>
``` 
Note that by default #option-3 has the button.move-down text set to "back to top" because it is the last option when there are only 3 available. When adding new options make sure that the last option has the "back to top" text and all others say "next option".

All of the other code within the section is boilerplate. The real action is happening in CSS and JS. 

####CSS####
All logo option images, their reversed color scheme counterparts and background colors are established within main.scss.

Within main.scss:

 - Replace the color mixins for each "configuresection( )" instance (background color, button color). 
 - Then replace the background url's within .inner-wrapper

**main.scss**

```
///////////////////////////////// Option 1
.option-1 {
    @include configuresection($red, $white);
    .inner-wrapper {
        margin: 0 auto;
        width: 500px;
        height: 500px;
        background: url("../images/logo-option-1-color.png");
    }
}

.option-1-reverse {
    @include configuresection($white, $red);
    .inner-wrapper {
        margin: 0 auto;
        width: 500px;
        height: 500px;
        background: url("../images/logo-option-1-white.png");
    }
}
```
In the example above .option-1 is the first option you would see when arriving to the site.

.option-1-reverse is the same logo but with the color scheme reversed and the appropriate image being loaded.

When saving images I recommend sticking with a similar naming convention for ease of replacement or additional options.

####JS####
Within main.js there is a click function for each option that reverses the color scheme by toggling the class on that section

**main.js***

```
$('.option-1 .reverse').click(function(){
   $('.option-1').toggleClass('option-1-reverse');
})
```
When adding new options be sure to copy and paste this click function and replace the number in the class names to match the index of the option added.

Also, you will see the configuration for the onepage_scroll( ) method which is available via the onepage-scroll js plugin. See documentation <a href="https://github.com/peachananr/onepage-scroll">here</a>. This provides the single-scroll pagination and moveDown( ) functionality to the pagination buttons. 




