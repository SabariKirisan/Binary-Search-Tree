## Construct Binary Search Tree from Preorder Traversal (c++)

Given an array of integers preorder, which represents the preorder traversal of a BST (i.e., binary search tree), construct the tree and return its root.

It is guaranteed that there is always possible to find a binary search tree with the given requirements for the given test cases.

A binary search tree is a binary tree where for every node, any descendant of Node.left has a value strictly less than Node.val, and any descendant of Node.right has a value strictly greater than Node.val.

A preorder traversal of a binary tree displays the value of the node first, then traverses Node.left, then traverses Node.right.

## Example
![image](https://github.com/user-attachments/assets/4b9c65a5-24f2-4fce-85ab-536eeb6ba894)

Input: preorder = [8,5,1,7,10,12]

Output: [8,5,10,1,7,null,12]
## PROGRAM:(Main.cpp)
```
class Solution {
public:
    TreeNode* bstFromPreorder(vector<int>& preorder) 
    {
        int i=0;
        return build(preorder,i,INT_MAX);   
    }
    TreeNode* build(vector<int>& preorder,int &i,int bound)
    {
        if(i==preorder.size() || preorder[i]>bound) return NULL;

        TreeNode* root=new TreeNode(preorder[i++]);

        root->left=build(preorder,i,root->val);
        root->right=build(preorder,i,bound);
        return root;
    }
};
```
## Complexity
- Time complexity : O(3N) ~ O(N)

- Space complexity : O(1)
