## Insert into a Binary Search Tree (c++)

You are given the root node of a binary search tree (BST) and a value to insert into the tree. Return the root node of the BST after the insertion. It is guaranteed that the new value does not exist in the original BST.

Notice that there may exist multiple valid ways for the insertion, as long as the tree remains a BST after insertion. You can return any of them.

## Example
![image](https://github.com/user-attachments/assets/19001280-2bbc-4625-b2ae-b09290cdbfe7)

Input: root = [4,2,7,1,3], val = 5

Output: [4,2,7,1,3,5]
## PROGRAM:(Main.cpp)
```
class Solution {
public:
    TreeNode* insertIntoBST(TreeNode* root, int val) 
    {
        if(root==NULL) return new TreeNode(val);

        TreeNode* cur=root;

        while(true)
        {
            if(cur->val<=val)
            {
                if(cur->right!=NULL) cur=cur->right;
                else
                {
                    cur->right=new TreeNode(val);
                    break;
                }
            }
            else
            {
                if(cur->left!=NULL) cur=cur->left;
                else
                {
                    cur->left=new TreeNode(val);
                    break;
                }
            }
        }
        return root;
    }
};
```
## Complexity
- Time complexity : O(log n) ~ O(N)

- Space complexity : O(1)
