## Kth Smallest Element in a BST (c++)

Given the root of a binary search tree, and an integer k, return the kth smallest value (1-indexed) of all the values of the nodes in the tree.

## Example
![image](https://github.com/user-attachments/assets/914f1233-216f-4259-8df0-32a0c6d4e5a0)

Input: root = [5,3,6,2,4,null,null,1], k = 3

Output: 3

## PROGRAM:(Main.cpp)
```
class Solution {
public:
    int kthSmallest(TreeNode* root, int k) 
    {
        int cnt=0;
        int result =-1;
        TreeNode* node=root;
        while(node!=NULL)
        {
            if(node->left == NULL)
            {
                cnt++;
                if(cnt==k) result=node->val;
                node=node->right;
            }
            else
            {
                TreeNode* cur=node->left;
                while(cur->right!=NULL && cur->right !=node)
                {
                    cur=cur->right;
                }
                if(cur->right==NULL)
                {
                    cur->right=node;
                    node=node->left;
                }
                else
                {
                    cur->right=NULL;
                    cnt++;
                    if(cnt==k) result=node->val;
                    node=node->right;
                }
            }
        }   
        return result;
    }
};
```
## Complexity
- Time complexity :  O(N)

- Space complexity : O(1)
