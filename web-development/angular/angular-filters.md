AngularJS Filters
=================

    {{ [NUMBERS] | currency }}                          # converts to currency 
    {{ "[STRING]" | uppercase }}                        # string to upcase
    {{ {foo: "bar", baz: 23} | json }}                  # outputs json
    {{ [NUMBERS] | date }}                              # converts to date


#### Order By

in index.html

``` html

Sort by:
<select ng-model="orderProp">
  <option value="name">Alphabetical</option>
  <option value="age">Newest</option>
</select>
...
  <li ng-repeat="object in list | filter:query | orderBy:orderProp">
    ...
  </li>

```
