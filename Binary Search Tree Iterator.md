## Binary Search Tree Iterator (c++)

Implement the BSTIterator class that represents an iterator over the in-order traversal of a binary search tree (BST):

BSTIterator(TreeNode root) Initializes an object of the BSTIterator class. The root of the BST is given as part of the constructor. The pointer should be initialized to a non-existent number smaller than any element in the BST.

boolean hasNext() Returns true if there exists a number in the traversal to the right of the pointer, otherwise returns false.

int next() Moves the pointer to the right, then returns the number at the pointer.

Notice that by initializing the pointer to a non-existent smallest number, the first call to next() will return the smallest element in the BST.

You may assume that next() calls will always be valid. That is, there will be at least a next number in the in-order traversal when next() is called.
## Example
![image](https://github.com/user-attachments/assets/e53c8c2a-92d2-499e-8139-0c5622cd9b49)

Input:["BSTIterator", "next", "next", "hasNext", "next", "hasNext", "next", "hasNext", "next", "hasNext"]

[[[7, 3, 15, null, null, 9, 20]], [], [], [], [], [], [], [], [], []]

Output:[null, 3, 7, true, 9, true, 15, true, 20, false]
## PROGRAM:(Main.cpp)
```
class BSTIterator 
{
private: stack<TreeNode*> st;
private: 
void pushall(TreeNode* root)
{
    while(root!=NULL)
    {
        st.push(root);
        root=root->left;
    }
}
public:
    BSTIterator(TreeNode* root) 
    {
        pushall(root);
    }
    
    int next() 
    {
        TreeNode* temp=st.top();
        st.pop();
        pushall(temp->right);
        return temp->val;
    }
    
    bool hasNext() 
    {
        return !st.empty();    
    }
};
```
## Complexity
- Time complexity : O(1)

- Space complexity : O(H)
