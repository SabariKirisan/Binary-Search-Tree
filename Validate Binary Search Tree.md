## Validate Binary Search Tree (c++)

Given the root of a binary tree, determine if it is a valid binary search tree (BST).

A valid BST is defined as follows:

The left subtree of a node contains only nodes with keys less than the node's key.

The right subtree of a node contains only nodes with keys greater than the node's key.

Both the left and right subtrees must also be binary search trees.

## Example
![image](https://github.com/user-attachments/assets/b34e7b09-2573-442d-9438-23fcfc38a21c)

Input: root = [5,1,4,null,null,3,6]

Output: false

Explanation: The root node's value is 5 but its right child's value is 4.
## PROGRAM:(Main.cpp)
```
class Solution {
public:
    bool isValidBST(TreeNode* root) 
    {
        return isvalidBST(root, LLONG_MIN, LLONG_MAX);   
    }
    bool isvalidBST(TreeNode* root, long minn,long maxx)
    {
        if(root==NULL) return true;
        if(root->val>=maxx || root->val<=minn) return false;
        return isvalidBST(root->left,minn,root->val) && isvalidBST(root->right,root->val,maxx);
    }
};
```
## Complexity
- Time complexity : O(N)

- Space complexity : O(1)
