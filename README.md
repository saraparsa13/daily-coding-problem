# daily-coding-problem

This repository contains JavaScript solutions to daily coding challenges provided by [Daily Coding Problem](https://www.dailycodingproblem.com/). Each solution is designed to solve a specific coding problem and can be a valuable resource for improving problem-solving skills.

Happy coding!

<details>
<summary>Problem#1[Hard]</summary>
<br/>
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

**Solution 2 - (Optimized O(n) Time Complexity)**

Create Arrays for the Left and Right Side of the Product.

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

<details>
<summary>Problem#2[Medium]</summary>
<br/>
This problem was asked by Google.

Given the root to a binary tree, implement serialize(root), which serializes the tree into a string, and deserialize(s), which deserializes the string back into the tree.

For example, given the following Node class

```python
class Node:
    def __init__(self, val, left=None, right=None):
        self.val = val
        self.left = left
        self.right = right
```
The following test should pass:

```python
node = Node('root', Node('left', Node('left.left')), Node('right'))
assert deserialize(serialize(node)).left.left.val == 'left.left'
```

**Solution 1 (DFS approach - Preorder)**

 serializing and deserializing a binary tree using the Depth-First Search (DFS) approach to traverse the tree.
```javascript
class Node {
  constructor(val, left = null, right = null) {
    this.val = val;
    this.left = left;
    this.right = right;
  }
}

function serialize(node) {
  let res = [];
  function dfs(node) {
    if (!node) {
      res.push("N");
      return;
    }
    res.push(node.val);
    dfs(node.left);
    dfs(node.right);
  };
  dfs(node);
  return res.join(',');
};

function deserialize(string) {
  data = string.split(',');
  let i = 0;

  function dfs() {
    if (data[i] === "N") {
      i++;
      return null;
    }

    const node = new Node(data[i]);
    i++;
    node.left = dfs();
    node.right = dfs();
    return node;
  }

  return dfs();
}


const node = new Node('root', new Node('left', new Node('left.left')), new Node('right'));
const serialized = serialize(node);
const deserialized = deserialize(serialized);

console.log(deserialized.left.left.val); // Outputs: 'left.left'
```

**Time Complexity**

serialize and deserialize functions both have the O(N) complexity, where N is the number of nodes in the binary tree. This is because the functions visit each node exactly once while performing the DFS traversal.


</details>


<details>
<summary>Problem#3[Hard]</summary>
<br/>
Good morning! Here's your coding interview problem for today.

This problem was asked by Facebook.

Given the mapping a = 1, b = 2, ... z = 26, and an encoded message, count the number of ways it can be decoded.

For example, the message '111' would give 3, since it could be decoded as 'aaa', 'ka', and 'ak'.

You can assume that the messages are decodable. For example, '001' is not allowed.
**Solution**
<br/>
```javascript

```

</details>
