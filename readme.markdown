# PlusSlider jQuery Plugin

A jQuery content slider that is easily configurable and can easily be switched between 'fading' and 'sliding'

## Features
* Slides are _HTML_ (_Can be images or text_)
* Multiple sliders per page
* API for developers
* Very _simple_ &amp; _valid markup_
* AutoPlay (_Optional_)
* **Next/Previous** Navigation (_Optional_)
* Titled, numbered or thumbnail **paginated** navigation (_Optional_)
* Various callbacks
* Tested on *IE 6+* and *modern browsers*

## Default Options
    $('#carousel').plusSlider({
        
        /* General */
        disableLoop : false,            // Disables prev or next buttons if they are on the first or last slide respectively. 'first' only disables the previous button, 'last' disables the next and 'both' disables both
        disableWhiteSpace : true,       // Content fills the carousel at all times - no empty spaces at the end.
        
        /* Display related */
        defaultSlide : 0,               // Sets the default starting slide - Number based on item index
        displayTime : 8000,             // The amount of time the carousel waits before automatically moving on to the next one. This requires 'autoPlay: true'
        sliderEasing : 'linear',        // Anything other than 'linear' and 'swing' requires the easing plugin
        speed : 500,                    // The amount of time it takes for the carousel to move from one slide to another

        /* Functioanlity related */
        autoPlay : true,                // Creats a times, looped 'slide-show'
        pauseOnHover : true,            // AutoPlay does not continue ifsomeone hovers over Plus Slider.

        /* Arrow related */
        createControls : true,          // Creates forward and backward navigation
        controlPosition : 'after',      //Where to insert arrows in relation to the slider ('before', 'prepend', 'append', or 'after')
        nextText : 'Next',              // Adds text to the 'next' trigger
        prevText : 'Previous',          // Adds text to the 'prev' trigger
        arrowJump : 1,                  // The amount of items jumped when next/previous is activated

        /* Pagination related */
        createPagination : true,        // Creates Numbered pagination
        paginationPosition : 'after',   // Where to insert pagination in relation to the carousel element ('before', 'prepend', 'append', or 'after')
        paginationWidth : false,        // Automatically gives the pagination a dynamic width

        /* Callbacks */
        onInit : null,                  // Callback function: On slider initialize
        onSlide : null,                 // Callback function: As the slide starts to animate
        afterSlide : null               // Callback function: As the slide completes the animation

    });

## Using the API
The following are the PlusSlider values you may use within the callback functions. Property names beginning with $ ( dollar sign ) are referencing a jQuery object, methods are referenced by ending in () ( open parenthasis, close parenthasis ) and the rest contain a number value.

    base.$wrap              // References the .plusshift jQuery object
    base.$slides            // References the .plusshift-child jQuery objects
    base.currentSlideIndex  // References the current item's index number
    base.$currentSlide      // References the .plusshift-active jQuery object
    base.sliderWidth        // References the target elements total width
    base.slideCount         // The amount of carousel items
    base.slideIndexCount    // The index number of the last item
    base.slidePosition      // Current slide's 'left' position
    base.sliderPosition     // The carousels current 'left' position
    base.animating          // Boolean - true means the slider is busy animating.
    base.slideWidth         // The width of each slide
    base.$pagination        // References the .plusshift-pagination jQuery object
    base.$paginationWrap    // References the .plusshift-pagination-wrap jQuery object
    base.$paginationItems   // References the .plusshift-arrow jQuery objects
    base.paginationThumb(i) // Determines whether the pagination thumbnail is activated on the item. Only accepts Item index
    base.paginationTitle(i) // Determines whether the pagination title is activated on the item. Only accepts Item index
    base.beginTimer()       // Method that begins the autoPlay timer
    base.clearTimer()       // Method that resets the autoPlay timer
    base.toSlide()          // Method that will change the current/active item - Accepts 'next', 'prev' or an index number value as args

### Accessing properties and methods from outside the callback functions
If you wish to make use of the slider methods and properties outside of the callback functions, you would need to initialize the slider in a slightly different way:

    var carousel = null;
    
    $(document).ready(function(){
        carousel = new $.plusShift($('#carousel'), {});
    });
    carousel.toSlide('next); // move carousel to the right
    carousel.toSlide('prev'); // move carousel to the left
    carousel.toSlide(3); // move slider to arbitrary index (first slide is 0, second is 1, etc.) and updates the current carousel item


## Customizing PlusSlider

### General
Each item *must* be the same width.

### Pagination titles and thumbnails (optional)
Add the attributes 'data-plusshift-thumbnail' and 'data-plusshift-title' to the carousel items.
attribute="value"
data-plusshift-thumbnail="path/to/image.jpg"
data-plusshift-title="Title of Item"

## Changelog

### Version 0.1
* First official version