## Recover Binary Search Tree (c++)

You are given the root of a binary search tree (BST), where the values of exactly two nodes of the tree were swapped by mistake. Recover the tree without changing its structure.

## Example
![image](https://github.com/user-attachments/assets/d9b8d8a9-9b54-4714-b962-f4d4e587bd28)

Input: root = [3,1,4,null,null,2]

Output: [2,1,4,null,null,3]

Explanation: 2 cannot be in the right subtree of 3 because 2 < 3. Swapping 2 and 3 makes the BST valid.
## PROGRAM:(Main.cpp)
```
class Solution {
private:
    TreeNode* first;
    TreeNode* last;
    TreeNode* middle;
    TreeNode* prev;
private:
    void inorder(TreeNode* root)
    {
        if(root==NULL) return;
        inorder(root->left);

        if(prev!=NULL && (root->val < prev->val))
        {
            if(first==NULL)
            {
                first=prev;
                middle=root;
            }
            else
            {
                last=root;
            }
        }
        prev=root;
        inorder(root->right);
    }
public:
    void recoverTree(TreeNode* root) 
    {
        first=middle=last= NULL;
        prev=new TreeNode(INT_MIN);
        inorder(root);
        if(first && last) swap(first->val,last->val);
        else if(first && middle) swap(first->val,middle->val);
    }
};
```
## Complexity
- Time complexity : O(N)

- Space complexity : O(1)
