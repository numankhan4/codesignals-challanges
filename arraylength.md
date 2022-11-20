======Problem=======

Given an array of words and a number k, your task is to return an array with length k where the ith element is the number of unique prefixes with length i + 1 among the given words (including only words that are at most i characters long).

Example

For words = ["apple", "app", "apricot", "stone"] and k = 8, the output should be solution(words, k) = [2, 2, 3, 3, 3, 1, 1, 0].

There are 2 different prefixes of length 1: a and s,
There are 2 different prefixes of length 2: ap and st,
There are 3 different prefixes of length 3: app, apr and sto,
There are 3 different prefixes of length 4: appl, apri and ston,
There are 3 different prefixes of length 5: apple, apric and stone,
There is only 1 prefixes of length 6: aprico,
There is only 1 prefixes of length 7: apricot,
There is no word of length 8, so the final element is 0.
Input/Output

[execution time limit] 4 seconds (js)

[input] array.string words

An array of strings, each of which consisting of only lowercase Latin letters.

Guaranteed constraints:
1 ≤ words.length ≤ 103,
1 ≤ sum(words[i].length) ≤ 103.

[input] integer k

An integer representing the length of the output array.

Guaranteed constraints:
1 ≤ k ≤ 103.

[output] array.integer

An array of numbers of unique prefixe

======Solution=======

function solution(words, k) {
const rtnArr = new Array(k);

 

   

  for(let i = 0; i < k; i++){

    const prArr = words.map(item => item.length >= i+1 ? item.substring(0, i+1) : "");

    const uniqueArr = prArr.filter((value, index, self) => {

    return value && self.indexOf(value) === index;

  });

    rtnArr[i] = uniqueArr.length;

  }

  return rtnArr;
}


