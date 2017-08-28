React PropTypes
===============

Provide property validation

* React.PropTypes.array
* React.PropTypes.bool
* React.PropTypes.func
* React.PropTypes.number
* React.PropTypes.object
* React.PropTypes.string

ES6 propTypes

``` javascript

class Cats extends React.Component {
    render() {
        const = {name, gender, age} = this.props
        return (
            <div>
                <h1>{title}</h1>
            </div>
        
        )
    }
}

Cat.propTypes = {
    
    title: propTypes.string.isRequired,
    age: propTypes.number
}

Cat.defaultProps = {
    age: 0,
}

```

Static defaultProps

``` javascript

static defaultProps = {
    
    title: 'kitty',
    age: 0,
}

```