HTML5 Canvas
===========

[Drawing functions](https://www.w3.org/TR/2dcontext/#building-paths);

#### Creating a Canvas

``` html

<canvas id="c" width="200" height="200"></canvas>

```

In javascript file:

``` javascript

<script>
    var c = document.querySelector("#c");
    // gets the canvas that was layed out
    
    var ctx = c.getContext("2d");
    // gets context of the canvas and pass in 2D canvas paramater
    
</script>



```

#### Clear

    ctx.clearRect(0, 0, c.width, c.height); # clears whole canvas

or

    c.width = c.width;  # clears whole canvas
    
Clear portion of Canvas

    ctx.clearRect(0,0,25,25); 



#### Fill

    ctx.fillStyle = "blue";
    ctx.fillRect(0,0,50,50);
