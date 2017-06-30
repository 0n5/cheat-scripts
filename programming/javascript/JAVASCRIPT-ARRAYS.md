JavaScript Arrays
=================

#### Loops

``` javascript

for (var i = 0; i < work.length; i++) {
	// something 
};
```

#### Push

adds object to end of an array

    myArray.push(["dog", 3]);

create new array and push objects

``` javascript

    var contactArray = [];
    contactArray.push(formattedMobile, formattedEmail, formattedTwitter, formattedGithub, formattedLocation);
```

#### Pop

removes last element in array

    var removedFromMyArray = myArray.pop();

#### Shift

removes first element in array

    var removedFromMyArray = myArray.shift();

#### Unshift

adds element to the front of an array

    myArray.unshift(["Paul", 35]);

#### Length

	var workLength = workArray.length;  // sets variable to length of array
