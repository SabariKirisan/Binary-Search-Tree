## Kth Largest Element in a BST (c++)

Given the root of a binary search tree, and an integer k, return the kth Largest value (1-indexed) of all the values of the nodes in the tree.

## Example
![image](https://github.com/user-attachments/assets/914f1233-216f-4259-8df0-32a0c6d4e5a0)

Input: root = [5,3,6,2,4,null,null,1], k = 3

Output: 4

## PROGRAM:(Main.cpp)
```
#include <bits/stdc++.h> 
using namespace std;
int KthLargestNumber(TreeNode<int>* root, int k) 
{
        TreeNode<int>* node = root;
        int count = 0;
        int result = -1;

        while (node != nullptr) 
        {
            if (node->right == nullptr) 
             {
                count++;
                if (count == k) result = node->data;
                node = node->left;
            } 
            else 
            {
                TreeNode<int>* pred = node->right;
                while (pred->left != nullptr && pred->left != node) 
                {
                    pred = pred->left;
                }

                if (pred->left == nullptr) 
                {
                    pred->left = node;
                    node = node->right;
                } 
                else 
                {
                    pred->left = nullptr;
                    count++;
                    if (count == k) result = node->data;
                    node = node->left;
                }
            }
        }
        return result;
}
```
## Complexity
- Time complexity :  O(N)

- Space complexity : O(1)
