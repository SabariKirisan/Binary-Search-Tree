## Search in a Binary Search Tree (c++)

You are given the root of a binary search tree (BST) and an integer val.

Find the node in the BST that the node's value equals val and return the subtree rooted with that node. If such a node does not exist, return null.

## Example
![image](https://github.com/user-attachments/assets/d3dc25b9-c2c0-44d9-ac75-a058b9fd09af)

Input: root = [4,2,7,1,3], val = 2

Output: [2,1,3]
## PROGRAM:(Main.cpp)
```
class Solution {
public:
    TreeNode* searchBST(TreeNode* root, int val) 
    {
        while(root != NULL && root->val!=val)
        {
            root=val>root->val?root->right:root->left;
        }   
        return root;
    }
};
```
## Complexity
- Time complexity : O(log n) ~ O(N)(skew tree)

- Space complexity : O(1)
