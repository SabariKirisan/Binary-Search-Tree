## Floor from BST (c++)

Floor of an integer is the closest integer smaller than or equal to a given number.

## Example
![image](https://github.com/user-attachments/assets/ae8bfb82-9d84-4636-a2da-d463772fd242)

Input: x=9

Output: 8
## PROGRAM:(Main.cpp)
```
using namespace std;
int floorInBST(TreeNode<int> * root, int X)
{
    int floor=-1;
    while(root)
    {
        if(root->val==X)
        {
            floor=root->val;
            return floor;
        }
    
        if(X > root->val)
        {
            floor=root->val;
            root=root->right;
        }
        else
        {
            root=root->left;
        }
    }
    return floor;
}
```
## Complexity
- Time complexity : O(log n) ~ O(N)

- Space complexity : O(1)
