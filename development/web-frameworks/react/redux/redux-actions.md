Redux Actions
===


Create actions in actions/index.js file

``` javascript

export function selectCat(cat) {
    return {
        type: 'CAT_SELECTED',
        payload: cat,   
    };
}

```