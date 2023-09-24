# daily-coding-problem

This repository contains JavaScript solutions to daily coding challenges provided by [Daily Coding Problem](https://www.dailycodingproblem.com/). Each solution is designed to solve a specific coding problem and can be a valuable resource for improving problem-solving skills.

Happy coding!

# daily-coding-problem

This repository contains JavaScript solutions to daily coding challenges provided by [Daily Coding Problem](https://www.dailycodingproblem.com/). Each solution is designed to solve a specific coding problem and can be a valuable resource for improving problem-solving skills.

Happy coding!

<details>
<summary>Problem#1[Hard]</summary>

**Problem Statement**

This coding interview problem was asked by Uber.

Given an array of integers, return a new array such that each element at index `i` of the new array is the product of all the numbers in the original array except the one at `i`.

For example, if our input was `[1, 2, 3, 4, 5]`, the expected output would be `[120, 60, 40, 30, 24]`. If our input was `[3, 2, 1]`, the expected output would be `[2, 3, 6]`.

**Follow-Up**

What if you can't use division?

**Solution 1 - Brute Force (O(n^2) Time Complexity)**

The first solution uses a brute force approach with a time complexity of O(n^2). It calculates the product of all elements except the current element for each element in the array.

```javascript
function getProductOfArray(array) {
  let arr = [];
  for (let i = 0; i < array.length; i++) {
    let multiple = 1;
    for (let j = 0; j < array.length; j++) {
      if (array[i] !== array[j]) {
        multiple *= array[j]
      }
    }
    arr.push(multiple)
  }

  return arr;
}
```

**Solution 2 - Create Arrays for Left and Right Side of the Product (Optimized O(n) Time Complexity)**

```javascript
function getProductOfArray(array) {
  const leftProdArray = new Array(array.length);
  const rightProdArray = new Array(array.length);
  const finalArray = new Array(array.length);

  leftProdArray[0] = 1;
  for(let i = 1; i  < array.length; i++){
    leftProdArray[i] = array[i - 1] * leftProdArray[i - 1];
  }

  rightProdArray[array.length - 1] = 1;
  for (let i = array.length - 2; i >= 0; i--) {
    rightProdArray[i] = array[i + 1] * rightProdArray[i + 1];
  }

  for (let i = 0; i < array.length; i++) {
    finalArray[i] = leftProdArray[i] * rightProdArray[i];
  }

  return finalArray;
}
```
**Usage**

To use these solutions, you can call the getProductOfArray function with an array of integers as an argument. For example:

```javascript
console.log(getProductOfArray([3, 2, 1])); // Outputs: [2, 3, 6]
```
</details>





