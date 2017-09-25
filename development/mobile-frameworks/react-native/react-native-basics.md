React Native Basics
====

#### Basics

* index.ios.js and index.android.js are the entry points for the app
* AppRegistry is the JS entry point of all RN apps
* Text Component displays text
* View Container builds UI, supports flexbox


#### App

In index.ios.js or index.android.js:

``` javascript

import React from 'react';
import { Text, AppRegistry, View } from 'react-native';


const App = () => ( 
    <View>
      <Header headerText={'Cats'}/>
    </View>   
    )

AppRegistry.registerComponent('cats', () => App);

```

#### Passing props from parent to child

``` javascript

import React from 'react';
import { View } from 'react-native';

const Cat = (props) => {
    return (
        <View>
            {props.children}
        </View>
    );
};

}

```

export default Card;


#### Links

``` javascript

    <Button onPress={()=> Linking.openURL(url)}>
        Buy Now
    </Button>

```

#### Scrolling

Must have flex property on the root view

``` javascript

    <View style={{ flex: 1 }}>
      <Header headerText={'Cats'}/>
    </View>   

```

``` javascript
    
    ...
    
    import { ScrollView, Text } from 'react-native';

    ...

    render() {
        return (
        <ScrollView>
            {this.renderCats()}
        </ScrollView>
    )

```