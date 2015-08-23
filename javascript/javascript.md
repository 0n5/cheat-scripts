Javascript algorithm cheats
===========================

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
