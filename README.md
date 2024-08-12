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


