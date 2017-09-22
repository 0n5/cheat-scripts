Redux Reducers
====

Individual reducers create in the reducers/ directory


``` javascript

export default function(state=null, action) {
    switch(action.type) {
        case 'CAT_SELECTED':
            return action.payload;
    }
    return state; // default 
}

```


#### Combine Reducers

create in reducers directory as index.js


``` javascript


import { combineReducers } from 'redux';
import CatsReducer from './reducers_cats';
import ActiveCat from './reducers_active_cats';

const rootReducer = combineReducers({
    cats: CatsReducer,
    activeCat: ActiveCat
    
});

export default rootReducer;


```