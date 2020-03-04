### Homework: Leetcode 222 - Count Complete Binary Tree
Solved by: Daniel Mai
JavaScript - Passed all Leetcode tests

```javascript
/**
 * Definition for a binary tree node.
 * function TreeNode(val) {
 *     this.val = val;
 *     this.left = this.right = null;
 * }
 */
/**
 * @param {TreeNode} root
 * @return {number}
 */

function Node(val) {
  this.val = val;
  this.left = null;
  this.right = null;
}
function countNodes(node){ 
  if(!node){
    return null;
  }
  const d = getHeight(node);
  if(d === 0) {
    return 1;
  }
  let left = 1, right = Math.pow(2, d) - 1;
  let mid;
  while(left <= right){
    mid = Math.floor((left + right) / 2);
    if(isExist(mid, d, node)){
      left = mid + 1;
    } else {
      right = mid - 1;
    }
  }
  return Math.pow(2, d) - 1 + left;
}

function getHeight(node){
  let height = 0;
  while(node.left){
    height++;
    node = node.left;
  }
  return height;
}

function isExist(k, d, node){
  let left = 0, right = Math.pow(2, d) - 1;
  for(let i = 0; i < d; i++) {
    let mid = (left + right) / 2;
    if(mid <= k){
      if(node.right){
        node = node.right;
      } else {
        node = null;
      }
      left = mid;
    }
    else if(mid > k){
      if(node.left){
        node = node.left;
      } else {
        node = null;
      }
      right = mid;
    }
  }
  return node !== null;
}
```