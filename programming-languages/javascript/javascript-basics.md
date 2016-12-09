JavaScript
==========

[JavaScript Beautifier](http://jsbeautifier.org/)

#### Scope

global scope

``` javascript

var someVariable = "test";  // global scope
var someFunction = function() {
	// function curly braces create scope paramaters
	
	var someLocalVariable = "local";   // local scope
	
}

```


#### Methods

``` javascript

var contact = {
// anonymous function 
  fullName: function() { 
  	var firstName = "Andrew";
  	var lastName = "Chalkley";
  	console.log(firstName + " " + lastName);
  }
}

```


#### Functions

##### Encapsulation

``` javascript
education.display = function() { 
	// some code
}

education.display()  // call function

```


#### Arrays

##### For Loop

``` javascript

for (var i = 0; i < work.length; i++) {
	// something 
};
```

##### Push

adds object to end of an array

    myArray.push(["dog", 3]);

create new array and push objects

``` javascript

    var contactArray = [];
    contactArray.push(formattedMobile, formattedEmail, formattedTwitter, formattedGithub, formattedLocation);
```

##### Pop

removes last element in array

    var removedFromMyArray = myArray.pop();

##### Shift

removes first element in array

    var removedFromMyArray = myArray.shift();

##### Unshift

adds element to the front of an array

    myArray.unshift(["Paul", 35]);

##### Length

	var workLength = workArray.length;  // sets variable to length of array



#### Methods

##### Replace

    string.replace("old", "new");

With Replacement Operators

    var formattedName = HTMLheaderName.replace("%data%", name);
    
    
##### Append

    string.append("new");

With Replacement Operators & jquery css selector

    $("#header").append(formattedName);


#### Objects

Literal Notation

``` javascript

var myObj = { "name" : "myname",
              "age"  : 30
        
};

``` javascript    


accessing objects

    console.log(myObj.name);
    $("#main").append(myObj.city);   # using jquery selector, dot notation
    $("#main").append(myObj(city["Somewheresville"]);  # bracket notation

Dot Notation

``` javascript
    
var myObj = {};
myObj.city = "Somewhere City";

```


Bracket Notation

``` javascript

var myObj = {};
myObj["name"] = "Name";

```

#### JSON

[JSON linter](jsonlint.com)


JSON with multiple objects

``` javascript

var bio = {
	"name": "My Name",
	"role": "Web Developer",
	"contacts": {
		"mobile": "867-5309",
		"email": "bob@class-central.com",
		"github": "p00gz",
		"twitter": "@p00gz",
		"location": "Chicago, IL"
	},
	"welcomeMessage": "Looking for full-time remote development opportunities",
	"skills": [
		"Front End Development", "Full Stack Development", "DevOps", "Information Security"
	],
	"biopic": "https://avatars0.githubusercontent.com/u/5743472?v=3&s=460"
};

```
