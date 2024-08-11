# TREES-striver-
<h2> striver trees playlist </h2>

 REPRESENTATION OF TREE IN CPP

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
THERE ARE 3 TYPES OF DFS IN,PRE,POST

PREORDER

void preorder(root)
{
  if(root==null)return ;
  print(root->data);
  preorder(root->left);
  preorder(root->right);
}

INORDER

void inorder(node)

{
  if(node==NULL)return ;
  inorder(node->left)'
  print(node->data);
  inorder(node->right);
}

POSTORDER

void postorder
{
  if(root==NULL)return ;
  postorder(root->left);
  postorder(root->right);
  print(root->data);
}
take a vector and instead of printing put it in vector and then return the vector

LEVEL ORDER TRAVERSAL ONE OF THE IMP
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



