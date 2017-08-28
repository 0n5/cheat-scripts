React Array.Map
===============

When mapping over an array the elements must have a `key` property. 


``` javascript

var cats = ["Frankie", "Helga", "Inga", "Frau"]

React.createElement(
    "ul",
    { className: "catList" }, 
    cats.map(cat, i) =>
        React.createElement("li", {key: i}, cat)
)

```

Spread operator

``` javascript

props.cats.map((cat, i) => {
    catComponent key={i} {...cat} />

// destructures object so you dont have to props on each 
// when accessing the props in the catComponent you dont need to call props
})

catComponent = ({ name, gender, type }) =>
    <div>
        <h1>{name}</h1>
        <span>{gender}</span>
        <span>{type}</span>
    </div>
// no prop.name needed!
```

