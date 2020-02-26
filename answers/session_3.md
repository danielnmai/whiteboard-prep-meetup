### Leetcode 944 - Delete Columns to Make Sorted
Solved by: Daniel Mai
JavaScript - Passed all Leetcode tests

```javascript
/**
 * @param {string[]} A
 * @return {number}
 */
var minDeletionSize = function(A) {
    
    
    /*
    0 1 2 3 4 5
 0  a b c d e f
 1  u v w x y z
 
 deletion indices {0, 2, 3} (D.length is 3) column 0, 2, 3 items are removed
 after deletion:
 b  e   f
 v  y   z
 
 => each column in the array are sorted in increasing order, we can return D.length
    
    
    
    */
    if(A === null) return -1;
  
  const rowLength = A.length;
  const colLength = A[0].length;
  let minDeletionSize = 0;

  for(let col = 0; col < colLength; col++){
    for(let row = 0; row < rowLength - 1; row++){
      if(A[row][col] > A[row + 1][col]){
       minDeletionSize++;
       break;
      }
    }
  }
  
  return minDeletionSize;
    
};
```

### Leetcode 63 - Unique Paths II
Solved by: Daniel Mai
JavaScript - Passed half Leetcode tests, exceeding time limit for 
large grids. Needs to optimize recursion calls by using dynamic programming

```javascript
/**
 * @param {number[][]} obstacleGrid
 * @return {number}
 */
var uniquePathsWithObstacles = function(grid) {
    const m = grid.length;
    const n = grid[0].length;
    
    let uPaths = 0;
    
    function move(row, col){
        if(row === m || col === n) return; // out of bound
        if(grid[row][col] === 1) return; // hit an obstable
        
        // reach destination
        if(row === m - 1 && col === n - 1){
            uPaths++;
            return;
        }        
        
       
        move(row + 1, col); // move down
        move(row, col + 1); // move right
        
    }
    move(0, 0);
    return uPaths;    
};
```