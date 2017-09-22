Redux Components
===


Create components in components/ directory

Components are functional, do not need to know anything about state

``` javascript

import React, { Component } from 'react';
import CatList from '../containers/cat-list';
import CatDetail from '../containers/cat-detail';

export default class App extends Component {
    render() {
        return (
            <div>
                <CatList />
                <CatDetail />
            </div>
            );
    }
    
}

```
