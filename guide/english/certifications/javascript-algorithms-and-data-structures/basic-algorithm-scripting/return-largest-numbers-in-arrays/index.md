---
title: Return Largest Numbers in Arrays
---
![:triangular_flag_on_post:](https://forum.freecodecamp.com/images/emoji/emoji_one/triangular_flag_on_post.png?v=3 ":triangular_flag_on_post:") Remember to use <a>**`Read-Search-Ask`**</a> if you get stuck. Try to pair program ![:busts_in_silhouette:](https://forum.freecodecamp.com/images/emoji/emoji_one/busts_in_silhouette.png?v=3 ":busts_in_silhouette:") and write your own code ![:pencil:](https://forum.freecodecamp.com/images/emoji/emoji_one/pencil.png?v=3 ":pencil:")

### ![:checkered_flag:](https://forum.freecodecamp.com/images/emoji/emoji_one/checkered_flag.png?v=3 ":checkered_flag:") Problem Explanation:

You will get an array that contains sub arrays of numbers and you need to return an array with the largest number from each of the sub arrays.

## ![:speech_balloon:](https://forum.freecodecamp.com/images/emoji/emoji_one/speech_balloon.png?v=3 ":speech_balloon:") Hint: 1

You will need to keep track of the array with the answer and the largest number of each sub-array.

> _try to solve the problem now_

## ![:speech_balloon:](https://forum.freecodecamp.com/images/emoji/emoji_one/speech_balloon.png?v=3 ":speech_balloon:") Hint: 2

You can work with multidimensional arrays by `Array[Index][SubIndex]`

> _try to solve the problem now_

## ![:speech_balloon:](https://forum.freecodecamp.com/images/emoji/emoji_one/speech_balloon.png?v=3 ":speech_balloon:") Hint: 3


Pay close attention to the timing of the storing of variables when working with loops

> _try to solve the problem now_

## Spoiler Alert!

![warning sign](//discourse-user-assets.s3.amazonaws.com/original/2X/2/2d6c412a50797771301e7ceabd554cef4edcd74d.gif)

**Solutions ahead!**

## ![:beginner:](https://forum.freecodecamp.com/images/emoji/emoji_one/beginner.png?v=3 ":beginner:") Basic Code Solution:

**(Procedural approach)**

    function largestOfFour(arr) {
      var results = [];
      for (var n = 0; n < arr.length; n++) {
        var largestNumber = arr[n][0];
        for (var sb = 1; sb < arr[n].length; sb++) {
          if (arr[n][sb] > largestNumber) {
            largestNumber = arr[n][sb];
          }
        }

        results[n] = largestNumber;
      }

      return results;
    }

![:rocket:](https://forum.freecodecamp.com/images/emoji/emoji_one/rocket.png?v=3 ":rocket:") <a href='https://repl.it/CLjU/734' target='_blank' rel='nofollow'>Run Code</a>

### Code Explanation:

*   Create a variable to store the _results_ as an array.
*   Create an outer loop to iterate through the outer array.
*   Create a second variable to hold the largest number and initialise it with the first number. This must be outside an inner loop so it won't be reassigned until we find a larger number.
*   Create said inner loop to work with the sub-arrays.
*   Check if the element of the sub array is larger than the currently stored largest number. If so, then update the number in the variable.
*   After the inner loop, save the largest number in the corresponding position inside of the `results` array.
*   And finally return said array.

#### Relevant Links

*   <a href='http://forum.freecodecamp.com/t/javascript-for-loop/14666s-Explained' target='_blank' rel='nofollow'>For loops</a>

## ![:sunflower:](https://forum.freecodecamp.com/images/emoji/emoji_one/sunflower.png?v=3 ":sunflower:") Intermediate Code Solution:

**(Declarative approach)**

    function largestOfFour(arr) {
      return arr.map(function(group){
        return group.reduce(function(prev, current) {
          return (current > prev) ? current : prev;
        });
      });
    }

![:rocket:](https://forum.freecodecamp.com/images/emoji/emoji_one/rocket.png?v=3 ":rocket:") <a href='https://repl.it/CLjU/733' target='_blank' rel='nofollow'>Run Code</a>

### Code Explanation:

*   we map all items within the main array to a new array using `Array.prototype.map()` and return this array as the final result
*   within each inner array, we reduce its contents down to a single value using `Array.prototype.reduce()`
*   the callback function passed to the reduce method takes the previous value and the current value and compares the two values
*   if the current value is higher than the previous value we set it as the new previous value for comparison with the next item within the array or returns it to the map method callback if it's the last item

#### Relevant Links

*   <a href='http://forum.freecodecamp.com/t/javascript-array-prototype-map/14294' target='_blank' rel='nofollow'>Array.prototype.map()</a>
*   <a href='http://forum.freecodecamp.com/t/javascript-array-prototype-reduce/14299' target='_blank' rel='nofollow'>Array.prototype.reduce()</a>
*   <a href='http://forum.freecodecamp.com/t/javascript-ternary-operator/15973' target='_blank' rel='nofollow'>Ternary Operators</a>

## ![:rotating_light:](https://forum.freecodecamp.com/images/emoji/emoji_one/rotating_light.png?v=3 ":rotating_light:") Advanced Code Solution:

**(Declarative approach)**

    function largestOfFour(arr) {
      return arr.map(sb => Math.max(...sb));
    }

![:rocket:](https://forum.freecodecamp.com/images/emoji/emoji_one/rocket.png?v=3 ":rocket:") <a href='https://repl.it/CLjU/17' target='_blank' rel='nofollow'>Run Code</a>

### Code Explanation:

*   We map all items within the main array to a new array using `Array.prototype.map()` and return this array as the final result
*   Then we spread `...` each subarray into `Math.max()` function as arguments. 
*   `Math.max()` function returns back the highest number which will be added into our final array. 


#### Relevant Links

*   <a href ='https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math/max' target='_blank' rel='nofollow'> Math.max()</a>
*   <a href='https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/map' target='_blank' rel='nofollow'>Array.prototype.map()</a>
*   <a href='https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Spread_syntax' target='_blank' rel='nofollow'>Spread syntax `...`</a>

## ![:clipboard:](https://forum.freecodecamp.com/images/emoji/emoji_one/clipboard.png?v=3 ":clipboard:") NOTES FOR CONTRIBUTIONS:

*   ![:warning:](https://forum.freecodecamp.com/images/emoji/emoji_one/warning.png?v=3 ":warning:") **DO NOT** add solutions that are similar to any existing solutions. If you think it is **_similar but better_**, then try to merge (or replace) the existing similar solution.
*   Add an explanation of your solution.
*   Categorize the solution in one of the following categories — **Basic**, **Intermediate** and **Advanced**. ![:traffic_light:](https://forum.freecodecamp.com/images/emoji/emoji_one/traffic_light.png?v=3 ":traffic_light:")
*   Please add your username only if you have added any **relevant main contents**. (![:warning:](https://forum.freecodecamp.com/images/emoji/emoji_one/warning.png?v=3 ":warning:") **_DO NOT_** _remove any existing usernames_)

> See ![:point_right:](https://forum.freecodecamp.com/images/emoji/emoji_one/point_right.png?v=3 ":point_right:") <a href='http://forum.freecodecamp.com/t/algorithm-article-template/14272' target='_blank' rel='nofollow'>**`Wiki Challenge Solution Template`**</a> for reference.
