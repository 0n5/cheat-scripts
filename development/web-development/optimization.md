Website optimization
====================

[CSS Triggers](https://csstriggers.com)
[Chrome Canary](https://www.google.com/chrome/browser/canary.html)


most devices refresh their screen 60 times a second<br>
60fps (frames per second) is performance standard

#### Frame Composition

* Javascript
* Style
* Layout
* Paint
* Composite

#### Critical Rendering Path

* DOM
* CSSOM
* Render Tree (DOM & CSSOM combined)
* Layout
* Paint Pixels


#### Web App Life Cycle (RAIL)

to reach 60 fps peak performance:

* Load (initial load should be about 1 second)
* Idle (waiting for user to interact. about 50 ms)
* Animations (16 ms, because of browser overhead actually around 10-12 ms)
* Response (100 ms)

After initial browser animation load, it can be run backwards at very little cost<br>
FLIP (First, Last, Invert, Play)

* Collect properties of the element in its collapsed or natural position
* expand the element and collect the properties again
* Figure out differences between the two
* transform the element back
* wait a frame
* switch on animations and remove transforms    


Interactions that require 60fps

* spinners
* scrolling
* drag and drop
* pinching
* pull to refresh
* side menu slide
* opening comments

Because of JIT compiling micro-optimizations should be a last resort<br>
Execute JS as early as possible every frame 