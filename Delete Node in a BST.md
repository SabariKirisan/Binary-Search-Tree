## Delete Node in a BST (c++)

Given a root node reference of a BST and a key, delete the node with the given key in the BST. Return the root node reference (possibly updated) of the BST.

Basically, the deletion can be divided into two stages:

Search for a node to remove.

If the node is found, delete the node.

## Example
![image](https://github.com/user-attachments/assets/f25f7781-c805-4561-a106-4aac62e2bf2a)

Input: root = [5,3,6,2,4,null,7], key = 3

Output: [5,4,6,2,null,null,7]

Explanation: Given key to delete is 3. So we find the node with value 3 and delete it.
One valid answer is [5,4,6,2,null,null,7], shown in the above BST.
Please notice that another valid answer is [5,2,6,null,4,null,7] and it's also accepted.
## PROGRAM:(Main.cpp)
```
class Solution {
public:
    TreeNode* helper(TreeNode* root)
    {
        if(root->left==NULL) return root->right;
        else if (root->right==NULL) return root->left;

        TreeNode* rightnode=root->right;
        TreeNode* left_lastright=find(root->left);
        left_lastright->right=rightnode;

        return root->left;
    }
    TreeNode* find(TreeNode* root)
    {
        if(root->right==NULL)
        {
            return root;
        } 
        return find(root->right);
    }
    TreeNode* deleteNode(TreeNode* root, int key) 
    {
        if(root==NULL) return NULL;
        if(root->val==key) return helper(root); 
        TreeNode* dummy=root;

        while(root!=NULL)
        {
            if(root->val>key)
            {
                if(root->left && root->left->val==key)
                {
                    root->left=helper(root->left);
                    break;
                }
                else
                {
                    root=root->left;
                }
            }
            else
            {
                if(root->right && root->right->val==key)
                {
                    root->right=helper(root->right);
                    break;
                }
                else
                {
                    root=root->right;
                }
            }
        } 
        return dummy; 
    }
};
```
## Complexity
- Time complexity : O(log n) ~ O(N)

- Space complexity : O(1)
