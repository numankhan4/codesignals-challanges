=====Problem ========

Yesterday you found some shoes in the back of your closet. Each shoe is described by two values:

type indicates if it's a left or a right shoe;
size is the size of the shoe.
Your task is to check whether it is possible to pair the shoes you found in such a way that each pair consists of a right and a left shoe of an equal size.

Example

For

shoes = [[0, 21], 
         [1, 23], 
         [1, 21], 
         [0, 23]]
the output should be
solution(shoes) = true;

For

shoes = [[0, 21], 
         [1, 23], 
         [1, 21], 
         [1, 23]]
the output should be
solution(shoes) = false.

Input/Output

[execution time limit] 4 seconds (js)

[input] array.array.integer shoes

Array of shoes. Each shoe is given in the format [type, size], where type is either 0 or 1 for left and right respectively, and size is a positive integer.

Guaranteed constraints:
1 ≤ shoes.length ≤ 200,
1 ≤ shoes[i][1] ≤ 100.

[output] boolean

true if it is possible to pair the shoes, false otherwise.

===== Solutions ========.

function solution(shoes) {
  const pairs = shoes.reduce((pairs, shoe) => {
    const [type, size] = shoe;
    pairs[size] = (pairs[size] || 0) + (type ? +1 : -1);
    return pairs;
  }, {});
  return !Object.values(pairs).some(value => value);
}

===== Solution 2========.
function solution(shoes) { 
 const result = shoes.reduce((acc, [side, size]) => {
  const action = side ? 1 : -1
  console.log("actions", action);
   
  acc[size]
    ? acc[size] += action
    : acc[size] = action
     console.log(acc)
  return acc;
 }, {});

 return Object
  .values(result)
  .every((item) => item === 0); 
 }

 console.log(solution([[0, 21], [1, 23], [1, 21], [0, 23]]));
