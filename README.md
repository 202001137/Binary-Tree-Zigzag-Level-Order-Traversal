# Binary-Tree-Zigzag-Level-Order-Traversal

vector<vector<int>> ans;
        queue<TreeNode*> q;
        q.push(root);
        int level=0;

        if(root==0)
            return ans;

        while(!q.empty()){
            vector<int> subans;
            int size=q.size();
            stack<int> s;

            if(level%2==0){
                for(int i=0; i<size; i++){
                    TreeNode* top = q.front();
                    q.pop();

                    subans.push_back(top->val);

                    if(top->left)
                        q.push(top->left);
                    if(top->right){
                        q.push(top->right);
                    }
                }
            }
            else{
                for(int i=0; i<size; i++){
                    //stack<int> s;

                    TreeNode* top = q.front();
                    q.pop();

                    s.push(top->val);

                    if(top->left)
                        q.push(top->left);
                    if(top->right){
                        q.push(top->right);
                    }
                }
                while(!s.empty()){
                    int top=s.top();
                    s.pop();

                    subans.push_back(top);
                }
            }
            
            ans.push_back(subans);
            level++;
        }
        return ans;
