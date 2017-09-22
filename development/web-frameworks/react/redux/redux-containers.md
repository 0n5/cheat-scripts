Redux Containers
===


Containers should be created in the containers/ directory

Containers are components that are class based and care about state

Anything return by mapStateToProps is available on container as props

``` javascript


import React, { Component } from 'react';
import { connect } from 'react-redux';

class CatDetail extends Component {

        return (
            <div>
                {this.props.cat.name}
            </div>
            );
    }
}

function mapStateToProps(state) {
    return {
        cat: state.activeCat
    };
}
export default connect(mapStateToProps)(CatDetail);


```

#### mapDispatchToProps


Anything that is dispatched from the action creator to the reducer is availabe as props on the container


``` javascript

import React, { Component } from 'react';
import { connect } from 'react-redux'
import { selectBook } from '../actions/index.js';
import { bindActionCreators } from 'redux';

class BookList extends Component {
    renderList() {
        // do something
    }
    
    render() {
        return (
            // return something
            );
    }
}

function mapStateToProps(state) {
    return {
        cats: state.cats
    };
}

function mapDispatchToProps(dispatch) {
    return bindActionCreators({ selectCat: selectCat }, dispatch);
}

export default connect(mapStateToProps, mapDispatchToProps)(CatList);
// exports the container created by connecting the component and state



```

#### Conditional Rendering

``` javascript

    render() {
        if(!this.props.cat) {
            return <div>Select Cat</div>;
        }
        // if the action creator has not been triggered this conditional will render
        // a default message instead of the actual return expression in the component
        
        return (
            <div>
                {this.props.cat.name}
            </div>
        )
```
