React Native Styling
======


#### Styling

``` javascript

import React from 'react';
import { Text, View } from 'react-native';
import Card from './Card';
import CardSection from './CardSection';

const CatDetail = (cats) => {
    const { catType, name } = cats
    // destructure props

    const { 
        headerContentStyle, headerTextStyle
    } = styles;
    
    // destructure styling

    return (

        <Card>
            <CardSection>
                <View style={headerContentStyle}>
                    <Text style={headerTextStyle}>{ name }</Text>
                    <Text>{ catType }</Text>
                </View>
            </CardSection>
        </Card>
    )
}

const styles = {
    headerContentStyle: {
        flexDirection: 'column',
        justifyContent: 'space-around'
    },
    headerTextStyle: {
        fontSize: 18
    }
}
// declared styles

export default CatDetail;
```


#### Images 

Images must have style associated to be visible

``` javascript
    
    ...

    const { image } = cats
    const { 
        thumbnailStyle, 
        imageStyle,
        thumbnailContainerStyle,
     } = styles;

     ...
            <View style={thumbnailContainerStyle}>
                <Image 
                    style={thumbnailStyle}
                    source={{ uri: thumbnail_image }} />
            </View>


            <Image 
                style={imageStyle}
                source={{ uri: image }} />
    ...

    const styles = {
    thumbnailStyle: {
        height: 50,
        width: 50
    },
    imageStyle: {
        height: 300,
        width: null,
        flex: 1
    },
    thumbnailContainerStyle: {
        justifyContent: 'center',
        alignItems: 'center',
        marginLeft: 10,
        marginRight: 10
    }
}
            

```
