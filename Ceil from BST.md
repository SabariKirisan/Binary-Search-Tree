## Ceil from BST (c++)

Ceil of an integer is the closest integer greater than or equal to a given number.

## Example
![image](https://github.com/user-attachments/assets/ae8bfb82-9d84-4636-a2da-d463772fd242)

Input: x=2

Output: 3
## PROGRAM:(Main.cpp)
```
#include <bits/stdc++.h> 
using namespace std;
int findCeil(BinaryTreeNode<int> *node, int x)
{
    int ceil=-1;
    while(node)
    {
        if(node->data == x)
        {
            ceil=node->data;
            return ceil;
        }   
       if(x > node->data)
       {
            node=node-> right;
       }
       else
       {
            ceil=node->data;
            node=node->left;
       }
    }
    return ceil;
}
```
## Complexity
- Time complexity : O(log n) ~ O(N)

- Space complexity : O(1)
