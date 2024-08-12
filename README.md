# TREES-striver-
<h2> striver trees playlist </h2>

 
 <h3>REPRESENTATION OF TREE IN CPP </h3>

struct node
{
int data;
struct node* right;
struct node* left;
node(int val)
{
data=val;
left=right=NULL;
}
};

DEPT FIRST SEARCH 
THERE ARE 3 TYPES OF DFS INORDER,PREORDER,POSTORDER

 <h3> PREORDER </h3>

void preorder(root)
{
  if(root==null)return ;
  print(root->data);
  preorder(root->left);
  preorder(root->right);
}

<h3>INORDER</h3>

void inorder(node)

{
  if(node==NULL)return ;
  inorder(node->left)'
  print(node->data);
  inorder(node->right);
}

<h3>POSTORDER</h3>

void postorder
{
  if(root==NULL)return ;
  postorder(root->left);
  postorder(root->right);
  print(root->data);
}
take a vector and instead of printing put it in vector and then return the vector
vectr<int>ans;
ans.push_back(root->val);


<h3>LEVEL ORDER TRAVERSAL ONE OF THE IMP</h3>
(BFS)

class Solution {
public:
    vector<vector<int>> levelOrder(TreeNode* root) {
        vector<vector<int>>ans;
        if(root==NULL)return ans;
        queue<TreeNode*>q;
        q.push(root);
        while(!q.empty())
        {
            int size=q.size();
            vector<int>level;
            for(int i=0 ; i<size ;i++)
            {
                TreeNode*node=q.front();
                q.pop();
                if(node->left!=NULL)q.push(node->left);
                if(node->right!=NULL)q.push(node->right);
                level.push_back(node->val);
            }
            ans.push_back(level);
        }
        return ans;
    }
};

<h3>PREORDER TRAVERSAL USING ITERATION</h3>

if(root==nullptr)return;
       stack<TreeNode*>st;
       st.push(root);
       while(!st.empty())
       {
        root=st.top();
        st.pop();
        ans.push_back(root->val);
        if(root->right) st.push(root->right);
        if(root->left) st.push(root->left);


 <h3>HEIGHT OF TREE</h3> 

   int maxDepth(TreeNode* root) {
        if(root==NULL) return 0;
        int leftdepth = maxDepth(root->left);
        int rightdepth = maxDepth(root->right);
        return 1+max(leftdepth,rightdepth);


<h3>BALANCED BINARY TREE </h3>
// BALANCED BINARY TREE IS A TREE WHOSE LEFTMAX-RIGHMAX>1

int findheight(TreeNode * root)
    {
        if(root==NULL)return 0;
        int left= findheight(root->left);
        int right =findheight(root->right);
        if(left==-1 || right==-1) return -1;
        if(abs(left-right)>1) return -1;
        return max(left,right)+1;
    }
    bool isBalanced(TreeNode* root) {
        if(findheight(root)==-1)return 0;
        else return 1;
    }

<h3>DIAMETER OF TREE</h3>
int findheight(TreeNode* root ,int &maxi)
{
 if(root==NULL)return 0;
 int left=findheight(root->left,maxi);
 int right=findheight(root->right,maxi);
 maxi=max(maxi,left+right);
 return 1+max(left,right);
 }
 
 int diameterOfBinaryTree(TreeNode* root) {
        int diameter = 0;
        findheight(root,diameter);
        return diameter;       
    }
<h3>ZIG ZAG LEVEL ORDER TRAVERSAL</h3>
vector<vector<int>> zigzagLevelOrder(TreeNode* root) {
        vector<vector<int>>ans;
        bool flag =true;
        queue<TreeNode*>q;
        if(root==NULL)return ans;
        q.push(root);
        while(!q.empty())
        {
            int n=q.size();
            vector<int>each(n);
            for(int i=0 ;i<n ; i++)
            {
                TreeNode *node=q.front();
                q.pop();
                int index= flag?i:(n-i-1);
                each[index]=node->val;
                if(node->left) q.push(node->left);
                if(node->right)q.push(node->right);
            }
            flag=!flag;
            ans.push_back(each);
        }
        return ans; }          
    <h3>SAME TREE </h3>
    bool isSameTree(TreeNode* p, TreeNode* q) {
        if(p== NULL && q==NULL) return true;
        if((p!= NULL && q==NULL) || (p==NULL && q!=NULL)) return false;
        bool left = isSameTree(p->left, q->left);
        bool right= isSameTree(p->right, q->right);
        bool value = (p->val == q->val);     
        if(left && right && value) return true;
        else return false;
    }
    <h3>MAXIMUM PATH SUM </h3>
     int findsum(TreeNode*root ,int &maxi)
     {
        if(root==NULL) return  0;
        int left= max(0,findsum(root->left));
        int right =max(0,findsum(root->right));
        maxi=max(maxi,left+right+root->val);
        return max(left+right)+root->val;
     }
     int maxPathSum(TreeNode* root) {
        int sum=INT_MIN;
        findsum(root,sum);
        return sum;
    }
<h3>BOUNDARY TRAVERSAL </h3>
 bool isLeaf(TreeNode root) {
    return !root->left && !root->right;
    }
    void addLeftBoundary(TreeNode root, vector<int>& res) {
        TreeNode curr = root->left;
        while (curr) {
            // If the current node is not a leaf,
            // add its value to the result
            if (!isLeaf(curr)) {
                res.push_back(curr->data);
            }
            // Move to the left child if it exists,
            // otherwise move to the right child
            if (curr->left) {
                curr = curr->left;
            } else {
                curr = curr->right;
            }
        }
    }
    // Function to add the
    // right boundary of the tree
    void addRightBoundary(TreeNode root, vector<int>& res) {
        TreeNode curr = root->right;
        vector<int> temp;
        while (curr) {
            // If the current node is not a leaf,
            // add its value to a temporary vector
            if (!isLeaf(curr)) {
                temp.push_back(curr->data);
            }
            // Move to the right child if it exists,
            // otherwise move to the left child
            if (curr->right) {
                curr = curr->right;
            } else {
                curr = curr->left;
            }
        }
        // Reverse and add the values from
        // the temporary vector to the result
        for (int i = temp.size() - 1; i >= 0; --i) {
            res.push_back(temp[i]);
        }
    }
    // Function to add the
    // leaves of the tree
    void addLeaves(TreeNode root, vector<int>& res) {
        // If the current node is a
        // leaf, add its value to the result
        if (isLeaf(root)) {
            res.push_back(root->data);
            return;
        }
        // Recursively add leaves of
        // the left and right subtrees
        if (root->left) {
            addLeaves(root->left, res);
        }
        if (root->right) {
            addLeaves(root->right, res);
        }
    }
vector<int> traverseBoundary(TreeNode root)
{
        vector<int> res;
        if (!root) {
            return res;
        }
        // If the root is not a leaf,
        // add its value to the result
        if (!isLeaf(root)) {
            res.push_back(root->data);
        }
        // Add the left boundary, leaves,
        // and right boundary in order
        addLeftBoundary(root, res);
        addLeaves(root, res);
        addRightBoundary(root, res);
        return res;
    }



