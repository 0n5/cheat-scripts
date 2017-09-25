React Native Axios
======


#### Axios

``` javascript

import React, { Component } from 'react';
import { ScrollView, Text } from 'react-native';
import axios from 'axios';
import CatDetail from './CatDetail';

class CatList extends Component  {

    state = { albums: [] };
    componentDidMount() {
        axios.get('https://someAPI')
        .then(response => this.setState({ cats: response.data }))
    }
    renderCats() {
        return this.state.cats.map(cat => 
            <CatDetail key={cat.name} cat={cat} />
        );
    }

    render() {
        return (
        <ScrollView>
            {this.renderCats()}
        </ScrollView>
    )
}
}
export default CatList;

```