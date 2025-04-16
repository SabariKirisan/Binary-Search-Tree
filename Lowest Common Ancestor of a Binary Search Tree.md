## Lowest Common Ancestor of a Binary Search Tree (c++)

Given a binary search tree (BST), find the lowest common ancestor (LCA) node of two given nodes in the BST.

According to the definition of LCA on Wikipedia: “The lowest common ancestor is defined between two nodes p and q as the lowest node in T that has both p and q as descendants (where we allow a node to be a descendant of itself).”

## Example
![image](https://github.com/user-attachments/assets/aa77ca12-cb0d-48d0-966f-9c1bdaacd4aa)

Input: root = [6,2,8,0,4,7,9,null,null,3,5], p = 2, q = 8

Output: 6

Explanation: The LCA of nodes 2 and 8 is 6.
## PROGRAM:(Main.cpp)
```
class Solution {
public:
    TreeNode* lowestCommonAncestor(TreeNode* root, TreeNode* p, TreeNode* q)  {
        if(root==NULL) return NULL;
        int cur=root->val;
        if(cur<p->val && cur<q->val)
        {
            return lowestCommonAncestor(root->right,p,q);
        } 
        if(cur > p->val && cur > q->val)
        {
            return lowestCommonAncestor(root->left,p,q);
        }
        return root;
    }
};
```
## Complexity
- Time complexity : O(H)

- Space complexity : O(1)
