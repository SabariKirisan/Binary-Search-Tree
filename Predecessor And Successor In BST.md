## Predecessor And Successor In BST (c++)

You have been given a binary search tree of integers with ‘N’ nodes. You are also given 'KEY' which represents data of a node of this tree.

Your task is to return the predecessor and successor of the given node in the BST.

## Example
![image](https://github.com/user-attachments/assets/991b4af5-19db-4ebf-8a7f-233378d5ce4f)

Input: 15 10 20 8 12 16 25 , key=10

Output: 8 12
## PROGRAM:(Main.cpp)
```
#include<bits/stdc++.h>
using namespace std;
pair<int, int> predecessorSuccessor(TreeNode *root, int key)
{
    int predecessor=-1;
    int successor=-1;
    TreeNode* temp=root;

    while(temp)
    {
        if(key>temp->data)
        {
            predecessor=temp->data;
            temp=temp->right;
        }
        else
        {
            temp=temp->left;
        }
    }
    temp=root;
    while(temp)
    {
        if(key<temp->data)
        {
            successor=temp->data;
            temp=temp->left;
        }
        else
        {
            temp=temp->right;
        }
    }
    return {predecessor,successor};
}
```
## Complexity
- Time complexity : O(H)

- Space complexity : O(1)
