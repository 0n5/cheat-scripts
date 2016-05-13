Javascript algorithm
====================



#### Reverse a String

``` javascript
function reverseString(str) {
  return str.split('').reverse().join('');
}

alert(reverseString('hello'));
```

#### Find the Factorial of a Number

```javascript
function factorialize(num) {
  if (num === 0) {
   return 1;
  } else {
    
  return num * factorialize(num-1);
}  
  }
  
alert(factorialize(5));
```


#### Find Longest Word in String:


``` javascript
function findLongestWord(str) {
  var longestArray = str.match(/\w[a-z]{0,}/gi);
    // string.match() uses regex to create array of matches
  var word = longestArray[0];

  for(i=1; i<longestArray.length; i++) {
      // loop thru the array of matches
    if (word.length < longestArray[i].length ) {
       // if the word in the array is less than 
       // the current iteration of the array of matches 
      word = longestArray[i];
        // store current iteration in the word variable
    }    
  }
  return word.length;
    // will return length of the longest word
}

alert(findLongestWord('The quick brown fox jumped over the lazy dog'));
```


#### Capitalize 1st letter of each word

``` javascript
function titleCase(str) {
 
    return str.replace(/\w\S*/g, function(txt) {
      // string.replace() matches string with a regex pattern as first parameter
      // regex pattern is any word, without whitespace

        return txt.charAt(0).toUpperCase()+ txt.substr(1).toLowerCase();
      
      });
          // replaces the first parameter with result of a function
          // function changes 0th index to uppercase
          // concats and lowercases the 1th and on, to the new string

}

alert(titleCase("I'm a little tea pot"));
```

#### Return array containing largest numbers from multi-d array

``` javascript
function largestOfFour(arr) {
  
    return arr.map(function(sub) {
    return Math.max.apply(null, sub);
  });
}

largestOfFour([[4, 5, 1, 3], [13, 27, 18, 26], [32, 35, 37, 39], [1000, 1001, 857, 1]]);
```

#### Return array containing largest numbers from multi-d array

Iteratively:

```javascript
function largestOfFour(arr) {

var newArray = [];
for (var i = 0; i < arr.length; i++) {
    newArray.push(Math.max.apply(Math, arr[i]));
  }
  return newArray;
}

alert(largestOfFour([[4, 5, 1, 3], [13, 27, 18, 26], [32, 35, 37, 39], [1000, 1001, 857, 1]]));

```

